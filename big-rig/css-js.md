# Styles & scripts
[<< Home](/)

[<< Working with Big Rig](/big-rig)

### Adding Styles & Scripts<a name="Adding"></a>
New SASS and JS files should be added to the `/src/` subdirectory of `assets/css` and `assets/js` respectively.

To register/enqueue a file it should be added to the array in `get_css_files()` or`get_js_files()`. The key of the array item should be `wp-rig-*filename*` as it will be used as the handle for the script or style when registered. This is particularly important for template part files.

Stylesheets accept the following  parameters:
- `file` _String_ Location of the **compiled** file within the `assets/css/` directory.
- `global` _Boolean_ Whether the stylesheet should be automatically enqueued on every page or not
- `preload_callback` _Function_ Returning true will add the preload attribute to the link tag. Should be used for stylesheets with very specific locations e.g. forms. Otherwise pass `return __false;`

 Scripts accept the following  parameters:
 - `theme_file` _Boolean_ Whether the script is located in the theme or not. 
 - `file` _String_ Location of the **compiled** file within the `assets/js/` directory. If `theme_file` is `false` a full URL should be passed.
 - `global` _Boolean_ Whether the script should be automatically enqueued on every page or not
 - `preload_callback` _Function_ (optional) Returning true automatically enqueue the script. Should be used for scripts present on specific pages.
 - `deps` _Array_ Script dependencies. Values should be other keys in the array
 - `footer` _Boolean_ Whether to add the script in the site `<footer>`
 - 'loading' _String_ Pass `defer` or `async` to add these loading attributes, otherwise `false`/`null`
 - `localise` _Array_ Data to be used with [`wp_localise_script()`](https://developer.wordpress.org/reference/functions/wp_localize_script/)
    - `object_name` _String_ JSON object on which data will be accessible in the script
    - `object` _Array_ Data to be made available
    
<a name="Templatepart-css-js"></a> Template part styles and scripts should follow the above rules as well as the following:
- The source files should always be located in `/src/template-parts`
- The handle *must* and the file name should match the template part filename
- `global` and callbacks should always be set to false

 
### Libraries<a name="Libraries"></a>


### Bootstrap utilities API<a name="Bootstrap-api"></a>

### Custom Utility Classes<a name="Custom-utilities"></a>

### Gravity Forms<a name="Gravity-forms"></a>

### Global Scripts<a name="Global-scripts"></a>


[Images >>](/big-rig/images)