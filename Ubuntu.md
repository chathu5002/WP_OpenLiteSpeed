Reference: https://upcloud.com/community/tutorials/install-openlitespeed-fast-secure-web-server/

# Ubuntu

## Step 1: Configuring firewall rules

#### Install ufw firewall

`sudo apt install ufw`

#### Then allow the following ports, set default rule to reject other connections and enable the firewall.

`sudo ufw allow 22,53,80,443,7080,8088/tcp`  
`sudo ufw default reject`  
`sudo ufw enable`  

## Step 2: Install OpenLiteSpeed Web Server and PHP

`wget -O - http://rpms.litespeedtech.com/debian/enable_lst_debian_repo.sh | sudo bash`  
`sudo apt update`  
`sudo apt install openlitespeed lsphp74`  

#### Create softlink for PHP

`sudo ln -sf /usr/local/lsws/lsphp74/bin/lsphp /usr/local/lsws/fcgi-bin/lsphp5`  

## Step 3: Setting admin password

`sudo /usr/local/lsws/admin/misc/admpass.sh` 

## Step 4: Install MySQL Database Server

`sudo apt-get install mysql-client mysql-server`

##### Optional: Install MariaDB

`sudo apt-get install mariadb-server mariadb-client`

##### Optional: (Recommended) Run a security script to remove insecure default settings and protect the database system.

`sudo mysql_secure_installation`

###### Firstly, you will be asked to install the ‘validate_password’ plugin, so type in Y/Yes and press Enter and also choose the default password strength level.

![alt text](https://github.com/chathu5002/WP_OpenLiteSpeed/Images/Set-MySQL-Root-Password.png?raw=true)

###### For the remaining questions, press Y and hit the ENTER key at each prompt.

## Step 5: Install WordPress in Ubuntu

#### Download and extract the latest version of the WordPress package.

`wget -c http://wordpress.org/latest.tar.gz`  
`tar -xzvf latest.tar.gz`

## Step 6: Host WordPress using default OLS virtual host

#### Move the WordPress files from the extracted folder to the OLS default virtual host directory, /usr/local/lsws/Example/:

`sudo mv wordpress/ /usr/local/lsws/Example/`

## Step 7: Create WordPress Database

#### Execute the command below and provide the root user password, then hit Enter to move to the mysql shell:

`sudo mysql -u root -p`

`CREATE DATABASE database_name;`  
`CREATE USER 'username'@'%' IDENTIFIED WITH mysql_native_password BY 'password';`  (MySQL)  
`CREATE USER username IDENTIFIED BY '1234';`  (MariaDB)  
`GRANT ALL ON database_name.* TO 'username'@'%';`  (MySQL)  
`GRANT ALL PRIVILEGES ON *.* TO 'username'@'%' ;`  (MariaDB)  
`FLUSH PRIVILEGES;`  
`EXIT;`

## Step 8: Obtaining SSL certificates

`sudo apt install certbot`  
`sudo certbot certonly --standalone -d <your-domain>`  
`sudo certbot certonly --non-interactive --agree-tos -m <your@email.com> --webroot -w /usr/local/lsws/Example/<virtual host> -d <your-domain>`  

## Step 9: Enabling HTTPS at the frontend

After obtaining valid SSL certificates, make the following two changes to the default listener address settings:
- Replace the port 8088 with 443
- Select Secure: Yes



# CentOS

## Step 1: Configuring firewall rules

`sudo firewall-cmd --add-service={http,https} --permanent`  
`sudo firewall-cmd --add-port={8088/tcp,7080/tcp} --permanent`  
`sudo firewall-cmd --reload`  

## Step 2: Install OpenLiteSpeed Web Server and PHP

`sudo rpm -Uvh http://rpms.litespeedtech.com/centos/litespeed-repo-1.1-1.el8.noarch.rpm`  
`sudo dnf install epel-release`  
`sudo dnf update`  
`sudo dnf install openlitespeed lsphp74`  

#### Create softlink for PHP

`sudo ln -sf /usr/local/lsws/lsphp74/bin/lsphp /usr/local/lsws/fcgi-bin/lsphp5`  

## Step 3: Setting admin password

`sudo /usr/local/lsws/admin/misc/admpass.sh` 


## Step 4: Install MySQL Database Server

`sudo apt-get install mysql-client mysql-server`

##### Optional: Install MariaDB

`sudo apt-get install mariadb-server mariadb-client`

##### Optional: (Recommended) Run a security script to remove insecure default settings and protect the database system.

`sudo mysql_secure_installation`

###### Firstly, you will be asked to install the ‘validate_password’ plugin, so type in Y/Yes and press Enter and also choose the default password strength level.

![alt text](https://github.com/chathu5002/WP_OpenLiteSpeed/blob/main/Set-MySQL-Root-Password.png?raw=true)

###### For the remaining questions, press Y and hit the ENTER key at each prompt.
