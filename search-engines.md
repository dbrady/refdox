# Search Engines

I wish Google would make custom search engines shareable across multiple
accounts. Easiest way is probably to make them {ex,im}portable like Nescape
bookmarks files.


## ruby

Search ruby-doc.org (ruby core and stdlib) and apidock.com (rails)

* Search Engine: ruby
* bind to: ruby
* url: https://www.google.com/search?q=%28site%3Aruby-doc.org+OR+site%3Aapidock.com%29+%s


## ruby3

Search ruby-doc.org, but confine search to current version of ruby

* Search engine: Ruby 3.x Docs
* bind to: ruby3
* url: https://www.google.com/search?q=site%3Aruby-doc.org+%28inurl%3Acore-3+OR+inurl%3Astdlib-3%29+%s
