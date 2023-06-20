# WordpressWebsite_AWS_EC2

Deploying your WordPress Website on AWS EC2

1.Launch an EC2 Instance:

Log in to the AWS Management Console.
Go to the EC2 service.
Click on "Launch Instance" to start the instance creation wizard.
Choose an Amazon Machine Image (AMI) that supports WordPress, such as an Amazon Linux 2 or Ubuntu Server.

2.Launch an EC2 Instance:

Log in to the AWS Management Console.
Go to the EC2 service.
Click on "Launch Instance" to start the instance creation wizard.
Choose an Amazon Machine Image (AMI) that supports WordPress, such as an Amazon Linux 2 or Ubuntu Server.

1. Install Apache server on Ubuntu
sudo apt install apache2

2. Install php runtime and php mysql connector
sudo apt install php libapache2-mod-php php-mysql

3. Install MySQL server
sudo apt install mysql-server 

4. Login to MySQL server
sudo mysql -u root

5. Change authentication plugin to mysql_native_password (change the password to something strong)
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password by 'Testpassword@123';

6. Create a new database user for wordpress (change the password to something strong)
CREATE USER 'wp_user'@localhost IDENTIFIED BY 'Testpassword@123';

7. Create a database for wordpress
CREATE DATABASE wp;

8. Grant all privilges on the database 'wp' to the newly created user
GRANT ALL PRIVILEGES ON wp.* TO 'wp_user'@localhost;

9. Download wordpress
cd /tmp
wget https://wordpress.org/latest.tar.gz

10. Unzip
tar -xvf latest.tar.gz

11. Move wordpress folder to apache document root
sudo mv wordpress/ /var/www/html

12. Command to restart/reload apache server
sudo systemctl restart apache2
OR
sudo systemctl reload apache2

13. Install certbot
sudo apt-get update
sudo apt install certbot python3-certbot-apache

14. Request and install ssl on your site with certbot
sudo certbot --apache

Access WordPress in a Browser:

Obtain the public IP address of your EC2 instance from the AWS EC2 console.
Open a web browser and enter the following URL:
http://

