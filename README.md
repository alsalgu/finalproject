# Udacity Final Project: Linux Configuration
----
**Url:** http://52.32.45.238  
**IPv4 Public IP:** 52.32.45.238  
**Public DNS (IPv4):** ec2-52-32-45-238.us-west-2.compute.amazonaws.com  
**Port:** 2200  
**Summary:**
- I created an account on Amazon's Lightsail and created an virtual host machine instance running Ubuntu 16.04.3
- Once the instance was running, I installed PuTTy as my go-to ssh client. This allowed me to log in as the default user, Ubuntu.
- After logging in, I did what any sane person would do and quickly re-configured the default users. I changed the passwords, disabled root login, and changed the default ports.
````
sudo passwd
sudo passwd root
sudo nano /etc/ssh/sshd_config
````
- In sshd_config , the port it listens for from '22' to '2200', PermitRootLogin to 'No', and changed the need for Key Authentication to Yes.
- I then created a user for the Udacity reviewer and gave them sudo access.
````
sudo adduser Udacity
usermod -aG sudo Udacity
````
- Afterwards, I set up the Uncomplicated Firewall (UFW). I checked what was opened and added/denied the ports according to rubric specifications. Then I activated the firewall.
````
sudo ufw status
sudo ufw deny [port]/tcp
sudo ufw add [port]/tcp
sudo ufw enable
````
- Then I updated and upgraded the list of system packages, as well as installed Apache, Python 3 and Postgresql. I also installed the third-party resources I needed to run my Item Catalog project.
````
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install apache2
sudo pip3 install (Python resource)
````
- This next part was the hardest for me to do. Plenty of trial and error. I got Apache to run just fine, but it was getting the wsgi file to pick up my project that proved tricky.  I configured Apache's site directory to be my project's repository I pulled from GitHub and to run the WSGI file that would import my app.
````
cd /var/www
sudo git pull (repository link to create /var/www/myBarn
sudo apt-get -y install libapache2-mod-wsgi-py3
sudo touch /var/www/myBarn/app.wsgi
sudo nano /etc/apache2/sites-enabled/000-default.conf
````
- I kept reading the error log and editing my app's python files until it ran smoothly. When everything was ready to go, I checked and adjusted permissions accordingly, reloaded ssh/apache services, and did one last final upgrade. Fortunately, doing a full upgrade didn't break my app or anything else.
````
sudo chmod 600
sudo chown www-data mybarnapp.py
sudo apt-get update
sudo apt-get dist-upgrade
````
-Oh, I also generated a key for the Udacity reviewer's account. 
````
cd ~/.ssh
ssh-keygen -t rsa -C "the email I put"
sudo nano authorized_keys
````
-I also changed the timezone to UTC at some point.
````
-sudo dpkg-reconfigure tzdata
````
I believe that was it.


**Third-Party Resources:** Python packages: passlib, sqlalchemy, flask, itsdangerous, httplib2, Flask-HTTPAuth, requests.
