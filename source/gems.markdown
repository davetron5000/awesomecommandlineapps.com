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



### By Category
<a href='#tag-colored_output'>Colored Output</a> | <a href='#tag-command_suite'>Command Suite</a> | <a href='#tag-documentation'>Documentation</a> | <a href='#tag-framework'>Framework</a> | <a href='#tag-inbook'>Inbook</a> | <a href='#tag-parsing'>Parsing</a> | <a href='#tag-progressbar'>Progressbar</a> | <a href='#tag-recommended'>Recommended</a> | <a href='#tag-simple'>Simple</a> | <a href='#tag-subprocess'>Subprocess</a> | <a href='#tag-table'>Table</a> | <a href='#tag-testing'>Testing</a> | <a href='#tag-ui'>UI</a> | <a href='#tag-user_io'>User I/O</a> | <a href='#tag-validation'>Validation</a>


<a name='tag-colored_output'></a>
#### Colored Output
* <a href='#gem-paint'>Paint</a>
* <a href='#gem-termansicolor'>Term-ansicolor</a>
* <a href='#gem-rainbow'>Rainbow</a>

<a name='tag-command_suite'></a>
#### Command Suite
* <a href='#gem-thor'>Thor</a>
* <a href='#gem-main'>Main</a>
* <a href='#gem-gli'>GLI</a>
* <a href='#gem-commander'>Commander</a>
* <a href='#gem-cri'>CRI</a>
* <a href='#gem-optitron'>Optitron</a>

<a name='tag-documentation'></a>
#### Documentation
* <a href='#gem-gemman'>Gem-man</a>
* <a href='#gem-ronn'>Ronn</a>

<a name='tag-framework'></a>
#### Framework
* <a href='#gem-methadone'>Methadone</a>
* <a href='#gem-thor'>Thor</a>
* <a href='#gem-gli'>GLI</a>

<a name='tag-inbook'></a>
#### Inbook
* <a href='#gem-methadone'>Methadone</a>
* <a href='#gem-thor'>Thor</a>
* <a href='#gem-trollop'>Trollop</a>
* <a href='#gem-main'>Main</a>
* <a href='#gem-gli'>GLI</a>
* <a href='#gem-rainbow'>Rainbow</a>
* <a href='#gem-terminaltable'>Terminal-Table</a>
* <a href='#gem-gemman'>Gem-man</a>
* <a href='#gem-ronn'>Ronn</a>

<a name='tag-parsing'></a>
#### Parsing
* <a href='#gem-methadone'>Methadone</a>
* <a href='#gem-thor'>Thor</a>
* <a href='#gem-trollop'>Trollop</a>
* <a href='#gem-main'>Main</a>
* <a href='#gem-gli'>GLI</a>
* <a href='#gem-choice'>Choice</a>
* <a href='#gem-commander'>Commander</a>
* <a href='#gem-cri'>CRI</a>
* <a href='#gem-mixlib'>Mixlib-CLI</a>
* <a href='#gem-optitron'>Optitron</a>
* <a href='#gem-slop'>Slop</a>

<a name='tag-progressbar'></a>
#### Progressbar
* <a href='#gem-formatador'>Formatador</a>
* <a href='#gem-progress_bar'>ProgressBar</a>

<a name='tag-recommended'></a>
#### Recommended
* <a href='#gem-methadone'>Methadone</a>
* <a href='#gem-main'>Main</a>
* <a href='#gem-gli'>GLI</a>
* <a href='#gem-rainbow'>Rainbow</a>
* <a href='#gem-commandlinereporter'>Command_line_reporter</a>
* <a href='#gem-gemman'>Gem-man</a>
* <a href='#gem-ronn'>Ronn</a>

<a name='tag-simple'></a>
#### Simple
* <a href='#gem-methadone'>Methadone</a>
* <a href='#gem-thor'>Thor</a>
* <a href='#gem-trollop'>Trollop</a>
* <a href='#gem-main'>Main</a>
* <a href='#gem-choice'>Choice</a>
* <a href='#gem-cri'>CRI</a>
* <a href='#gem-mixlib'>Mixlib-CLI</a>
* <a href='#gem-slop'>Slop</a>

<a name='tag-subprocess'></a>
#### Subprocess
* <a href='#gem-methadone'>Methadone</a>
* <a href='#gem-childprocess'>Childprocess</a>
* <a href='#gem-open4'>Open4</a>

<a name='tag-table'></a>
#### Table
* <a href='#gem-formatador'>Formatador</a>
* <a href='#gem-terminaltable'>Terminal-Table</a>
* <a href='#gem-commandlinereporter'>Command_line_reporter</a>

<a name='tag-testing'></a>
#### Testing
* <a href='#gem-construct'>Construct</a>
* <a href='#gem-fakefs'>FakeFS</a>
* <a href='#gem-aruba'>Aruba</a>

<a name='tag-ui'></a>
#### UI
* <a href='#gem-formatador'>Formatador</a>
* <a href='#gem-highline'>Highline</a>
* <a href='#gem-paint'>Paint</a>
* <a href='#gem-progress_bar'>ProgressBar</a>
* <a href='#gem-termansicolor'>Term-ansicolor</a>
* <a href='#gem-rainbow'>Rainbow</a>
* <a href='#gem-terminaltable'>Terminal-Table</a>
* <a href='#gem-commandlinereporter'>Command_line_reporter</a>

<a name='tag-user_io'></a>
#### User I/O
* <a href='#gem-highline'>Highline</a>

<a name='tag-validation'></a>
#### Validation
* <a href='#gem-highline'>Highline</a>






<a name='alpha'></a>
### By Name
<ul>
<a name='gem-aruba'></a>
<li><strong><a href='https://github.com/cucumber/aruba'>Aruba</a></strong> - Test your command-line app with Cucumber</li>
<a name='gem-cri'></a>
<li><strong><a href='https:/github.com/ddfreyne/cri'>CRI</a></strong> - Create simple or command-suites with a syntax that is a mix of main and GLI.</li>
<a name='gem-childprocess'></a>
<li><strong><a href='https://github.com/jarib/childprocess'>Childprocess</a></strong> - Cross-platform ruby library for managing child processes</li>
<a name='gem-choice'></a>
<li><strong><a href='https:/github.com/defunkt/choice'>Choice</a></strong> - Command-line parser for simple command-line apps</li>
<a name='gem-commandlinereporter'></a>
<li><strong><a href='https://github.com/wbailey/command_line_reporter'>Command_line_reporter</a></strong> - Create a "report", using unicode characters in the output for tables</li>
<a name='gem-commander'></a>
<li><strong><a href='https:/github.com/visionmedia/commander'>Commander</a></strong> - Create command suites with a rake-like syntax</li>
<a name='gem-construct'></a>
<li><strong><a href='https:/github.com/devver/construct'>Construct</a></strong> - Create temporary directory structure for testing</li>
<a name='gem-fakefs'></a>
<li><strong><a href='https:/github.com/defunkt/fakefs'>FakeFS</a></strong> - Fakes out various `File` and related calls to simulate a filesystem without changing system files.</li>
<a name='gem-formatador'></a>
<li><strong><a href='https:/github.com/geemus/formatador'>Formatador</a></strong> - produce rich output with a tag-like string syntax, including tables and progressbars</li>
<a name='gem-gli'></a>
<li><strong><a href='http://github.com/davetron5000/gli'>GLI</a></strong> - Create awesome, polished command suites without a lot of code</li>
<a name='gem-gemman'></a>
<li><strong><a href='https://github.com/defunkt/gem-man'>Gem-man</a></strong> - Read man pages installed with gems a la `man`</li>
<a name='gem-highline'></a>
<li><strong><a href='https:/github.com/JEG2/highline'>Highline</a></strong> - handle user input and output via a "Q&A" style API, including type conversions and validation</li>
<a name='gem-main'></a>
<li><strong><a href='http://github.com/ahoward/main'>Main</a></strong> - A class factory and DSL for generating command line programs real quick.</li>
<a name='gem-methadone'></a>
<li><strong><a href='http://www.github.com/davetron5000/methadone'>Methadone</a></strong> - Bootstrap your command line app, get all the power of `OptionParser`, but none of the verbosity</li>
<a name='gem-mixlib'></a>
<li><strong><a href='https:/github.com/opscode/mixlib-cli'>Mixlib-CLI</a></strong> - Maintained by Opscode, the maintainers of chef, this can create simple command-line apps in a readable, if verbose, syntax</li>
<a name='gem-open4'></a>
<li><strong><a href='https://github.com/ahoward/open4'>Open4</a></strong> - Open3-like library for Ruby 1.8</li>
<a name='gem-optitron'></a>
<li><strong><a href='https:/github.com/joshbuddy/optitron'>Optitron</a></strong> - Create command-suites based on classes and methods, similar to thor.</li>
<a name='gem-paint'></a>
<li><strong><a href='https:/github.com/janlelis/paint'>Paint</a></strong> - Color your output using RGB, with support for 256-color terminals</li>
<a name='gem-progress_bar'></a>
<li><strong><a href='https:/github.com/paul/progress_bar'>ProgressBar</a></strong> - create progress bars in terminal output</li>
<a name='gem-rainbow'></a>
<li><strong><a href='https://github.com/sickill/rainbow'>Rainbow</a></strong> - Create colored output</li>
<a name='gem-ronn'></a>
<li><strong><a href='https://github.com/rtomayko/ronn'>Ronn</a></strong> - Author man pages in Markdown</li>
<a name='gem-slop'></a>
<li><strong><a href='https:/github.com/injekt/slop'>Slop</a></strong> - Create simple command-line apps with a syntax similar to trollop.</li>
<a name='gem-termansicolor'></a>
<li><strong><a href='https:/github.com/flori/term-ansicolor.git'>Term-ansicolor</a></strong> - Create colored output</li>
<a name='gem-terminaltable'></a>
<li><strong><a href='https://github.com/visionmedia/terminal-table'>Terminal-Table</a></strong> - Create ASCII tables in your output, similar to a SQL clienbt</li>
<a name='gem-thor'></a>
<li><strong><a href='http://www.github.com/wycats/thor'>Thor</a></strong> - Create a command-suite app simply and easily, as well as Rails generators</li>
<a name='gem-trollop'></a>
<li><strong><a href='http://trollop.rubyforge.org'>Trollop</a></strong> - Parse the command-line idiomatically without a lot of code</li>
</ul>
