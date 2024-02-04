Create a VM
Open port 80 on VM NIC NSG and Subnet NSG
#installing apache2
sudo apt update && sudo apt install apache2
sudo systemctl status apache2
curl localhost:80 also curl publicip:80 on a different machine
sudo apt install mysql-server
sudo mysql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';
exit
sudo mysql_secure_installation
sudo mysql -p
exit
#installing php
sudo apt install php libapache2-mod-php php-mysql
#After installation is done, run the following command to confirm your PHP version: php -v
#CREATING A VIRTUAL HOST FOR YOUR WEBSITE USING APACHE
sudo mkdir /var/www/projectlamp
sudo chown -R $USER:$USER /var/www/projectlamp
sudo vi /etc/apache2/sites-available/projectlamp.conf
#add these lines in file
<VirtualHost *:80> 
    ServerName projectlamp 
    ServerAlias www.projectlamp 
    ServerAdmin webmaster@localhost 
    DocumentRoot /var/www/projectlamp 
    ErrorLog ${APACHE_LOG_DIR}/error.log 
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
####
sudo a2ensite p<F12>rojectlamp
sudo a2dissite 000-default
sudo apache2ctl configtest
sudo systemctl reload apacche2
sudo vi /var/www/projectlamp/index.html
## add data to this file
## Enable php on the website
sudo vim /etc/apache2/mods-enabled/dir.conf then: #Change this: #DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm #To this: DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
sudo systemctl reload apache2
vim /var/www/projectlamp/index.php
## this to the file <?php phpinfo();
save and close

