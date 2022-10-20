# Documentation of project 1
### In this project, i learnt about other Web Stack Implementation used in AWS.
### In this project, i learnt and worked with LEMP (Linux, Nginx, MySQl, PHP) WEB STACK.
### This project was done using the steps below:
#### 1. Setup AWS account and Provisioned an Ubuntu Server
### 2. Created an EC2 Instance and Connected to the EC2 Instance
- Got the SSH link of the Instance

![SSH link](./images\connect-instance1.PNG)

-Pasted the SSH link to  the terminal and connectted to the instance

![SSH connect](./images\ssh.PNG)
### 3. Installed Nginx by running the code:
`sudo apt update`

`sudo apt install nginx`

![installig Nginx](./images\install-nginx.PNG)
### Verified that nginx is running in the OS using the code:
`sudo systemctl status nginx`

![Nginx status](./images\nginx-stat.PNG)

### 4. I logged on into my new site using my IP address:
[My site](http://44.211.200.92:80)
![My site](./images\nginx-site.PNG)

### 5. Installed MySQL and logged into it by running the codes respectively:
`sudo apt install mysql-server`
![MySQL](./images\install-mysql.PNG)

`sudo mysql`
![MySQL login](./images\mysql_login.PNG)

### 6. Installed PHP using the code:
`sudo apt install php-fpm php-mysql`

### The version of the installed PHP was confirmed using the code:
`php -v`
![PHP version](./images\php-installed.PNG)

### 7. Configuring Nginx to Use PHP Processor:
### - Created the root web directory for my domain as using the code:
`sudo mkdir /var/www/projectLEMP`

### - Assigned ownership of the directory with the $USER environment variable, which will reference the current system user:
`sudo chown -R $USER:$USER /var/www/projectLEMP`

### - Opened a new configuration file in Nginx’s *sites-available* directory:
`sudo nano /etc/nginx/sites-available/projectLEMP`

### - Pasted in, the bare-bones configuration as shown below:
![Site comfiguration](./images\config-nginx.PNG)

### - Activated the configuration by linking to the config file from Nginx’s *sites-enabled* directory:
`sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/`

### -  The configuration was tested for syntax errors using the code:
`sudo nginx -t`
![Test comfiguration](./images\test-nginx.PNG)

### - The default Nginx host that is currently configured to listen on port 80 was disabled by running:
`sudo unlink /etc/nginx/sites-enabled/default`

### - Nginx was reloaded to apply the changes using:
`sudo systemctl reload nginx`

### - An index.html file was created in the /var/www/projectLEMP directory to test if the new server block works as expected:
`sudo echo 'Hello LEMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectLEMP/index.html`

### The result as shown in picture below revealed that the comfiguration was successful:
![Site update](./images\site-update1.PNG)

### 8. Testing PHP with Nginx

### -  A new file called *info.php* was crreated within your document root:
`sudo nano /var/www/projectLEMP/info.php`

### - The following lines of code was typed into the new file as shown below:
![Site update](./images\site-update2.PNG)

### - By accessing the site using the IP address (`http://44.211.200.92/info.php`), the result shown below revealed the details of the site in PHP perspective.
![Site update](./images\site-update1.PNG)

### - Since the page shown contain sensitive details about the site, it is best to remove the file from the directory
### This was done using:
`sudo rm /var/www/your_domain/info.php`

### 9. Retrieving data from MYSQL database with PHP

### -  I connectted to the MySQL console using the root account:
`sudo mysql`

### - Created a new database, by running the following command from the MySQL console:
![create database](./images\create-user.PNG)

### -  Created a new user and granted full privileges on the database using the following codes shown below:
![create user](./images\create-user1.PNG)

### - Gave the user permission over the example_database database:
![permit user](./images\create-user2.PNG)

### -  Logged in to the MySQL console again using the custom user credentials:
`mysql -u example_user -p`

### - Createt a test table named *todo_list* by running the following statement on th MySQL console:
![create dtable](./images\create-table.PNG)

### - Inserted the following few rows of content in the test table:
>mysql> INSERT INTO example_database.todo_list (content) VALUES ("My first important item");

>mysql> INSERT INTO example_database.todo_list (content) VALUES ("My second important item");

>mysql> INSERT INTO example_database.todo_list (content) VALUES ("My third important item");

>mysql> INSERT INTO example_database.todo_list (content) VALUES ("and this one more thing");

### - To confirm that the data was successfully saved on the table, the code below was run on Mysql console:
>mysql>  SELECT * FROM example_database.todo_list;

### The result is showm below:
![update table](./images\update-table.PNG)

### - Then exited the Mysql

### -  Createt a PHP file in the web root directory to hold a PHP script that will connect to MySQL and query for the content  of the *todo_list table*, and displayed the results in a list.
`nano /var/www/projectLEMP/todo_list.php`

### - The following content as shown below was copied into your todo_list.php script and saved:
![update table](./images\php-script.PNG)

###  By visiting the address [My PHP site](http://44.211.200.92/todo_list.php), the content that was inserted in the test table was shown:
![update table](./images\site-update4.PNG)

### This is an indication that the PHP environment is ready to connect and interact with your MySQL server.
### This PBL project has further helped in making me to understand LEMP as a WEB STACK technology and its usefulness in modern day software production.