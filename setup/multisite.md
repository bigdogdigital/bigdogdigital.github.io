# Working with WordPress Multisite
[<< Home](/)

[<< Setting up your development environment](/setup)

Local currently does not support connecting to WPEngine for WordPress Multisite installs and only supports them being run on an NginX server. This means that:
- Images cannot be mapped from the WPE install to your local one. To remedy this either:
	- Use a single (or small amount of) placeholder image uploaded to the both the local and remote installs during development
	- Remove the `wp-content/uploads/*` ignore rule from `.wpe-pull-ignore` and sync the full media library when pulling from WPEngine
- We have to sync the database using an alternative method.
	- Install WP Migrate DB Pro on the WPE site
	- Connect to WPE site via SFTP and download plugins
	- Log in to WPE site and copy WP Migrate DB Pro API key for DB Pull
	- Log in to local site. Network Admin >> Settings >> Migrate DB Pro
	- Add API key and pull full DB to local