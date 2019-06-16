# Install in Production
!!! warning
    Please remember that the OpenDataMap is currently in an early alpha state of development and that we cannot guarantee that it's running stable.

## Install node.js
Please install node.js in version `10`, `11` or `12` with npm. For most operating systems you find the install guide on [here](https://nodejs.org/en/download/package-manager/)

## Download OpenDataMap
Execute the following command as a normal user (not root/sudo):
```
git clone https://github.com/OpenDataMap/opendatamap
cd opendatamap
npm install
``` 

## Run as background process via pm2
```
npm install -g pm2
cd [$OpenDataMap-Directory]
pm2 start main.js --name opendatamap --prod [$PORT]
```

## Connection to webserver
The OpenDataMap server will listen on the port you defined. You may want to use a reverse proxy on your webserver to pass a domain to the OpenDataMap instance:

- [nginx](https://docs.nginx.com/nginx/admin-guide/web-server/reverse-proxy/#pass)
- [apache2.4](https://httpd.apache.org/docs/2.4/mod/mod_proxy.html#examples)