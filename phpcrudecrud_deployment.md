___________
Section 1:

The purpose of the PHP Crude CRUD Application was for us to understand and work with dynamic 
data-driven web applications. The application creates a LAMP server right on our local machine, 
and used MariaDB as our MySQL database that held a bunch of information regarding employees. 
This allows the user to look up information about an employee, specify what credentials a user 
may be looking for when searching for employees, as well as add new employees to the database 
that can be stored and viewed in the MySQL database or displayed as an HTML table. 
___________
Section 2:

___________
Section 3:

Specifications for Virtual Machine:
- - - - - - - - - - - - - - - - - -
Disk: 20GB	| CPU: 1  |	RAM: 2048
- - - - - - - - - - - - - - - - - -
___________
Section 4:

How to Create a VirtualBox Virtual Machine
If you haven’t already installed the Ubuntu 20.04 Operating System on your machine, 
skip to section 5 and then come back here to install a virtual machine.

Once you have the VirtualBox Virtual Machine downloaded and installed, then it is time
to create a a virtual machine server. 
To do this, click the blue button at the top that says New. 
Enter a name for your virutal machine server, and then for type, select Linux and then Ubuntu (64 bit).
Click next, and set your RAM to 2048, then hit next. Select create a new disk drive now; you will later change this to 20 GB. 
Click next, then select VDI (VirtualBox Disk Image). Click next, select dynamically allocated, next select 20 GB for your storage. 
Click create, and then you virtual machine is created. 

Before starting the virtual machine, this the server you created on the left, and then select settings. Click network, and then click the "Adapter 2" tab.
Then checkmark "Enable Network Adapter." This will allow you to ssh onto the server from your device with it's own IP. 

Now we need to set up the congiguration of the server by clicking your newly created server on the left, and then hit the green arrow for "Start"
This will bring you through a bunch of questions; fill them out with the information you have. Make sure you check "Open SSH" when that screen pops up,
as it will allow you to connect to this server via ssh. Otherwise, you wouldn't be able to use a fancy terminal that is much easier than the Ubunutu server interface. 

Once finished, restart the server and it should prop up a log in and password, then you can begin to use the server. Use a seperate terminal to ssh into your server with it's ip. Using the server and typing "ip addr" will show you the enp0s8 with an ip address. Use this to ssh into the server.
___________
Section 5:

Installing the Ubuntu 20.04 Operating System 
Navigate to [Oracle VM VirtualBox](https://www.virtualbox.org/) and download the
VirtualBox that is specified for you machine’s
operating system. 

When it the file finishes downloading, run the file. 
Once the software is installed, you can add a virtual machine to begin creating local servers. 

Once you ssh into your virtual machine using the terminal, type these following commands to set up the configuration.

sudo apt update
sudo apt upgrade

___________
Section 6:

Then type this command to install Apache 2:

sudo apt install apache2

This will create the /var/www/html directory, which you can navigate to and edit.

Now we need to install PHP.
Type these commands seperately in the terminal. 

sudo apt install php
--
sudo apt install libapache2-mod-php
--
sudo apt install php-cli
sudo apt install php-mysql
sudo apt install php-pgsql

Restart the server.
Once back in, create/edit a php file to test that Apache and PHP are working. 
type sudo nano testphp.php.
Add these lines to the file:

<?php>
phpinfo()
<php?>

Now, move this file to the /var/www/html folder with this command: sudo mv testphp.php /var/www/html.
Then go to your browser and type http://<your server ip address>/testphp.php. 
If this shows a page with "PHP Version 7.4.3...." then everything is working and was installed correctly. 

By creating html or php files and moving them into the /var/www/html directory, you can display the web pages by using your servers
ip address/<name of file you want to be dipslayed>


___________
Section 7:


___________
Section 8:


___________
Section 9:


___________
Section 10:
