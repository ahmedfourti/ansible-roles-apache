Role Name: Apache
================

This role will install and configure your web-servers.  
It will install apache2/httpd (depending on your distribution), configure the virtualhost with the provided variables and enable them.  
You can configure multiple virtualhosts. See "Example" part. 

Requirements
------------

No requirements

Role Variables
--------------

**serverName** : The server name used by web server  
**http_port**: (optional) The port to listen on, if not set the default port is 80  
**serverAdmin**: (optional) Email address of the webmaster  
**docRoot**: Path to deploy the application  
**logsDir**: Path for logs    
**app_repo**: URL of the app to deploy  
**repo_version**: Your repo version. If not set, default is 'master'  

Dependencies
------------

No dependencies

Installation
------------

You can get this role by using ```git clone``` command.  
You can also add this repo to your ```requirements.yml``` and use ```ansible-galaxy install -r requirements.yml -p {{path_to_roles}}```  
Or you can download and unzip it in your roles directory 

Example Playbook
----------------


```---
   - name: Deploying Demo
     hosts:
       - web-debian
       - web-centos
     roles:
       - apache
     vars:
       apps:
         local.home:
           serverName: local.home
           http_port: 8080
           serverAdmin: root@webmaster.com
           docRoot: /var/www
           logsDir: /var/log
           app_repo: https://github.com/cfjedimaster/HTML-Code-Demos.git
           repo_version: master
         local.prod:
           serverName: local.prod
           http_port: 8080
           serverAdmin: root@webmaster.com
           docRoot: /var/www
           logsDir: /var/log
           app_repo: https://github.com/cfjedimaster/HTML-Code-Demos.git
           repo_version: master
 ```


License
-------

BSD

