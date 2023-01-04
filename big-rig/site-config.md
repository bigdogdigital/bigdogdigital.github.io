# Big Rig theme configuration
[<< Home](/)

[<< Working with Big Rig](/big-rig)

The first step should be naming the theme for the current project. Update `/wp-content/themes/bigrig/config/config.json`. 

```json
{
  "slug": "*themename*",
  "name": "*Site Name*",
  "PHPNamespace": "*Sitename*\\*Sitename*"
}
```

In general these options will be reflective of the client's name e.g. for Big Dog:

```json
{
  "slug": "bigdog"
  "name": "Big Dog Digital",
  "PHPNamespace": "BigDog\\BigDog"
}
```

### <a name="Fonts"></a>Font Files
1. Download the project fonts and add them to the `/assets/fonts` directory.
2. Replace the `@font-face` declarations in `assets/css/src/_fonts.scss` with ones for your project.
3. Update the `$global-font-family` and `$heading-font-family` variable declarations in `assets/css/src/_variables.scss`.

### <a name="Variables"></a>Variables
`assets/css/src/_variables.scss` contains a variety of SASS variables for use throughout the project. 

Initially updates should be:

1. Colour variables
    - Add all of the project colours with descriptive names (line 29)
    - Map `$brand-primary` and `$brand-secondary` to declared variables.
    - Default text (`$color-text`) and heading (`$color-heading`) colours
2. Ensure global font size, weight, and line-height variables are correct. These will usually be aligned with the Design System but be sure to check on a project-by-project basis
3. `$header-logo-width` and `$header-logo-width-mobile` are used for SVG logos. You can generally pull these values directly from the design files. If mobile designs aren't present scale the site down to mobile and set a width which looks appropriate.
4. Update the shadow variables (line 147) to align with the project. If necessary update the variable names to describe them more accurately e.g. if there's different colour shadows used instead of sizes `$shadow-black` and `$shadow-grey` may be more appropriate. If you change the variables or add extra ones be sure to [Change the Bootstrap utilities map](/big-rig/css-js#Bootstrap-api) to reflect this

### <a name="Typography"></a>Typography
`assets/css/src/_typography.scss` contains all of the standard styles and some utility classes for text, but is set up so that initially you may not need to make any changes.

Add or update any global rules for headings (line 107), then update your individual heading mixins in `assets/css/src/_bdd_mixins.scss`

From line 168 there are several classes for standard, visited and hover states for various colours. Add, remove or update these as necessary.

Inline link styles can be modified in `assets/css/src/_links.scss` 

### <a name="Buttons"></a>Buttons
`assets/css/src/_buttons.scss` contains all of the standard classes and extends used for button styled elements across the site, mapped to mixins in. `assets/css/src/_bdd_mixins`.

Classes are set up for two 'standard' and one 'ghost' button. If your project has different values to these, duplicate and rename both a full set of classes and the mixins then rename them e.g.

```scss
/* Secondary */

a.bd-btn-three,
a.bd-btn-three:visited {
	@include btn_three
}

button.bd-btn-three,
input.bd-btn-three,
li.bd-btn-three a {
	@extend a.bd-btn-three;
}

a.bd-btn-three:hover {
	@include btn_three_hover;
}

button.bd-btn-three:hover,
input.bd-btn-three:hover,
li.bd-btn-three a:hover {
	@extend a.bd-btn-three:hover;
}
```

```scss
@mixin btn_three {
	background-color: $colo;
	border-color: $color;
	color: white;

	&:focus {
		outline-color: $color;
		color: white;
	}
}

@mixin btn_three_hover {
	background-color: darken($another-color, 10%);
	border-color: darken($another-color, 10%);
	color: white;
}
```
### <a name="Forms"></a>Forms
There are two stylesheets for forms; `assets/css/src/forms.scss` for standard HTML forms and `assets/css/src/gforms.scss` for any forms outputted byt the Gravity Forms plugin. Both of them use mixins from `assets/css/src/_bdd_mixins.scss` to style the standard form elements

### <a name="Unused"></a>Removing unused elements
Many elements included in the theme will not be relevant to your project. This is non-exhaustive, but should serve as a guide as to what to look for. 

- Does your site features widgets, comments or sidebars? Will you be using the gutenberg editor? Then you should remove their [Components](/big-rig/components) and stylesheets.
- Some stylesheets have rules for elements or classes you may not use e.g. `<blockquote>`, `<table>`, `<abbr>` and many more. Have a quick scan through the standard stylesheets and remove anything that definitely won't be needed.
- The Swiper [Library](/big-rig/css-js#Libraries) is included but your project may not use sliders
 

[Template parts >>](/big-rig/template-parts)