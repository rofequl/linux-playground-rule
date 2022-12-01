## Linux tool setup

### Step 1 - Install Git on your Ubuntu system:

- Install Git on Ubuntu
  ```bash
  $ sudo apt install git
  $ git --version
  ```
- Setting Up Git:
  ```bash
  $ git config --global user.name "Your Name"
  $ git config --global user.email "youremail@domain.com"
  $ git config --list
  ```
- Setting Up Github account:
  ```bash
  $ sudo apt install gh
  $ gh auth login
  ```

### Step 2 - Code editor and IDE setup:

- PhpStorm: [www.jetbrains.com/phpstorm/download](https://www.jetbrains.com/phpstorm/download/#section=linux)

### Step 3 - Composer setup:

- To quickly install Composer in the current directory, run the following script in your terminal. To automate the
  installation, use the guide on installing Composer programmatically.
    ```bash
    $ php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
    $ php -r "if (hash_file('sha384', 'composer-setup.php') === '55ce33d7678c5a611085589f1f3ddf8b3c52d662cd01d4ba75c0ee0459970c2200a51f492d557530c71c15d8dba01eae') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
    $ php composer-setup.php
    $ php -r "unlink('composer-setup.php');"
    $ sudo mv composer.phar /usr/local/bin/composer
    ```

### Step 4 - unzip a zip file from the Terminal:

   ```bash
    $ sudo apt-get install unzip
    $ unzip <zip file name> -d <destination folder>
    $ unzip <zip file name>
   ```

### Step 5 - Installing MySQL Workbench

- Start by navigating to [MySQL APT Repository](https://dev.mysql.com/downloads/repo/apt/) download page and click
  Download to save the deb package on your Ubuntu system.
- add the official MySQL repository to the apt source list by running the command:
  ```bash
    $ cd Downloads
    $ ls
    $ sudo apt install ./mysql-apt-config_0.8.22-1_all.deb
   ```
- A pop-up window appears asking which MySQL product to install. As the required product is preselected, scroll down to
  Ok and hit Enter to continue installing.
- Install MySQL Workbench by running:
  ```bash
    $ sudo apt update
    $ sudo apt install mysql-workbench-community
    $ mysql-workbench
   ```