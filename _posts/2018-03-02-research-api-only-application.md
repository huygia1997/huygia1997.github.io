---
layout: post
title: Research using Rails for API-only Applications
tags:
---

<h1 style="color: red">
	Why Use Rails for JSON APIs?
</h1>

- The reason most people use Rails is that it provides a set of defaults that allows developers to get up and running quickly, without having to make a lot of trivial decisions

<h3 style="color: green">
	Creating a new application
</h3>
* $ rails new my_api --api
- it will do 3 main things for you:
+ not done
+ not done
+ not done

<h1 style="color: red">
	Changing an existing application
</h1>

- In config/application.rb: config.api_only = true
- In config/environments/development.rb: config.debug_exception_response_format = :default (it will set to :api when config.api_only is 'true')
- inside app/controllers/application_controller.rb:  

-- class ApplicationController < ActionController::API  
-- end

<h1 style="color: red">
	Choosing Middleware
</h1>
An API application comes with the following middleware by default:

- Rack::Sendfile
- ActionDispatch::Static
- ActionDispatch::Executor
- ActiveSupport::Cache::Strategy::LocalCache::Middleware
- Rack::Runtime
- ActionDispatch::RequestId
- ActionDispatch::RemoteIp
- Rails::Rack::Logger
- ActionDispatch::ShowExceptions
- ActionDispatch::DebugExceptions
- ActionDispatch::Reloader
- ActionDispatch::Callbacks
- ActiveRecord::Migration::CheckPending
- Rack::Head
- Rack::ConditionalGet
- Rack::ETag
- MyApi::Application::Routes

<h3 style="color: green">
	Using the Cache Middleware
</h3>

- using the stale? method: will compare the If-Modified-Since header in the request with @post.updated_at. If the header is newer than the last modified, this action will return a "304 Not Modified" response. Otherwise, it will render the response and include a Last-Modified header in it.



