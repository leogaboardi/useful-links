#Production checklist (for Heroku)

##Asset precompile
Tips:
https://www.reinteractive.net/posts/116-12-tips-for-the-rails-asset-pipeline

Layout view:
```
<%= stylesheet_link_tag    "bootstrap.min", media: "all", "data-turbolinks-track" => true %>
<%= stylesheet_link_tag    "styles", media: "all", "data-turbolinks-track" => true %>
<%= javascript_include_tag "application", "data-turbolinks-track" => true %>
```
Add in /config/environments/production.rb:
```
config.assets.precompile = ['*.js', '*.css', '*.css.erb']
```

In rails environment
```
RAILS_ENV=production bundle exec rake assets:precompile
```
