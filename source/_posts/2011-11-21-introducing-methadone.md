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
* They are, by and large, very different from how OptionParser and GLI work
* I wanted to give them a real shakedown

I also surveyed many other tools, but, alas, I can't include everything.  Each of these tools had common theme, which was to
avoid the boilerplate of OptionParser, and make it really easy to parse command-line arguments.  They all have done this at quite
a large cost.  All of them are less powerful and extensible than OptionParser, and only slightly more compact (or, in the case of
main, way less compact).

Enter [methadone][methadone], which I developed while working on the book and developing my [talk][gogaruco-talk] for Golden Gate
Ruby Conf 2011.

## Another command-line option parser?

Yes and no.  Methadone isn't a re-implementation of command-line option parsing.  It's barely a DSL, making use of almost no
meta-programming. `class_eval`, or other craziness.  It's a pure Ruby proxy to OptionParser, with some helper methods.  It makes
idiomatic and canonical option parsing and command-line app design as seemless as possible, but doesn't force *any* of itself one
you.  In this post, I'll derive its syntax while showing you the basics of how to structure a simple command-line app.  To dig
deeper, you'll have to [buy the book][book] (but never fear, if you don't like Methadone, it only takes up a few scant pages at
the end).

## Basic Command-line App Structure

Most command-line apps start off with parsing the command-line with OptionParser (which typically consists of setting values into
some `Hash`), defining a few helper methods, and then, at the end, implementing the main logic of the program:

<script src="https://gist.github.com/1384855.js?file=naive_cli.rb" />

Yuck.  The boilerplate optino parsing is bad enough, but the structure is all wrong.  The interesting stuff is all the way at the bottom; you have to read the thing in the wrong order.  At the very least, you should use a main method:

<script src="https://gist.github.com/1384855.js?file=main_method.rb"></script>

Of course, we might raise an exception.  We might *want* to, but we certainly don't want our app vomitinbg out a backtrace.
That's amateur hour.  So, we wrap our call to `main`:

<script src="https://gist.github.com/1384855.js?file=wrapped_main.rb"></script>

## Methadone's Main Method

We now have a pretty canonical structure for any simple command-line app.  We don't want to include this every time, so we'll use
the first feature of Methadone, which is the `main` method:

<script src="https://gist.github.com/1384855.js?file=main_methadone.rb"></script>

This does a few things for us.  `go!` will execute the contents of the block given to `main`.  It will extract the contents of
`ARGV` and pass them to the block, you don't have to call `shift` a bunch of times.  Just name your parameters whatever, and
Metahdone takes care of it.   If your main block raises an exception,
     `go!` will handle catching it, messaging the user without a backtrace, and exiting nonzer.

## Parse Options with no Loss of Power

Of course, that option parsing code is still annoying, especially since we're just setting it into an options hash.

Methadone's `Main` module exposes some helper methods.  One of them is called `on`, and it works exactly like `OptionParser`'s
`on` method:

<script src="https://gist.github.com/1384855.js?file=methadone_on.rb"></script>

Methadone maintains an instance of `OptionParser`, and this will pass through to it.  That means that validations via list or
regex will work just fine.  Type conversions pass right on through; you can even add your own via `opts.accept`.

Of course, since we are almost always just taking
the flag argument and putting it into a `Hash`, Methadone takes care of that for us.  The following code is identical to the code
above:

<script src="https://gist.github.com/1384855.js?file=methadone_on_better.rb"></script>

This works because Methadone exposes a method `options`, which returns the `Hash` of the current options.  It's available inside
our `main` block.  Of course, if we need to do something fancy, we can do anything that OptionParser can do, and if we set values
in `options`, they'll stick.

## Do the Right Thing

Because we're using OptionParser, we get all the benefits of the great help system that OptionParser provides.  A key part of
that system is the _banner_.  The banner tells the user what the program is for and how to invoke it.  OptionParser provides a
reasonable default, but it's not good enough.   We want:

    $ awesome_app.rb --help
    Does so many awesome things, you won't believe it.

    Usage:  awesome_app.rb [options] thing other_thing [optional_thing]

We can make this with a big, fat string, but why should we?  Methadone knows that our app takes options, and it knows the name of
our app, so let's just tell it the missing information:

<script src="https://gist.github.com/1384855.js?file=banner.rb"></script>

Not only will Methadone automatically create your banner, but it will complain if the first two, required, arguments are missing.
Don't like that?  Just call `banner=` and set the banner to whatever you want.  Methadone doesn't care.  It's just there to help.

Methadone makes it dead simple to write only what you need to, but doesn't stop you from unleashing the full power of
OptionParser, or doing things a different way, if you like.

## Sweet, Sweet Sugar

But wait!  There's more!  Complex programs start to look like this:

<script src="https://gist.github.com/1384855.js?file=cheesy.rb"></script>

You've got a mix of commented-out debug statements, informational messages and teadiously long error messages going to the
standard error.  Methadone includes a special `Logger` instance that does away with all this:

<script src="https://gist.github.com/1384855.js?file=logger.rb"></script>

By defuault, `debug` messages don't go anywhere.  `info` goes to the standard output and
`warn`, `error`, and `fatal` go to the standard error.  Theses messages are _unformatted_ and ready for consumption by the user.
Messags automatically go to the right stream.  Of course, if you redirect either of these to a file, you get full, complete
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


    $ gem install methadone

[book]: http://www.google.com
[optparse]: http://www.google.com
[gli]: http://www.google.com
[main]: http://www.google.com
[thor]: http://www.google.com
[trollop]: http://www.google.com
[methadone]: http://www.google.com
[gogaruco-talk]: http://www.google.com
[book]: http://www.google.com
[aruba]: http://www.google.com