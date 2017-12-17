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

**vhost_state**: The vhost state (present or absent)  
**serverName**: The server name used by web server  
**serverAlias**: The serverAlias
**docRoot**: Path to deploy the application         
**http_port**: (optional) The port to listen on, if not set the default port is 80    
**http_host**: (optional) The IP to use, if not set the default is "*"   
**http_port_disabled**: (optional) List of port to disable   
**serverAdmin**: (optional) Email address of the webmaster      
**app_repo**: URL of the repo to deploy  
**repo_version**: Your repo version. If not set, default is 'master'    
**package_state**: The package state (present, installed, latest, absent or removed)      
**apache_modules**: Modules to install for Debian Systems    
**httpd_modules**: Modules to install for RedHat Systems        
  


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
     become: yes
     vars:
       vhosts:
         local.home:
           vhost_state: present
           serverName: local.home
           serverAlias: local.home
           http_port: 80
           http_host: '*'
           serverAdmin: root@webmaster.com
           docRoot: /var/www
           logsDir: /var/log
           app_repo: https://github.com/cfjedimaster/HTML-Code-Demos.git
           repo_version: master
         local.prod:
           vhost_state: absent
           serverName: local.prod
           serverAlias: local.prod
           http_port: 81
           http_host: '*'
           serverAdmin: root@webmaster.com
           docRoot: /var/www
           logsDir: /var/log
           app_repo: https://github.com/cfjedimaster/HTML-Code-Demos.git
           repo_version: master
       mods_enabled:
         - cgi.load
         - filter.load
       http_port_disabled:
         - 8080
         - 8181
 ```


License
-------

BSD

