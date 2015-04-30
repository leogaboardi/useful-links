#Production checklist (for Heroku)

### Useful references
https://devcenter.heroku.com/articles/rails-4-asset-pipeline

https://www.reinteractive.net/posts/116-12-tips-for-the-rails-asset-pipeline

## Allow serve assets
In `config/environment/production.rb`:
```
config.serve_static_assets = true
```
Otherwise assets will not be served in production enviroment

## Use only EBR helpers:
This will not work:
```
<img src="assets/jumbotronv2.jpg">
```
The compiled asset will be "digested", i.e. be named like `jumbotronv2-ba10fc8029bdb7490c38301fdbb1a8b4.jpg`, so the link will be broken. This will solve:
```
<img src=<%= image_path("jumbotronv2.jpg") %>>
```
Make sure to add a '.erb' extension to any files in 'app/assets' that use an ERB helper. So:

```
<%= asset_path('application.css.erb') %>
``` 

##Asset precompile

In rails environment
```
RAILS_ENV=production bundle exec rake assets:precompile
```
Does this need to be made in heroky as well>?
