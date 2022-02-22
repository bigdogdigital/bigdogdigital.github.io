# Components
[<< Home](/)

[<< Working with Big Rig](/big-rig)

Big rig uses the [PHP Class Component](https://wprig.io/documentation/php-architecture-in-wp-rig/) architecture of WP Rig. Their documentation includes full reference for creating and modifying components so we will focus on the purpose of the Components included in Big Rig by default.

Some components have been left without description as their names should speak for themselves. When adding new Components you should keep this in mind too.

- **Accessibility** Adding attributes and markup and functionality for accessibility purposes
- **ACF** Adding Advanced Custom Fields related functionality like options pages
- **Base_Support** WordPress theme supports
- **Blocks** Gutenberg block registrations and related functions
- **Bootstrap** Bootstrap functions like making breakpoints available server-side
- **Cleanup** Removing extraneous WordPress data like scripts for emojis, comments etc.
- **Comments**
- **Custom_Logo** Varieties of ways to add the site logo to the frontend
- **Editor** Functionality and theme supports specific to Gutenberg
- **Forms** Gravity Forms plugin and other form functions
- **Header_Code** Outputting external code like analytics in the site header
- **Helper** Developer specific and minor utility functions
- **Images**
- **Localisation** Localisation and translation functions
- **Mail** SMTP and emails
- **Nav_Menus** Menu functions and nav_walkers
- **Posts** CPT declarations and post data modification
- **Scripts**
- **Sidebars**
- **Styles**
- **Swiper** Initialisation for Swiper library use

When declaring new functions they should be added to a relevant existing Component (Class) or have a new one created to house it e.g. a function to remove the default Gutenberg scripts if the editor isn't being used would go in Cleanup.php (and remove Blocks.php entirely) but a function to add new REST API endpoints would go in it's own new Component.  

[Styles & scripts >>](/big-rig/css-js)