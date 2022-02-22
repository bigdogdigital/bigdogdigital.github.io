# Template Parts
[<< Home](/)

[<< Working with Big Rig](/big-rig)

Templates in the theme should make wide use of [template parts](https://developer.wordpress.org/reference/functions/get_template_part/).

The starting framework has a suggested structure in `/template-parts` but keep in mind this can be modified or may not be suitable for your project at all.

```
- content //general template parts 
    - components //individual components
        - post //components strictly related posts, not pages 
    - sections //full sections
        - post //sections strictly used on post templates
- footer //strictly used in footer 
- header //strictly used in header
```

For example a template part used for social media links which is used on both the contact page and in the footer would be `template-parts/content/components/social_icons.php`.

Big Rig will check for a [registered stylesheet and script](/big-rig/css-js#Templatepart-css-js) with the same name as a template part whenever it is used on the site e.g. when `template-parts/content/components/social_icons.php` is called a stylesheet at `assets/css/src/template-parts/social_icons.min.css` will be added as long as it is configured correctly.

Named variations of template parts are also encouraged. For example you have social media icons that will be used on a blog template which will require some additional styles not used in the footer or contact page. You can create `template-parts/content/components/post/social_icons-blog.php` (it goes in the /post sub-folder because we are only using this on the single blog template) and register `assets/css/src/template-parts/social_icons.min.css`. **Both** the original stylesheet and the new one will be printed when the named variation is used but only the original stylesheet when the standard template part is used.

Any user inputted data that needs to be made available to the template part should be added through an ACF 'group' field with the same name as the template part, and individual fields in that group representing the data used in the template part. The ACF field can then be retrieved and passed into the template part as additional arguments in the `get_template_part()` function. This allows flexibility in the source of the data to be used in a template part e.g. hard-coded or from a [custom block](/big-rig/blocks)

If we add the above into a single example the template or template part where the social icons are outputted on the blog page would include this:

```php
$social_icons_blog_args = get_field('social_icons-blog');
get_template_part('content/components/post/social_icons', 'blog', $social_icons_blog_args);
``` 

[Components >>](/big-rig/components)