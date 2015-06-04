# useful-links
Compilation of useful links explaining several tools that are used in coding

- Setting up postgres (databased used in rails that is understandable by Heroku
http://stackoverflow.com/questions/7086654/installing-postgres-on-windows-for-use-with-ruby-on-rails

- Tutorial on sending emails
http://www.gotealeaf.com/blog/handling-emails-in-rails

- How to set up Amazon S3 for Paperclip
https://devcenter.heroku.com/articles/paperclip-s3

- Railscasts.com

- Favorites.offset(random(Favorites.count)).first  (hint for pagination)
- respond_to do |format|

## Useful gems
- paperclip
- activeadmin
- ransack gem (for search functions)

## Other useful stuff
- Ajax: on the link_to tag, add:
``` :remote => true ``` 
- The request works without reloading the page, but it does not update the view. Add responder block
``` respond_to do |format|
  format.html do
    redirect_to "/index",:notice => "deletedL
  end
  format.js do
    render('destroy.js.erb')
  end
```

-Lastly: add the useful code in the js.erb file. Note the js.erb file stays in the view mode:

$('favorite('favorite.dadsadasd').hide();



