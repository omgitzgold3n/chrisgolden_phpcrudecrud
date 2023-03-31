___________
__*Section 1 - PHP Crude Crud Application Guide*__

The purpose of the PHP Crude CRUD Application was for us to understand and work with dynamic 
data-driven web applications. The application creates a LAMP server right on our local machine, 
and used MariaDB as our MySQL database that held a bunch of information regarding employees. 
This allows the user to look up information about an employee, specify what credentials a user 
may be looking for when searching for employees, as well as add new employees to the database 
that can be stored and viewed in the MySQL database or displayed as an HTML table. 

___________
__*Section 2 - Deployment Overview*__

The PHP Crude Crud Deployment involves several steps to set up and configure so that you are able 
to create functional websites that can be accessed on your machine via a virutal machine server. 
You will need to install Oracle's VirtualBox from their website for whatever device you are using, 
and then you will need to create virtual machines that are local servers on your machine. After the 
VirtualBox is installed, and you've created virtual machine servers, you can begin installing Apache
and PHP so that you can create php and html files that can be displayed in a browser. Once files are 
created and stored on the /var/www/html directory on your local server, you can deploy your PHP Crude
Crud Application using it's ip address and file location on the server in your web browser. 


___________
__*Section 3*__

Specifications for Virtual Machine:
```
Disk: 20GB	| CPU: 1  |	RAM: 2048
```

___________
__*Section 4 - Create a Virutal Machine*__

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
__*Section 5 - Install Ubuntu 20.04 OS*__

Installing the Ubuntu 20.04 Operating System 
Navigate to [Oracle VM VirtualBox](https://www.virtualbox.org/) and download the
VirtualBox that is specified for you machine’s
operating system. 

When it the file finishes downloading, run the file. 
Once the software is installed, you can add a virtual machine to begin creating local servers. 

Once you ssh into your virtual machine using the terminal, type these following commands to set up the configuration.
```
$sudo apt update
$sudo apt upgrade
```
___________
__*Section 6 - Install Apache 2 and PHP*__

Now we need to set up Apache so that we can run functioning websites. 
Type this command to install Apache 2:
```
$sudo apt install apache2
```
This will create the /var/www/html directory, which you can navigate to and edit.

Now we need to install PHP.
Type these commands seperately in the terminal. 
```
$sudo apt install php
$sudo apt install libapache2-mod-php
$sudo apt install php-cli
$sudo apt install php-mysql
$sudo apt install php-pgsql
```
Restart the server.
Once back in, create/edit a php file to test that Apache and PHP are working. 
type sudo nano testphp.php.
Add these lines to the file:

```
<?php>
phpinfo()
<php?>
```

Now, move this file to the /var/www/html folder with this command: sudo mv testphp.php /var/www/html.
Then go to your browser and type http://(your server ip address)/testphp.php. 
If this shows a page with "PHP Version 7.4.3...." then everything is working and was installed correctly. 

By creating html or php files and moving them into the /var/www/html directory, you can display the web pages by using your servers
ip address/<name of file you want to be dipslayed>


___________
__*Section 7 - Install MySQL*__

Next, we need to install MySQL so that we can type commands and add users later on in the database.
 
```
$ sudo apt update
$ sudo apt upgrade 
$ sudo apt install mariadb-server
$ sudo systemctl status mariadb
$ mysql -V
```
You will see this output after the mysql -V command:
```
$ mysql  Ver 15.1 Distrib 10.3.38-MariaDB, for debian-linux-gnu (x86_64) using readline 5.2
```
Next, type this command to secure your MySQL installation:
```
$ sudo mysql_secure_installation
```
You will recieve a long output, this means everything worked. Now it's time to restart mariaDB.
```
$ systemctl restart mariadb
```
Create a user on MySQL by doing the following command:
```
$ sudo mysql
```
Then, once you're in mariaDB, type this command and type in your username and password that you will use
everytime you use mariaDB.
```
MariaDB [(none)]> create user '<your username>'@'localhost' identified by 'your password';
MariaDB [(none)]> grant all privileges on *.* to '<your username>'@'localhost';
MariaDB [(none)]> flush privileges;

```
Make sure you always use a semilcolon ";" at the end of each line. When you want to quit, type control Z.

To check that MySQL is working, you can go to section 10 and download the github repository with a 
database.
 
___________
__*Section 8 - Configuration Information for PHP credentials needed to connect to database*__

You need to have your server running in order to connect to any php or html files you have saved 
on your machine in the /var/www/html file. You don't need to save everything in this directory in 
order to run a php or html file, though it's nice to have everything saved and stored in a 
directory. To run a php or html file, type:
 
```
http://<your_server_ip>/<thefilename>
```
 
If your file is in another folder that isn't specified in the /var/www/html directory, you will need to add
the directory name before the file with a / and this should work then. 

___________
__*Section 9 - Deploy PHP Crude Crud Application*__
Once you have created the PHP application, you can now deploy it to an existing cloud server.
You want to make sure you download this key, and move it into your .ssh files on your local user. 
 This filename looks like this below, and can be found at https://canvas.umn.edu/courses/349316/assignments/3118287.
```
INET4031_Spring_2023.pem
```
Then you want to make a zip file of your php application on your server;
```
tar -zcvf <your name>_phpcrudecrud.tar.gz phpcrudecrudapp/
```
Now, on your local machine terminal, you want to move the application using the .ssh key provided to us.
Type in this following command using your information:
```
$ scp -i .ssh INET4031_Spring_2023.pem <yourname>_phpcrudecrud.tar.gz ubuntu@18.119.121.213:.
```
This sends your zipped php directory to the server, and then you can ssh into this server by typing this:
```
$ ssh -i .ssh/INET4031_Spring_2023.pem ubuntu@18.119.121.213
```
Now, you can extract the zip file, and move the contents into a directory by naming it <yourname>_phpcrudecrud:
```
$ tar -xvf <yourname>_phpcrudecrud.tar.gz
```
Now we need to move the "phpcrudecrudapp" you created in ther server by doing the following:
```
ubuntu@ip-172-31-3-146:~$ mv phpcrudecrudapp/ <your name>_phpcrudecrud
```
Then, we must move our application to the /var/www/html directory so we can view it on the browser. In the 
ubuntu server directory, type this command:
```
$ sudo cp -R <yourname>_phpcrudecrudapp/ /var/www/html
```
cd into the /var/www/html directory and make sure your application is located in there. 

Now you will be able to see your php crude crud application by typing in your browser: http://18.119.121.213/<your name>_phpcrudecrudapp
If you don't see it, you didn't follow a step correctly. 
 
___________
__*Section 10 - Suggested Tests*__
 
Test any php file or html file if it's working by typing 
```
http://<your_server_ip>/<thefilename>
```
in the browser.
If the conneciton doesn't work, then your file may not be in the right directory. Also make sure you ip address is typed correctly. 

To test if you correctly installed MySQL and PHP, you can clone this git hub repository with a database created.
```
$ git clone https://github.com/datacharmer/test_db.git
```
Now, open up mariaDB:
```
$ mysql -u <yourusername> -p
```
Now you can run MySQL commands to look at the databases, and select employees and do multiple commands to see how the database works.
