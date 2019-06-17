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