---
layout: post
title: Research debugging
tags:
---

* 3 ways to inspect to contents of variables:
- debug, to_yaml, inspect
(YAML) display content as a hash( pair of key:value)

<h1 style="color: red"> What is the Logger?</h1>
- Rails makes use of the ActiveSupport::Logger class to write log information. Other loggers, such as Log4r, may also be substituted


<h1 style="color: red"> Logs level</h1>
- If you want to know the current log level, you can call the Rails.logger.level method.
- The available log levels are: :debug, :info, :warn, :error, :fatal, and :unknown, corresponding to the log level numbers from 0 up to 5, respectively. To change the default log level, use: 
' config.log_level = :warn '

** Logging will always have a small impact on the performance of your Rails app, particularly when logging to disk, Using the :debug level will have a greater performance penalty than :fatal


<h1 style="color: red"> byebug gem</h1>
install : $ gem install byebug

Inside any Rails application you can then invoke the debugger by calling the byebug method

All request after byebug will be hung until the debugger has finished.

Use command 'help' to see all supported commands, for some examples :
- use 'list' to show 10 previous lines
- use 'instance_variables' to see all variables from controller
- use 'step' or 's' to continue your process
- use'quit' or 'q' to quit byebug

