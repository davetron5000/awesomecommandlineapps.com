---
layout: page
title: "Ruby Gems for Command-Line Apps"
date: 2012-03-26 21:15
comments: true
sharing: true
footer: true
---
One of the toughest things about writing command-line apps in Ruby is finding the right gems.  There's tons out there, but they
can be really hard to find, either due to names that are too generic (main) or too bizzare (trollop).  Searching on RubyGems and
Github is OK, but not great.  While speaking at conferences and writing the book, I came across a ton of wonderful
gems for writing command-line apps.  This page is an attempt to catalog them all.

----



<a href='#tag-colored_output'>Colored Output</a> | <a href='#tag-command_suite'>Command Suite</a> | <a href='#tag-documentation'>Documentation</a> | <a href='#tag-framework'>Framework</a> | <a href='#tag-inbook'>In Book</a> | <a href='#tag-parsing'>Parsing</a> | <a href='#tag-progressbar'>Progressbar</a> | <a href='#tag-recommended'>Recommended</a> | <a href='#tag-simple'>Simple</a> | <a href='#tag-subprocess'>Subprocess</a> | <a href='#tag-table'>Table</a> | <a href='#tag-testing'>Testing</a> | <a href='#tag-ui'>UI</a> | <a href='#tag-user_io'>User I/O</a> | <a href='#tag-validation'>Validation</a>


<a name='tag-colored_output'></a>
#### Colored Output
* <a href='https:/github.com/janlelis/paint'>Paint</a> - Color your output using RGB, with support for 256-color terminals
* <a href='https:/github.com/flori/term-ansicolor.git'>Term-ansicolor</a> - Create colored output
* <a href='https://github.com/sickill/rainbow'>Rainbow</a> - Create colored output

<a name='tag-command_suite'></a>
#### Command Suite
* <a href='http://www.github.com/wycats/thor'>Thor</a> - Create a command-suite app simply and easily, as well as Rails generators
* <a href='http://github.com/ahoward/main'>Main</a> - A class factory and DSL for generating command line programs real quick.
* <a href='http://github.com/davetron5000/gli'>GLI</a> - Create awesome, polished command suites without a lot of code
* <a href='https:/github.com/visionmedia/commander'>Commander</a> - Create command suites with a rake-like syntax
* <a href='https:/github.com/ddfreyne/cri'>CRI</a> - Create simple or command-suites with a syntax that is a mix of main and GLI.
* <a href='https:/github.com/joshbuddy/optitron'>Optitron</a> - Create command-suites based on classes and methods, similar to thor.

<a name='tag-documentation'></a>
#### Documentation
* <a href='https://github.com/defunkt/gem-man'>Gem-man</a> - Read man pages installed with gems a la `man`
* <a href='https://github.com/rtomayko/ronn'>Ronn</a> - Author man pages in Markdown

<a name='tag-framework'></a>
#### Framework
* <a href='http://www.github.com/davetron5000/methadone'>Methadone</a> - Bootstrap your command line app, get all the power of `OptionParser`, but none of the verbosity
* <a href='http://www.github.com/wycats/thor'>Thor</a> - Create a command-suite app simply and easily, as well as Rails generators
* <a href='http://github.com/davetron5000/gli'>GLI</a> - Create awesome, polished command suites without a lot of code
* <a href='http://rubyworks.github.com/executable/'>executable</a> - Executable is to commandline what ActiveRecord is to the database

<a name='tag-inbook'></a>
#### In Book
* <a href='http://www.github.com/davetron5000/methadone'>Methadone</a> - Bootstrap your command line app, get all the power of `OptionParser`, but none of the verbosity
* <a href='http://www.github.com/wycats/thor'>Thor</a> - Create a command-suite app simply and easily, as well as Rails generators
* <a href='http://trollop.rubyforge.org'>Trollop</a> - Parse the command-line idiomatically without a lot of code
* <a href='http://github.com/ahoward/main'>Main</a> - A class factory and DSL for generating command line programs real quick.
* <a href='http://github.com/davetron5000/gli'>GLI</a> - Create awesome, polished command suites without a lot of code
* <a href='https://github.com/sickill/rainbow'>Rainbow</a> - Create colored output
* <a href='https://github.com/visionmedia/terminal-table'>Terminal-Table</a> - Create ASCII tables in your output, similar to a SQL clienbt
* <a href='https://github.com/defunkt/gem-man'>Gem-man</a> - Read man pages installed with gems a la `man`
* <a href='https://github.com/rtomayko/ronn'>Ronn</a> - Author man pages in Markdown

<a name='tag-parsing'></a>
#### Parsing
* <a href='http://www.github.com/davetron5000/methadone'>Methadone</a> - Bootstrap your command line app, get all the power of `OptionParser`, but none of the verbosity
* <a href='http://www.github.com/wycats/thor'>Thor</a> - Create a command-suite app simply and easily, as well as Rails generators
* <a href='http://trollop.rubyforge.org'>Trollop</a> - Parse the command-line idiomatically without a lot of code
* <a href='http://github.com/ahoward/main'>Main</a> - A class factory and DSL for generating command line programs real quick.
* <a href='http://github.com/davetron5000/gli'>GLI</a> - Create awesome, polished command suites without a lot of code
* <a href='https:/github.com/defunkt/choice'>Choice</a> - Command-line parser for simple command-line apps
* <a href='https:/github.com/visionmedia/commander'>Commander</a> - Create command suites with a rake-like syntax
* <a href='https:/github.com/ddfreyne/cri'>CRI</a> - Create simple or command-suites with a syntax that is a mix of main and GLI.
* <a href='https:/github.com/opscode/mixlib-cli'>Mixlib-CLI</a> - Maintained by Opscode, the maintainers of chef, this can create simple command-line apps in a readable, if verbose, syntax
* <a href='https:/github.com/joshbuddy/optitron'>Optitron</a> - Create command-suites based on classes and methods, similar to thor.
* <a href='https:/github.com/injekt/slop'>Slop</a> - Create simple command-line apps with a syntax similar to trollop.
* <a href='http://rubyworks.github.com/executable/'>executable</a> - Executable is to commandline what ActiveRecord is to the database

<a name='tag-progressbar'></a>
#### Progressbar
* <a href='https:/github.com/geemus/formatador'>Formatador</a> - produce rich output with a tag-like string syntax, including tables and progressbars
* <a href='https:/github.com/paul/progress_bar'>ProgressBar</a> - create progress bars in terminal output

<a name='tag-recommended'></a>
#### Recommended
* <a href='http://www.github.com/davetron5000/methadone'>Methadone</a> - Bootstrap your command line app, get all the power of `OptionParser`, but none of the verbosity
* <a href='http://github.com/ahoward/main'>Main</a> - A class factory and DSL for generating command line programs real quick.
* <a href='http://github.com/davetron5000/gli'>GLI</a> - Create awesome, polished command suites without a lot of code
* <a href='https://github.com/sickill/rainbow'>Rainbow</a> - Create colored output
* <a href='https://github.com/wbailey/command_line_reporter'>Command_line_reporter</a> - Create a "report", using unicode characters in the output for tables
* <a href='https://github.com/defunkt/gem-man'>Gem-man</a> - Read man pages installed with gems a la `man`
* <a href='https://github.com/rtomayko/ronn'>Ronn</a> - Author man pages in Markdown

<a name='tag-simple'></a>
#### Simple
* <a href='http://www.github.com/davetron5000/methadone'>Methadone</a> - Bootstrap your command line app, get all the power of `OptionParser`, but none of the verbosity
* <a href='http://www.github.com/wycats/thor'>Thor</a> - Create a command-suite app simply and easily, as well as Rails generators
* <a href='http://trollop.rubyforge.org'>Trollop</a> - Parse the command-line idiomatically without a lot of code
* <a href='http://github.com/ahoward/main'>Main</a> - A class factory and DSL for generating command line programs real quick.
* <a href='https:/github.com/defunkt/choice'>Choice</a> - Command-line parser for simple command-line apps
* <a href='https:/github.com/ddfreyne/cri'>CRI</a> - Create simple or command-suites with a syntax that is a mix of main and GLI.
* <a href='https:/github.com/opscode/mixlib-cli'>Mixlib-CLI</a> - Maintained by Opscode, the maintainers of chef, this can create simple command-line apps in a readable, if verbose, syntax
* <a href='https:/github.com/injekt/slop'>Slop</a> - Create simple command-line apps with a syntax similar to trollop.

<a name='tag-subprocess'></a>
#### Subprocess
* <a href='http://www.github.com/davetron5000/methadone'>Methadone</a> - Bootstrap your command line app, get all the power of `OptionParser`, but none of the verbosity
* <a href='https://github.com/jarib/childprocess'>Childprocess</a> - Cross-platform ruby library for managing child processes
* <a href='https://github.com/ahoward/open4'>Open4</a> - Open3-like library for Ruby 1.8

<a name='tag-table'></a>
#### Table
* <a href='https:/github.com/geemus/formatador'>Formatador</a> - produce rich output with a tag-like string syntax, including tables and progressbars
* <a href='https://github.com/visionmedia/terminal-table'>Terminal-Table</a> - Create ASCII tables in your output, similar to a SQL clienbt
* <a href='https://github.com/wbailey/command_line_reporter'>Command_line_reporter</a> - Create a "report", using unicode characters in the output for tables
* <a href='https://github.com/arches/table_print'>table_print</a> - Turn objects into nicely formatted columns for easy reading - works great in Rails console with flexible formatting options

<a name='tag-testing'></a>
#### Testing
* <a href='https:/github.com/devver/construct'>Construct</a> - Create temporary directory structure for testing
* <a href='https:/github.com/defunkt/fakefs'>FakeFS</a> - Fakes out various `File` and related calls to simulate a filesystem without changing system files.
* <a href='https://github.com/cucumber/aruba'>Aruba</a> - Test your command-line app with Cucumber

<a name='tag-ui'></a>
#### UI
* <a href='https:/github.com/geemus/formatador'>Formatador</a> - produce rich output with a tag-like string syntax, including tables and progressbars
* <a href='https:/github.com/JEG2/highline'>Highline</a> - handle user input and output via a "Q&A" style API, including type conversions and validation
* <a href='https:/github.com/janlelis/paint'>Paint</a> - Color your output using RGB, with support for 256-color terminals
* <a href='https:/github.com/paul/progress_bar'>ProgressBar</a> - create progress bars in terminal output
* <a href='https:/github.com/flori/term-ansicolor.git'>Term-ansicolor</a> - Create colored output
* <a href='https://github.com/sickill/rainbow'>Rainbow</a> - Create colored output
* <a href='https://github.com/visionmedia/terminal-table'>Terminal-Table</a> - Create ASCII tables in your output, similar to a SQL clienbt
* <a href='https://github.com/wbailey/command_line_reporter'>Command_line_reporter</a> - Create a "report", using unicode characters in the output for tables
* <a href='https://github.com/arches/table_print'>table_print</a> - Turn objects into nicely formatted columns for easy reading - works great in Rails console with flexible formatting options

<a name='tag-user_io'></a>
#### User I/O
* <a href='https:/github.com/JEG2/highline'>Highline</a> - handle user input and output via a "Q&A" style API, including type conversions and validation

<a name='tag-validation'></a>
#### Validation
* <a href='https:/github.com/JEG2/highline'>Highline</a> - handle user input and output via a "Q&A" style API, including type conversions and validation
