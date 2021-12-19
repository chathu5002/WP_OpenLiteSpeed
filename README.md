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

### Step 3: Setting admin password

`sudo /usr/local/lsws/admin/misc/admpass.sh` 



# CentOS

## Step 1: Configuring firewall rules

`sudo firewall-cmd --add-service={http,https} --permanent`  
`sudo firewall-cmd --add-port={8088/tcp,7080/tcp} --permanent`  
`sudo firewall-cmd --reload`  

## Step 2: Install OpenLiteSpeed Web Server

`sudo rpm -Uvh http://rpms.litespeedtech.com/centos/litespeed-repo-1.1-1.el8.noarch.rpm`  
`sudo dnf install epel-release`  
`sudo dnf update`  

sudo dnf install openlitespeed lsphp74

