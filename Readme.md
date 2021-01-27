#check uou have all visual studio dependecy packages you have down load and check from the below
https://wampserver.aviatechno.net/files/tools/check_vcredist.exe

#if something missing download allin one package
https://us5-dl.techpowerup.com/files/wHT6aCm273xA9WhHOTWufg/1596800301/Visual-C-Runtimes-All-in-One-Jul-2020.zip

#first install wamp server
https://versaweb.dl.sourceforge.net/project/wampserver/WampServer%203/WampServer%203.0.0/wampserver3.2.3_x64.exe

#enable ssl_module in apache


#modify your httpd.conf to listen in the port 80 and 443

Listen 0.0.0.0:80
Listen *:80
Listen 0.0.0.0:443
Listen *:443

#create virtual host for your domain dont touch the localhost virtual entry
#also check windows host file have the virtual host created otherwise created that
add well known entry before directory declaration
Alias /.well-known "c:/wamp64/www/eblucare/.well-known"
---------------------------------------------------------------------------------
# Virtual Hosts
#
<VirtualHost *:80>
  ServerName localhost
  ServerAlias localhost
  DocumentRoot "${INSTALL_DIR}/www"
  Alias /.well-known "c:/wamp64/www/.well-known"
  <Directory "${INSTALL_DIR}/www/">
    Options +Indexes +Includes +FollowSymLinks +MultiViews
    AllowOverride All
    Require local
  </Directory>
</VirtualHost>


#
<VirtualHost *:80>
	ServerName www.lok.ecare.com
	ServerAlias lok.ecare.com
	DocumentRoot "c:/wamp64/www/ecare"
	Alias /.well-known "c:/wamp64/www/ecare/.well-known"
	<Directory  "c:/wamp64/www/ecare/">
		Options +Indexes +Includes +FollowSymLinks +MultiViews
		AllowOverride All
		Require all granted
	</Directory>
</VirtualHost>
-----------------------------------------------------------------------
#allow every one access your webroot and 80 http port
#Configure a record for your website and create cname for www .if its subdomain means create www record like www.subdomain target ip.

#install certbot
https://dl.eff.org/certbot-beta-installer-win32.exe

#run as admin cmd and enter the below command

certbot certonly --webroot

a. enter your email for renewal
b. agree
c. efw agree
d. enter your webroot path
e. enter your domain name comma seprated venketraman.com,www.venketraman.com

#thats all set your certificate stored in c drive cerbot\live folder
#now you going to configure ssl path and redirection in your virtual host folder

#now your site is ssl protected.

if you are confused with localhost virtual host entry change the port number
all the example files are attached.




