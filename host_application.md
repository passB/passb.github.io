---
title: The passb host application
---
To allow passb to communicate with your password-store installation, you have to install the [passb host application](https://github.com/passB/nodeHostApp).

## downloading the host application

### bundled with node.js

There are bundled ready-to-run downloads available at [the github replease page](https://github.com/passB/nodeHostApp/releases). 

### from source

If you already have an installation of node.js in a recent version, you just use that. In this case, just clone the repository:

`git clone https://github.com/passB/nodeHostApp.git`

## installation

To install the host application, depending on your platform, run `install_host_app.sh firefox` (Linux and Mac OS) or `install_host_app.bat firefox` (Windows)

Be sure to do this from a console, where `pass` is available and working. The installer will snapshot the following environment variables so that they are also available when called from Firefox:
 * `PATH` 
 * `HOME` 
 * `GNUPGHOME` 
 * `PASSWORD_STORE_DIR` 
 * `PASSWORD_STORE_GPG_OPTS` 
 * `PASSWORD_STORE_ENABLE_EXTENSIONS`

If you want to change any of those values in the future, just re-run the installer script from a console that is configured approriately. 

[back to the main site](./index.html)