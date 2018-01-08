## Integrating Bootstrap into your Rails Project

First, install the `jquery` gem and the `bootstrap-sass` gem by adding

```ruby
gem 'jquery-rails'
gem 'bootstrap', '~> 4.0.0.beta3'
gem 'sprockets-rails'
```

to your gemfile. Double check that the `sass-rails` gem is present - it is added to new Rails applications by default. If it's there, then run ``` bundle install ```.  After you install, you'll need to restart your rails server.

In `app/assets/stylesheets`, change the file extension of `application.css` to `application.scss`. Remove the `*= require_self` and `*= require_tree .` statements and use `@import` (SASS syntax for `require`) to import SASS files.  Import Bootstrap using the following syntax:

```scss
@import "bootstrap";
```

You can include other `scss` files using the same `@import` syntax. For example, if you created a new SASS file called `app/assets/stylesheets/homepage.scss`, you would include the following line in `app/assets/stylesheets/application.scss`:

```scss
@import "homepage";
```


Do not use `*= require` in Sass or your other stylesheets will [not be able to access](https://github.com/twbs/bootstrap-sass/issues/79#issuecomment-4428595) Bootstrap mixins or variables.

Next, require Bootstrap Javascripts in `app/assets/javascripts/application.js`:

```js
//= require jquery3
//= require bootstrap
```

You could alternatively require `bootstrap-sprockets` instead of `bootstrap`, but [don't include both](https://github.com/twbs/bootstrap-sass/issues/829#issuecomment-75153827) in `application.js`; `bootstrap-sprockets` provides individual Bootstrap JS files (`alert.js` or `dropdown.js`, for example), while `bootstrap` provides a concatenated file containing all Bootstrap JS.
