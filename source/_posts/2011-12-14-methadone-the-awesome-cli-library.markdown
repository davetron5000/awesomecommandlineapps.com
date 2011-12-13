--- 
title: Introducing Methadone, the Awesome Command-Line Library
layout: post
---

I've spent the last year [writing a book][book] on building awesome command-line applications in Ruby.  Over the course of
writing it, I"ve used a lot of Ruby libraries for building command-line apps, and none of them work quite right.  In my book, I
spent significant time on [OptionParser][optparse], since it's builtin, and [GLI][gli], since I wrote it.

I just finished up an appendix where I used [main][main], [thor][thor], and [trollop][trollop] to build my running examples in
the book.  I did this for a few reasons:

* These tools are popular, and people have asked if they'd be included
* They are, by and large, very different from how `OptionParser` and GLI work
* I wanted to give them a real shakedown

I also surveyed many other tools, but, alas, I can't include everything.  Each of these tools had common theme, which was to
avoid the boilerplate of `OptionParser`, and make it really easy to parse command-line arguments.  They all have done this at quite
a large cost.  All of them are less powerful and extensible than `OptionParser`, and only slightly more compact (or, in the case of
main, way less compact).

Enter [methadone][methadone], which I developed while working on the book and developing my [talk][gogaruco-talk] for Golden Gate
Ruby Conf 2011.

<!-- more -->

## Another command-line option parser?

Yes and no.  Methadone isn't a re-implementation of command-line option parsing.  It's barely a DSL, making use of almost no
meta-programming,, `class_eval`, or other craziness.  It's a pure Ruby proxy to `OptionParser`, with some helper methods.  It makes
idiomatic and canonical option parsing and command-line app design as seemless as possible, but doesn't force *any* of itself one
you.  In this post, I'll derive its syntax while showing you the basics of how to structure a simple command-line app.  To dig
deeper, you'll have to [buy the book][book] (but never fear, if you don't like Methadone, it only takes up a few scant pages at
the end).

## Basic Command-line App Structure

Most command-line apps start off with parsing the command-line with `OptionParser` (which typically consists of setting values into
some `Hash`), defining a few helper methods, and then, at the end, implementing the main logic of the program:

```ruby
#!/usr/bin/env ruby

require 'optparse'

options = {}

parser = OptionParser.new do |opts|
  opts.banner 'My awesome app'
  
  opts.on("-u USERNAME","--username","The username") do |user|
    options[:username] = user
  end

  opts.on("-v","--verbose","Be verbose") do 
    options[:verbose] = true
  end

  # etc.

end

parser.parse!

def some_helper_method
end

def some_other_helper_method

puts "Starting program" if options[:verbose]

# etc, the main logic of your program
```

Yuck.  The boilerplate option parsing is bad enough, but the structure is all wrong.  The interesting stuff is all the way at the bottom; you have to read the thing in the wrong order.  At the very least, you should use a main method:

```ruby
#!/usr/bin/env ruby

require 'optparse'

def main(args)
  # main logic of your app
  0 # or return nonzero if something went wrong
end

def some_helper_method
end

def some_other_helper_method

puts "Starting program" if options[:verbose]

options = {}

parser = OptionParser.new do |opts|
  opts.banner 'My awesome app'
  
  opts.on("-u USERNAME","--username","The username") do |user|
    options[:username] = user
  end

  opts.on("-v","--verbose","Be verbose") do 
    options[:verbose] = true
  end

  # etc.

end

parser.parse!

exit main(ARGV)
```

Of course, we might raise an exception.  We might *want* to, but this isn't amateur hour and we can't have our app vomiting out a backtrace.  So, we wrap our call to `main`:

```ruby
begin
  exit main(ARGV)
rescue => ex
  STDERR.puts ex.message
  exit 1
end
```

## Methadone's Main Method

We now have a pretty canonical structure for any simple command-line app.  We don't want to include this every time, so we'll use
the first feature of Methadone, which is the `main` method:


```ruby
#!/usr/bin/env ruby

require 'methadone'

include Methadone::Main

main do |args,go,here|
  # main logic
  # raise exceptions at will
end

# declare options and helper methods as before

go!
```

This does a few things for us.  `go!` will execute the contents of the block given to `main`.  It will extract the contents of
`ARGV` leftover after parsing and pass them to the block.  Since they're passed as individual arguments, you don't have to call `shift` a bunch of times.  Just name your parameters whatever, and
Metahdone takes care of it.   If your main block raises an exception, `go!` will handle catching it, messaging the user without a backtrace, and exiting nonzero.

## Parse Options with no Loss of Power

Of course, that option parsing code is still annoying, especially since we're just setting it into an options hash.

Methadone's `Main` module exposes some helper methods.  One of them is called `on`, and it works exactly like `OptionParser`'s
`on` method:

```ruby
main do
  # logic
end

options = {}

on("-u USER","--username","The username") do |user|
  options[:username] = user
end
```

Methadone maintains an instance of `OptionParser`, and this will pass through to it.  That means that validations via list or
regex will work just fine.  Type conversions pass right on through; you can even add your own via `opts.accept`.

Of course, since we are almost always just taking
the flag argument and putting it into a `Hash`, Methadone takes care of that for us.  The following code is identical to the code
above:

```ruby
on("-u USER","--username","The user name")
```

This works because Methadone exposes a method `options`, which returns the `Hash` of the current options.  It's available inside
our `main` block, so we can access the values the user used on the command-line.  Of course, if we need to do something fancy, we can do anything that `OptionParser` can do, and if we set values in `options`, they'll stick.

## Do the Right Thing

Because we're using `OptionParser`, we get all the benefits of the great help system that `OptionParser` provides.  A key part of
that system is the _banner_.  The banner tells the user what the program is for and how to invoke it.  `OptionParser` provides a
reasonable default, but it's not good enough.   We want:

    $ awesome_app.rb --help
    Does so many awesome things, you won't believe it.

    Usage:  awesome_app.rb [options] thing other_thing [optional_thing]

We can make this with a big, fat string, but why should we?  Methadone knows that our app takes options, and it knows the name of
our app, so let's just tell it the missing information:

```ruby
main do |thing,other_thing,optional_thing|
  # logic
end

opts.on("-u USER","--username","The user name")

description "Does so many awesome things, you won't believe it."

arg :thing
arg :other_thing
arg :optional_thing, :optional

go!
```


Not only will Methadone automatically create your banner, but it will complain if the first two, required, arguments are missing.
Don't like that?  Just call `banner=` and set the banner to whatever you want.  Methadone doesn't care.  It's just there to help.

Methadone makes it dead simple to write only what you need to, but doesn't stop you from unleashing the full power of
`OptionParser`, or doing things a different way, if you like.

## Sweet, Sweet Sugar

But wait!  There's more!  Complex programs start to look like this:

```ruby
if have_connection
  # puts "got a connection"
  file = request_data
  puts "Got data"
  if file.nil?
    STDERR.puts "Data was nil!?!?"
  end
end
# puts "Moving on"
```

You've got a mix of commented-out debug statements, informational messages and teadiously long error messages going to the
standard error.  Methadone includes a special `Logger` instance that does away with all this:

```ruby
if have_connection
  debug "got a connection"
  file = request_data
  info "Got data"
  if file.nil?
    error "Data was nil!?!?"
  end
end
debug "Moving on"
```

By default, `debug` messages don't go anywhere.  `info` goes to the standard output and
`warn`, `error`, and `fatal` go to the standard error.  Theses messages are _unformatted_ and ready for consumption by the 
user (i.e. they are not maven-style enterprise logging with timestamps; they go to the console formatted for a human).
Messages automatically go to the right stream.  Of course, if you redirect either of these to a file, you get full, complete
timestamped log messages.  Perfect for use in cron.

## Even this is too much to type

    $ methadone my_app

This generates a gemified project, complete with a README, Rakefile, unit tests and an [aruba][aruba]-powered cucumber test, so
you can TDD your app instantly.  Your `bin` file will be setup with Methadone's structure and you're off to the races.  It even
comes with some add-ons to Aruba to let you test-drive your user interface.

## Will there be more?

Of course!  Methadone's still in a pre-release state right now, although it's being used in production.  The parts that are there
are solid, completely tested and good to go.  I just want to add some more sugar before calling it V1.  Namely, I want to make it
easy to write shell scripts in Ruby.  Something like `FileUtils` but better.

[book]: http://www.awesomecommandlineapps.com
[optparse]: http://www.ruby-doc.org/stdlib-1.9.3/libdoc/optparse/rdoc/OptionParser.html
[gli]: https://github.com/davetron5000/gli
[main]: https://github.com/ahoward/main
[thor]: https://github.com/wycats/thor
[trollop]: http://trollop.rubyforge.org/
[methadone]: https://github.com/davetron5000/methadone
[gogaruco-talk]: http://confreaks.net/videos/638-gogaruco2011-test-drive-the-development-of-your-command-line-applications
[aruba]: https://github.com/cucumber/aruba
