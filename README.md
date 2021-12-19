## Step 1: Install OpenLiteSpeed Web Server on Ubuntu

Reference: https://upcloud.com/community/tutorials/install-openlitespeed-fast-secure-web-server/

`wget -O - http://rpms.litespeedtech.com/debian/enable_lst_debian_repo.sh | sudo bash`
`sudo apt update`

`sudo apt install openlitespeed lsphp74`

`sudo ln -sf /usr/local/lsws/lsphp74/bin/lsphp /usr/local/lsws/fcgi-bin/lsphp5`

`sudo /usr/local/lsws/admin/misc/admpass.sh`

