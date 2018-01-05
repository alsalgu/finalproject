# Udacity Final Project: Linux Configuration
----
**Url:** http://52.32.45.238
**IPv4 Public IP:** 52.32.45.238
**Public DNS (IPv4):** ec2-52-32-45-238.us-west-2.compute.amazonaws.com
**Port:** 2200
**Summary:** 
- Added '*****' as a user, generated an RSA key for them and placed it in their authorized_keys. 
- Gave sudo access to '*****'. 
- Changed the default port to 2200 and set up the UFW firewall to only accept incoming requests to ports SSH's 2200, HTTP's 80, and NTP's 123. 
- Disabled remote log-ins for root and changed the default password for the default users (ubuntu and root). 
- Updated the list of system packages and upgraded them. 
- Installed postgresql. 
- Upgraded python to version 3 as well and installed third-party resources I used for the Item Catalog project. 
- Git cloned in my Item Catalog project's [repository](https://github.com/alsalgu/myBarn) to Apache's /var/www directory and changed Apache's config to host the project. 
- Allowed Apache to read and write from the database directory. 

**Third-Party Resources:** Python packages(passlib, sqlalchemy, flask, itsdangerous, httplib2, Flask-HTTPAuth, requests)