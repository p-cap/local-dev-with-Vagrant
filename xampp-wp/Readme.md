# Local installation
Download XAMPP
- https://www.apachefriends.org/download.html
- get the latest 
- wget <download-link>
- chmod 700 <.run-file>
- ./<.run-file>
- edit sudo vi /opt/lampp/etc/extra/httpd-xampp.conf
'''
# since XAMPP 1.4.3
<Directory "/opt/lampp/phpmyadmin">
    AllowOverride AuthConfig Limit
    # Require local
    Require ip 10.10
    ErrorDocument 403 /error/XAMPP_FORBIDDEN.html.var
</Directory>
- sudo /opt/lampp/xampp restart


'''
- open the XAMPP web console
- click on "phpMyAdmin"
- click on "database" 
- click on "create" (e.g. pcap)
- mkdir /opt/lampp/htdocs/pcap & cd /opt/lampp/htdocs/pcap 
  - NOTE: the folder created is the same name of the database
- download wordpress and select the tar.gz file
https://wordpress.org/download/
- sudo tar -C /opt/lampp/htdocs/pcap -xvf wordpress-6.4.3.tar.gz 
  - NOTE 1: pcap is the folder that was previously created
- mv /opt/lampp/htdocs/pcap/wordpress/* /opt/lampp/htdocs/pcap
  - NOTE: You are moving newly extracted files on directly up
- sudo vi wp-config-sample.php 
  - NOTE 1: look for  // ** MySQL settings – You can get this info from your web host ** //
  - NOTE 2: annotate the following 
    - database_name_here # the database pcap we created
    - username_here # root for now
    - password_here # leave it blank
- http://<Vagrant-assigned-IP>/<name-of-db-which-is-pcap>
- During the installation, it will ask you to create a "wp-config" with the following content
- YOU ARE ALL SET!!!


REF:
Install WP locally (there is step I did not follow in this link)
https://wpengine.com/resources/wordpress-xampp/#Installing_WordPress_in_XAMPP_on_MAC_OS
