## Install Linux, Apache, MySQL, PHP (LAMP)

### Step 1 - Installing Apache

#### Uncomplicated Firewall (ufw) :

Uncomplicated Firewall is a program for managing a netfilter firewall designed to be easy to use. It uses a command-line
interface consisting of a small number of simple commands, and uses iptables for configuration. UFW is available by
default in all Ubuntu installations since 8.04 LTS.

- Check current status of (ufw):
    ```bash
  $ sudo ufw status
  ```
- Now open ports 22 (for SSH), 80 and 443 and enable Ubuntu Firewall (ufw):
    ```bash
    $ sudo ufw allow ssh
    $ sudo ufw allow 80
    $ sudo ufw allow 443
    $ sudo ufw enable
    ```
- To list all currently available UFW application profiles
    ```bash
    $ sudo ufw app list
    ```
- Install apache2
    ```bash
    $ sudo apt install apache2
    $ apache2 -v    [Check Apache version] 
    ```
- To only allow traffic on port 80, use the Apache profile:
    ```bash
    $ sudo ufw allow in "Apache"
    $ sudo ufw app info "Apache Full"
    ```
- Confirm that Apache is now running with the following command:
    ```bash
    $ sudo systemctl status apache2
    $ sudo systemctl start apache2   [If it’s not running, use systemctl to start it]
    $ sudo systemctl restart apache2 [Restart your Web server]
    $ sudo systemctl enable apache2  [It’s also a good idea to enable Apache to automatically start at system boot time]
    ```
  [localhost:80](localhost:80) Traffic on port 80 is now allowed through the firewall. You should see a page with an
  “Apache2 Ubuntu Default” header
  showing that Apache2 has been installed successfully.

### Step 2 - Installing MySQL

- install this software:
    ```bash
    $ sudo apt install mysql-server
    $ sudo service mysql status
    ```
  - check which authentication method each of your MySQL user accounts use with the following command:
    ```bash
    mysql> SELECT user,authentication_string,plugin,host FROM mysql.user;
    ```
  - Configuring Password Access for a Dedicated MySQL User:
    ```bash
    $ sudo mysql
    $ mysql -u <user> -p
    mysql> CREATE USER 'sammy'@'localhost' IDENTIFIED WITH caching_sha2_password BY 'password';
    mysql> ALTER USER 'sammy'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
    mysql> GRANT ALL PRIVILEGES ON *.* TO 'sammy'@'localhost' WITH GRANT OPTION;
    mysql> exit
    ```

### Step 3 - Installing PHP

- Installing and testing PHP 7.3<br>
  ```bash
  $ sudo apt install php libapache2-mod-php php-mysql
  $ php -v
  ```
  `software-properties-common` it provides some useful scripts for adding and removing PPA. Using a `Personal Package
  Archive (PPA)`, you can distribute software and updates directly to Ubuntu users. Create your source package, upload
  it
  and Launchpad will build binaries and then host them in your own apt repository.
    ```bash
    $ sudo apt install software-properties-common
    $ sudo add-apt-repository ppa:ondrej/php
    $ sudo apt update
    $ sudo apt install -y php7.3
    $ php -v
    $ php -S localhost:8000    [PHP Built-in WebServer]
    ```
- Installing PHP 7.3 Extensions
  ```bash
  $ sudo apt install php7.3-cli php7.3-fpm php7.3-json php7.3-pdo php7.3-mysql php7.3-zip php7.3-gd  php7.3-mbstring php7.3-curl php7.3-xml php7.3-bcmath php7.3-json
  ```
- completely remove any package with a name that starts with `php`
  ```bash
  $ sudo apt-get purge 'php*'
  ```

### Step 4 - Install phpMyAdmin

- Once you have your LAMP setup you can start by installing phpMyAdmin.
- below command to install phpMyAdmin:<br>
  Warning: When the prompt appears, “apache2” is highlighted, but not selected. If you do not hit SPACE to select
  Apache, the installer will not move the necessary files during installation. Hit SPACE, TAB, and then ENTER to select
  Apache.
    ```bash
    $ sudo apt install phpmyadmin php-mbstring php-zip php-gd php-json php-curl
    $ sudo phpenmod mbstring
    $ sudo systemctl restart apache2
    ```
  - To resolve this, select the abort option to stop the installation process.
    ```bash
    $ sudo mysql
    $ UNINSTALL COMPONENT "file://component_validate_password";
    $ INSTALL COMPONENT "file://component_validate_password";
    $ exit
    ```
  - Completely removing phpMyAdmin:
      ```bash
      $ sudo apt-get -f install
      $ sudo dpkg -P phpmyadmin  
      $ sudo rm -vf /etc/apache2/conf.d/phpmyadmin.conf
      $ sudo rm -vfR /usr/share/phpmyadmin
      $ sudo service apache2 restart
      ```