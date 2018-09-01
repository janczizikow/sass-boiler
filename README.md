# Sass Boiler

Sass boilerplate using [7-1 architecture pattern](https://sass-guidelin.es/#the-7-1-pattern), [OCSS](http://thesassway.com/intermediate/using-object-oriented-css-with-sass) and [BEM](http://getbem.com/) naming conventions.

## Setup

There're no depedencies (only normalize.css, but it's already included for you in the files), so all you need to do precomiple SCSS to CSS. The styles are not prefixed so you should do it yourself.

### Prefixing

You can use [autoprefixer-rails](https://github.com/ai/autoprefixer-rails) to prefix the styles. Add `autoprefixer-rails` to your gemfile:

```
gem 'autoprefixer-rails'
```

Install the gem with

```
bundle
```

### Adding stylesheets

Replace Rails' stylesheets (make sure you're in your project's root directory):

```
rm -rf app/assets/stylesheets
curl -L https://github.com/janczizikow/sass-boiler/archive/master.zip > stylesheets.zip
unzip stylesheets.zip -d app/assets && rm stylesheets.zip && mv app/assets/sass-boiler-master app/assets/stylesheets && rm app/assets/stylesheets/.gitignore && rm app/assets/stylesheets/.scss-lint.yml
```

### Viewport tag

Make sure that you have viewport & X-UA-Compatible meta tag's in your layout:

```
<!-- app/views/layouts/application.html.erb -->
<head>
  <!-- Add these line for detecting device width -->
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">

  <!-- [...] -->
</head>
```


### Adding new `.sccs` files

Take a look at your `application.scss` file to see how the files are imported. The order in which you import files is important as well. As opposed to [Le Wagon stylesheets](https://github.com/lewagon/rails-stylesheets), scss partials are imported explicitly to the main stylesheet (one file per `@import;`). This is intended in order to offer more visiblity to what is actually imported to the main stylesheet and in-line with SASS recommended architecture. You can read more about the folder structure [here](https://sass-guidelin.es/#the-7-1-pattern).

```
// app/assets/stylesheets/application.scss

@charset "UTF-8";

@import "abstracts/variables";
@import "abstracts/functions";
@import "abstracts/mixins";
@import "abstracts/placeholders";

@import "vendor/normalize";

@import "base/base";
@import "base/fonts";
@import "base/typography";
@import "base/helpers";

@import "layout/grid";
@import "layout/header";
@import "layout/footer";

@import "components/banner";
@import "components/button";
@import "components/card";
@import "components/input";
@import "components/tabs";

// TODO: Add your page imports below:


// TODO: If your project contains different themes import them below:

```

### Header animations

The header component includes ["checkobx hack"](https://css-tricks.com/the-checkbox-hack/) to animate navigation links sliding down on mobile devices. No JS required to make this work :wink: You can also take a look at [this codepen](https://codepen.io/hollow3d/pen/ygBvQw) to see the "checkbox hack" in action. Basically it uses `:checked` with [general sibling combinator](https://developer.mozilla.org/en-US/docs/Web/CSS/General_sibling_selectors) (`~`).

#### Header links delay



