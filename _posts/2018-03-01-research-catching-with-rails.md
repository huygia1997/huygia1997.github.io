---
layout: post
title: Research caching with rails
tags:
---

<font color="blue">
	* Caching means to store content generated during the request-response cycle and to reuse it when responding to similar requests
	- Caching is often the most effective way to boost an application's performance. 
</font>

By default, caching is only enabled in your production environment. To play around with caching locally you'll want to enable caching in your local environment: config.action_controller.perform_caching = true

<h1 style="color: red">
	Fragment Caching
</h1>

- store cache by variable of components which have same cache characteristic.
- When different parts of the page need to be cached and expired separately you can use Fragment Caching.
- Rails uses the timestamp value to make sure it is not serving stale data. If the value of updated_at has changed, a new key will be generated

<h1 style="color: red">
	Russian Doll Caching
</h1>
- You may want to nest cached fragments inside other cached fragments. This is called Russian doll caching
- Example: cache game nested inside cache company, if any cache game update, the old cache will be expired, but the old company cache will be not expired. => use touch:true to solve this.

<h1 style="color: red">
	Low-level caching
</h1>

- to cache a particular value or query result instead of caching view fragments. Rails' caching mechanism works great for storing any kind of information.
- The most efficient way to implement low-level caching is using the Rails.cache.fetch method. This method does both reading and writing to the cache.

<h1 style="color: red">
	SQL caching
</h1>
- cache the result return by sql query. if that query is requested again, the result in cache will be returned => increase performance

<h1 style="color: red">
	Cache store
</h1>
:namespace - This option can be used to create a namespace within the cache store. It is especially useful if your application shares a cache with other applications.

:compress - This option can be used to indicate that compression should be used in the cache. This can be useful for transferring large cache entries over a slow network.

:compress_threshold - This option is used in conjunction with the :compress option to indicate a threshold under which cache entries should not be compressed. This defaults to 16 kilobytes.

:expires_in - This option sets an expiration time in seconds for the cache entry when it will be automatically removed from the cache.

<h2>* ActiveSupport::Cache::MemoryStore</h2>
- config.cache_store = :memory_store, { size: 64.megabytes }
- This cache store keeps entries in memory in the same Ruby process
- When the cache exceeds the allotted size, a cleanup will occur and the least recently used entries will be removed. (remove cai gan day it dc su dung)

<h2>* ActiveSupport::Cache::FileStore</h2>
- config.cache_store = :file_store, "/path/to/cache/directory"
- As the cache will grow until the disk is full, it is recommended to periodically clear out old entries.

<h1 style="color: red">
	Caching in Development
</h1>
$ bin/rails dev:cache  
Development mode is now being cached.  
$ bin/rails dev:cache  
Development mode is no longer being cached.
