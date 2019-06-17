# Linking with webserver
The OpenDataMap will listen on the port you defined. You may want to use a reverse proxy on your webserver to pass a domain to the OpenDataMap instance. Please follow the guide for your webserver, if your webserver is not in the list, you should search in the manual of your webserver for _reverse proxy_ 
##nginx
Include the following block in your vhost (`server`-context):
```
location / {
    proxy_pass http://localhost:[$PORT];
}
```
or if you want to have the opendatamap in a specific subdirectory (as example `opendatamap.net/demo`):
```
location /demo/ {
    proxy_pass http://localhost:[$PORT];
}
```

For more informations visit the [nginx documentation](https://docs.nginx.com/nginx/admin-guide/web-server/reverse-proxy/#pass).
## apache2.4
For all options please enable `mod_proxy` with `a2enmod mod_proxy`. Except in most cases of shared hosting you don't need that.

If you have access to the webserver configuration you can use the **VirtualHost** method otherwise you can only use the **.htaccess** method.
For more informations visit the [apache2 documentation](https://httpd.apache.org/docs/2.4/mod/mod_proxy.html). 
### VirtualHost
Include the following block in the VirtualHost of the domain:
```
ProxyPass "/"  "http://localhost:[$PORT]/"
ProxyPassReverse "/"  "http://localhost:[$PORT]/"
```
### .htaccess
Please place the following block in a file named .htaccess in the directory of the domain.  
```
RewriteEngine On
RewriteRule (.*) http://localhost:[$PORT]/$1 [P]
```