## Laravel command and helper
- Cloning laravel project from github
  ```bash
  $ git clone <my-cool-project>
  $ composer install
  $ cp .env.example .env
  $ php artisan key:generate
  $ php artisan migrate
  $ php artisan serve
  ```
- Setup a virtual host for a Laravel project
  - First, copy the default configuration file and rename it:
    ```bash
    $ sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/your_domain_1.conf
    ```
  - open your_domain_1.conf file and Add the directives:
    ```bash
    ServerAdmin webmaster@localhost
    serverName www.myAwesomeLink.com
    DocumentRoot /var/www/html/laravel-app/public
  
    <Directory /var/www/html/laravel-app>
          AllowOverride All
    </Directory>
    ```
  - Now add an entry in the hosts file:
    ```bash
    127.0.0.1   www.myAwesomeLink.com
    ```
  - Enable site and the rewrite mode:
    ```bash
    $ sudo a2enmod rewrite
    $ sudo a2ensite myVhost.conf
    ```
  - Restart the server:
    ```bash
    $ sudo service apache2 restart
    ```