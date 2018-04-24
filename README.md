# phpmyadmin-configuration
#### whole php my admin configuration

PHPMYADMIN configuration and how to install it.
this file is created by Mehdi Filban ...

first of all 
	
	apt update
	apt install phpmyadmin
	
	set all configurations in the setup 
	if you cannot add a password dont worry about that.

	just ignore it.
	and do the following things.

	nano /etc/phpmyadmin/apache.conf
	make sure that you add the below changes
	
		<Directory /usr/share/phpmyadmin>
	        Options SymLinksIfOwnerMatch
                DirectoryIndex index.php
    	        (you have to add this line)AllowOverride All

	
	and then 
	
	systemctl reload apache2.service
	
	and the next step is to create a .htaccess file by running the commands below
	
	sudo nano /usr/share/phpmyadmin/.htaccess

	and the you should add the content below and just save it

		AuthType Basic
		AuthName "Restricted Files"
		AuthUserFile /etc/phpmyadmin/.htpasswd
		Require valid-user

	and 
	
	sudo apt-get install apache2-utils

	Finally, run the commands below to create an account for mehdi.

	sudo htpasswd -c /etc/phpmyadmin/.htpasswd mehdi

	and then 
	
	sudo -H gedit /etc/apache2/apache2.conf

	and then add this line somewhere
	
	Include /etc/phpmyadmin/apache.conf

	and the last step is to run ...
	
	sudo service apache2 restart
