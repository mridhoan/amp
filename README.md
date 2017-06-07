# The AMP Minimal Theme

This theme is based on the Minimal [Github Pages](https://pages.github.com/) theme, which is in turn based on @orderedlist's [Minimal](https://github.com/orderedlist/minimal).

The Theme has been updated to be compatible with Google's [AMP Project](https://www.ampproject.org/). Therefore their is custom information located below, in the [Google AMP Limitations](#google-amp-limitations) section, to help you use this theme.

## Usage

1. Fork the project

2. Download the [Zip](https://github.com/lafronzt/AMP-Minimal/archive/master.zip) and create your own repository.

3. Clone the Project
    ```git
    git clone git@github.com:lafronzt/AMP-Minimal.git
    ```

Than use this theme just like any other Jekyll theme.

## Examples of Use

### [My Portfolio](https://work.lafronz.com)
* Running with some custom CSS on top

![](https://work.github.com/images/examples/AMP-Minimal-Example.png)

## Customizing

### Configuration variables

Minimal will respect the following variables, if set in your site's `_config.yml`:

```yml
title: [The title of your site]
description: [A short description of your site's purpose]
```

Additionally, you may choose to set the following optional variables:

```yml
show_downloads: ["true" or "false" to indicate whether to provide a download URL]
google_analytics: [Your Google Analytics tracking ID]
```

### Stylesheet

If you'd like to customize the styling:

1. Open the file `_includes/style.scss`
2. Ensure that the following code is located at the top:
    ```scss
    @import "jekyll-theme-minimal";
    ```
3. Add any custom CSS (or Sass, including imports) you'd like immediately after the `@import` line

### Layouts

If you'd like to change the theme's HTML layout:

1. Open and edit the file called `/_layouts/default.html` in your site
2. Customize the layout as you'd like

*Keep in mind: AMP does not allow inline styling, or JS files.*

## [](#google-amp-limitations)Google AMP Limitations

Google AMP sets many
[strict limits on what you can include in your web pages](https://www.ampproject.org/docs/get_started/technical_overview.html).
A few of these are worth talking about:

*Limitation: All CSS must be inline which is automaticly generated from the `_includes/style.scss`.*

Because of this, the main css file for this site is in `_includes/style.scss`
instead of in the normal `css/` Jekyll folder. This css file is inlined
into the header of every page via the special `scssify` filter in `_layouts/default.html`.

*Limitation: Size all resources statically*

Every image you include in your page *must* have a height and width. This also
applies to other things like embedding videos or other resources. Check below
for more details.

## Writing Posts with Google AMP

Writing posts works
[just like it does normally in Jekyll](https://jekyllrb.com/docs/posts/)
except when you want to include extra resources likes pictures, videos,
embedded Twitter posts, etc.

Google AMP has it's own set of special html tags for including content. You
should use these instead of normal Markdown or HTML tags.

The one you are most likely to need is `<amp-img>`:

### Images in your posts

```
<amp-img width="600" height="300" layout="responsive" src="/assets/images/your_picture.jpg"></amp-img>
```

### Embedding other types of content

The AMP Project provides helpers for many other types of content like audio,
ads, Google Analytics, etc.

* Built-in AMP tags:
 * https://github.com/ampproject/amphtml/blob/master/builtins/README.md

* Extended AMP tags:
 * https://github.com/ampproject/amphtml/blob/master/extensions/README.md

## Validating your page with Google AMP

Google AMP adds built-in validation logic to make sure your pages follow all
the rules so they render as fast as possible.

To check your page, just add `#development=1` to any url on your site and then
check the javascript console in your browser.

http://localhost:4000/#development=1

You will either see a success message:

```
Powered by AMP ⚡ HTML – Version 1457112743399
AMP validation successful.
```

Or you will see a list of errors to fix:

```
Powered by AMP ⚡ HTML – Version 1457112743399
AMP validation had errors:
The attribute 'style' may not appear in tag 'span'
The attribute 'style' may not appear in tag 'div'
```
