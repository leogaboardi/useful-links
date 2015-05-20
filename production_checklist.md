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

## Setup pg server:
in Gemfile:

```
gem 'pg'
```

Optional (if you don't want to set up the posgreSQL locally):
```
group :development, :test do
  gem 'sqlite3'
end
```

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
## Put newrelic

`gem 'newrelic_rpm'`
Download and put the yaml file in `application_name/config`

## Check if app name in git matches Heroku:
If terminal send an app-not-found message: 
'''
git remote rm heroku
git remote add heroku git@heroku.com:yourappname.git
'''

## Databases

```
rake db:create:all
heroku run rake db:create
heroku run  rake db:migrate
```
Check if seed work in production (or: should I care?)

## Setup Amazon S3 for paperclip storage

https://devcenter.heroku.com/articles/paperclip-s3

https://devcenter.heroku.com/articles/direct-to-s3-image-uploads-in-rails

## Put configuration variables

You can check configuration variables in 
```
$heroku config
```

```
$ heroku config:set AWS_SECRET_ACCESS_KEY=your_secret_access_key
```
(Note there is no need for "" in the string names)
So you can put code such as
```
  :secret_access_key => ENV['AWS_SECRET_ACCESS_KEY'],
```
