# Columns DIY #

A WordPress plugin that enables two simple shortcodes for generating div-based columns and rows. Wrap the desired content block in `[column]` `[/column]`. Mark the end of a row with `[endrow]`. CSS not included.

## Description ##

This plugin is intended for theme developers and others who want to have full control of their column styles while still providing a quick and easy framework for adding/editing column content via WordPress's visual editor. It eliminates the need to type tedious, unmanageable chunks of HTML into the editor when specific posts or pages require a columnar layout.

That said, this plugin is not plug-and-play. It does not include any styles out-of-the-box, so if you start using the shortcodes without adding appropriate CSS rules, there probably won't be any visible changes to your content.

### Usage ###

* Designate each column with `[column]` and `[/column]`
* Mark the end of a row with `[endrow]`

### Features ###

* Enumerates columns and rows, allowing for per-column and -row styling.
* If a user forgets to add the last `[endrow]` shortcode, the plugin will automatically insert a closing `</div>` so the site layout doesn't get broken.
* Cleans up errant `<p>` and `</p>` tags that result from Wordpress's `wpautop()` function.

### Example ###

Putting this into the visual editor:
> `[column]`
>
> This is the column of Foo.
>
> `[/column]`
>
> `[column]`
>
> This is the column of Bar.
>
> `[/column]` `[endrow]`

Will result in this output:
```html
<div class="diy-row diy-row-1">
<div class="diy-column diy-column-1">
<p>This is the column of Foo.</p>
</div>
<!-- end diy-column-1 -->

<div class="diy-column diy-column-2">
<p>This is the column of Bar.</p>
</div>
<!-- end diy-column-2 -->
</div><!-- end diy-row-1 -->
```

### Parameters ###

The following optional parameters can be added to the `[column]` shortcode:

* _class_ (String : '')
Classes for the column `<div>` element. Separate multiple classes with spaces.
* _rowclass_ (String : '')
Classes for the row `<div>` element. Only works when included with the first `[column]` shortcode in a row.
* _style_ (String : '')
Inline styles for the column `<div>` element.
* _norow_ (Boolean : false)
Set to true to omit the row wrapper `<div>`.

## Installation ##

1. Upload the `columns-diy` folder to the `/wp-content/plugins/` directory
1. Activate the plugin through the 'Plugins' menu in WordPress

There are a few different options for adding the CSS to style your columns:

* Edit the `style.css` file in your theme. This is *not* recommended if you are using a third-party theme such as a commercial theme or one downloaded from the WordPress Theme Directory. Your changes will be lost if/when you update the theme to a new version.
* Create a [child theme](http://codex.wordpress.org/Child_Themes).
* Use a plugin such as [CSS & JavaScript Toolbox](http://wordpress.org/extend/plugins/css-javascript-toolbox/) to embed the styles without modifying your theme.
* Use the `style` parameter in the `[column]` shortcode to add inline styles. Only recommended for "one-off" scenarios (and how often does a "one-off" remain that way?).
