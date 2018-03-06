---
layout: post
title: Research assets-pipeline
tags:
---

## <font color="red">1. What is assets-pipeline</font>
- it provides the framework to concatenate and minify or compress JS, CSS assets
- it can also write these assets in other languages and pre-processors such as CoffeeScript, Sass and ERB
- it is implemented by gem  sprockets-rails gem, and is enabled by defaut.


*** <b>Fingerprinting technical</b>
- make name of file dependent on the content of file, file changed => name changed
- it avoid query strings to reduce problems

<h1 style="color: red"> Using assets-pipeline</h1>
- At subdirectory : app/assets
-  Any assets under public will be served as static files by the application or web server when config.public_file_server.enabled is set to true. 
- In production, Rails precompile those file to public/assets by default. The precompiled copies are then served as static assets by the web server. File in app/assets never be run directly

* if the coffee-rails or sass-rails is in Gemfile, when you generate the controller or scafford, Rails automatically generate .coffee and .scss file.

* You can also disable generation of controller specific asset files by adding the following to your config/application.rb configuration:  
(config.generators do |g|  
  g.assets false  
end)

<h2 style="color: blue"> Assets organization</h2>
- app/assets: store your custom code (js, css, ...)
- lib/assets: store your custom code but can use for another apps
- vendor/assets: store third-party's code, use helper to edit their code


