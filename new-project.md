# Starting a new project

- Take fresh WPEngine backup of bdstarterrig
- Create new environment, production install _installname_ copied from bdstarterrig
- Create the staging install _staginginstallname_, and use the WPE Copy Environment feature to deploy the new production install to it. (it's generally a good idea to name the staging install the same as production with '-dev' appended e.g. _mynewsite_ and _mynewsite-dev_)
- Generate SSH key pair if necessary
	- A single pair of keys will be sufficient for accessing all WPEngine installs. These can also be used for the WPE SSH Gateway
- Copy your SSH public key and add to the Git Push section of the both production and staging installs on the WPEngine dashboard
- Create new repository on github git@github.com:bigdogdigital/_repositoryname_.git (repository and WPE production install names should be the same)
- Copy and add private & public SSH keys as github repository secrets in Settings>>Secrets>>Actions
```
WPENGINE_SSH_KEY_PRIVATE
WPENGINE_SSH_KEY_PUBLIC
```
- Create new install with Local, ensuring to run on an Apache server
- Create local git repo in _siteDirectory_/app/public/ then:
```
git remote add bigrig git@github.com:bigdogdigital/big-rig.git
git pull bigrig main
git remote remove bigrig
//TODO: Add step here to remove commit history
```
- update .github/workflows/production.yml
```
WPENGINE_ENVIRONMENT_NAME: _installname_
```
- update .github/workflows/staging.yml
```
WPENGINE_ENVIRONMENT_NAME: _staginginstallname_
```
- Ensure your default git branch is ```main```. If it's ```master``` do the following:
```
git checkout -b main
git branch -d master
```
- Push to github
```
git remote add origin git@github.com:bigdogdigital/repositoryname.git
git add .
git commit -m 'initial commit'
git push -u origin main
git checkout -b staging
git push -u origin staging
``` 
- Update .htaccess with the following rule before ```# BEGIN WordPress```:
```
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteCond %{REQUEST_URI} ^/wp-content/uploads/[^\/]*/?.*$
RewriteRule ^(.*)$ https://{{staginginstallname}}.wpengine.com/$1 [QSA,L]
</IfModule>
```
- Trust the SSL cert from Local
- Connect to WPE staging site on Local and pull with database