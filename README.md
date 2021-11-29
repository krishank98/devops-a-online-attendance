Attendance-System
=================

The project is meant to create an advanced attendance taking system to help teachers, 
students and college administration by automating the entire process. It is designed keeping 
scalability and code- reusability in mind, which means that the same project can be altered 
by changing few variables to get desired results. Furthermore, there’s scope of adding more 
functionality without disturbing any of the existing one. This is made possible by using 
Object Oriented Programming, a Modular for designing web service, and following large 
parts of MVC model. This allows us to extend the project to mobile applications and other environments.

Video Demo : 

https://www.projectworlds.in/online-attendance



A. Host a sample PHP application on Apache on Local

-Get a sample PHP application from internet

-Install the DB component (MYSQL)

-Integrate the PHPO app with MySQL DB

-Accept connection only from PORT 8000 on Apache 

-Apply reverse proxy to redirect the pages to PORT 80 [Internally]


/////////////////////////////////
add 8000,80 to security group
///////////////////////////////////
lamp stack installation on ubuntu

https://www.techomoro.com/how-to-run-a-php-application-on-ubuntu-18-04-2-lts/
/////////////////////
project url

https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-20-04
and
https://projectworlds.in/free-projects/php-projects/online-attendance-system-php-mysql-bootsrap/
and
https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-16-04

//////////////////////
4: IMPORTANT STEP:

if you are using UBUNTU server in AWS run following command

  sudo cat /etc/mysql/debian.cnf
you will see output like this >>>

---------------------------------------------------------
# Automatically generated for Debian scripts. DO NOT TOUCH!
  [client]
  host     = localhost
  user     = debian-sys-maint
  password = 24cZSZPgPZECdDyT               
  socket   = /var/run/mysqld/mysqld.sock
  [mysql_upgrade]
  host     = localhost
  user     = debian-sys-maint
  password = 24cZSZPgPZECdDyT
  socket   = /var/run/mysqld/mysqld.sock
//////////////////////
change apache port to 8000

sudo vi /etc/apache2/ports.conf
change Listen 80 to Listen 8000
sudo systemctl restart apache2

///////////////////

change port forwarding 

sudo iptables -t nat -I PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 8000
sudo iptables -I INPUT -p tcp --dport 8000 -j ACCEPT
sudo tcpdump -i any -n port 80
///////////////////////

http://port/foldername
