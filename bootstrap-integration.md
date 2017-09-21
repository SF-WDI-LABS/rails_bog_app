## Integrating Bootstrap into your Rails Project

First, install the `jquery` gem and the `bootstrap-sass` gem by adding

```ruby
gem 'jquery-rails'
gem 'bootstrap-sass', '~> 3.3.6'
```

to your gemfile. Double check that the `sass-rails` gem is present - it is added to new Rails applications by default. If it's there, then run ``` bundle install ```.  After you install, you'll need to restart your rails server.

In `app/assets/stylesheets`, make sure to change the file extension of `application.css` to `application.scss`. Import Bootstrap styles in `app/assets/stylesheets/application.scss` using the following syntax:

```scss
@import "bootstrap-sprockets";
@import "bootstrap";
```

`bootstrap-sprockets` must be imported before `bootstrap` for the icon fonts to work. This `@import` syntax is SASS syntax and takes the place of using the `require` syntax. In order to accommodate that change, remove all the `*= require_self` and `*= require_tree .` statements from the sass file. Instead, use `@import` to import Sass files. For example, if you build a `scss` file called `app/assets/stylesheets/homepage.scss`, you would include the line:

```scss
@import "homepage";
```

in `app/assets/stylesheets/application.scss`.


Do not use `*= require` in Sass or your other stylesheets will not be [able to access](https://github.com/twbs/bootstrap-sass/issues/79#issuecomment-4428595) Bootstrap mixins or variables.

Require Bootstrap Javascripts in `app/assets/javascripts/application.js`:

```js
//= require jquery
//= require bootstrap-sprockets
```

[Don't include both `bootstrap-sprockets` and `bootstrap`](https://github.com/twbs/bootstrap-sass/issues/829#issuecomment-75153827) in `application.js`; `bootstrap-sprockets` provides individual Bootstrap Javascript files (`alert.js` or `dropdown.js`, for example), while
`bootstrap` provides a concatenated file containing all Bootstrap Javascripts.
