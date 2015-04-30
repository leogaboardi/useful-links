#Production checklist (for Heroku)

https://devcenter.heroku.com/articles/rails-4-asset-pipeline

## Allow serve assets
In `config/environment/production.rb`:
```
config.serve_static_assets = true
```

Otherwise assets will not be served in production enviroment

## Use only EBR helpers:
This will not work because of the production of a "digest":
```
<img src="assets/jumbotronv2.jpg">
```
The compiled asset will be named like jumbotronv2-ba10fc8029bdb7490c38301fdbb1a8b4.jpg, so the link will be broken. This will solve:
```
<img src=<%= image_path("jumbotronv2.jpg") %>>
```
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
