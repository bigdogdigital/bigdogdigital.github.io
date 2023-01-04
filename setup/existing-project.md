# Working on an existing site
[<< Home](/)

[<< Setting up your development environment](/setup)

The following only applies to sites built using the version of Big Rig active from late 2021 onwards. For legacy builds enquire with [Bríain](mailto:briain@bigdog.ie) as to the best approach.

For multisite projects see [Working with WordPress Multisite](setup/multisite) first.

### Sites with an existing git repository
1. Create new install with Local
2. Create local git repo in *siteDir*/app/public/ then:

    ``` 
    git remote add origin git@github.com:bigdogdigital/*repositoryname*.git
    git pull origin main
    ```
3. Fetch and checkout a local staging branch:
    
    If your local respository defaults to `master` instead of `main` execute the following:  
    ```
    git checkout -b main --track origin/main
    git branch -d master (check if this is a local settings issue)
    git branch -u origin/main
    git fetch origin staging 
    git checkout -b staging --track origin/staging
    ```
   Otherwise:
    ``` 
    git branch -u origin/main
    git fetch origin staging 
    git checkout -b staging --track origin/staging
    ```
4. Connect to WPE production site on Local and pull with database 
5. Update .htaccess with the following rule before the WordPress configuration:

    ```
    <IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteCond %{REQUEST_URI} ^/wp-content/uploads/[^\/]*/?.*$
    RewriteRule ^(.*)$ https://*staginginstallname*.wpengine.com/$1 [QSA,L]
    </IfModule>
    ```
6. Trust the SSL cert from Local

### Sites without an existing git repository
1. Follow steps 2-8 from [Starting a new project](/new-project)
2. Create local git repo in *siteDir*/app/public/
3. Copy the `.gitignore`, `.wpe-pull-ignore` & `.wpe-push-ignore` files as well as the `.github` directory from [Big Rig](https://github.com/bigdogdigital/big-rig/) and add them to the repository. 
4. Add any project specific `.gitignore` rules necessary such as:
    - [Composer](/big-rig/composer) packages
    - Integrated VueJS application `node_modules` directory 
5. Follow steps 10-16 from [Starting a new project](/new-project)