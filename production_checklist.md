#Production checklist (for Heroku)

##Asset precompile
Add in /config/environments/production.rb:
```
config.assets.precompile = ['*.js', '*.css', '*.css.erb']
```

In rails environment
```
RAILS_ENV=production bundle exec rake assets:precompile
```
