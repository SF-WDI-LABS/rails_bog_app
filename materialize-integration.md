## Integrating Materialize into your Rails Project

In your Gemfile, add the `jquery-rails` gem and the `materialize-sass` gem:

```ruby
gem 'jquery-rails'
gem 'materialize-sass'
```

Double check that the `sass-rails` gem is present - it is added to new Rails applications by default. If it's there, then run ``` bundle install ```.  After you install, you'll need to restart your rails server.

In `app/assets/stylesheets`, make sure to change the file extension of `application.css` to `application.scss`. Import Materialize styles in `app/assets/stylesheets/application.scss` using the following syntax:

```scss
@import "materialize";
```

As is, this approach can limit your selection of colors in Materialize, so you can change your import statements to give you the ability to edit them. From the `materialize-sass` documentation:

> Since materialize color scheme are declared in color.scss you should import the color.scss first. then you can override color variable just like this:
```scss
@import "materialize/components/color";
$primary-color: color("blue", "lighten-2") !default;
$secondary-color: color("yellow", "base") !default;
@import 'materialize';
```

If you want to include the materialize icons in your Rails project.

```scss
 @import "https://fonts.googleapis.com/icon?family=Material+Icons";
```

Finally, require Materialize javascripts in `app/assets/javascripts/application.js`:

```js
//= require jquery
//= require materialize
```
