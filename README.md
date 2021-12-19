Reference: https://upcloud.com/community/tutorials/install-openlitespeed-fast-secure-web-server/

# Ubuntu

## Step 1: Configuring firewall rules

### Install ufw firewall

`sudo apt install ufw`

### Then allow the following ports, set default rule to reject other connections and enable the firewall.

`sudo ufw allow 22,53,80,443,7080,8088/tcp`
`sudo ufw default reject`
`sudo ufw enable`

## Step 2: Install OpenLiteSpeed Web Server

`wget -O - http://rpms.litespeedtech.com/debian/enable_lst_debian_repo.sh | sudo bash`

`sudo apt update`

`sudo apt install openlitespeed lsphp74`

`sudo ln -sf /usr/local/lsws/lsphp74/bin/lsphp /usr/local/lsws/fcgi-bin/lsphp5`

`sudo /usr/local/lsws/admin/misc/admpass.sh`

## CentOS

