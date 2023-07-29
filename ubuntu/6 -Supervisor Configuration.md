## Supervisor: A Process Control System
[Supervisor](http://supervisord.org) is a client/server system that allows its users to monitor and control a number of processes on UNIX-like operating systems.
we will discuss how to configure it in the following documentation.<br>
For more information on Supervisor, consult the [Supervisor documentation](http://supervisord.org).<br>
For more information on Laravel Supervisor, consult the [Laravel Supervisor documentation](https://laravel.com/docs/10.x/queues#supervisor-configuration).



- We will install supervisor by running the command below in our terminal:
    ```bash
   sudo apt-get install supervisor
    ```
- Navigate to supervisor config directory:
    ```bash
   cd /etc/supervisor/conf.d
    ```
- Create a new supervisor configuration file for Laravel:
    ```bash
   sudo nano laravel-worker.conf
    ```
- Paste the following contents into the newly created file:
    ```bash
   [program:laravel-worker]
    process_name=%(program_name)s_%(process_num)02d
    command=php /home/forge/app.com/artisan queue:work --sleep=3 --tries=3 --max-time=3600
    autostart=true
    autorestart=true
    stopasgroup=true
    killasgroup=true
    user=forge
    numprocs=8
    redirect_stderr=true
    stdout_logfile=/home/forge/app.com/worker.log
    stopwaitsecs=3600
    ```
- Once the configuration file has been created, you may update the Supervisor configuration and start the processes using the following commands:
  ```bash
   sudo supervisorctl reread

   sudo supervisorctl update

   sudo supervisorctl start laravel-worker:*
    ```
### Supervisor Actions
  ```bash
   #Print a list of available actions
   $ sudo supervisorctl help

   #Reload config and add/remove as necessary, and will restart affected programs
   $ sudo supervisorctl update

   #Start all processes in a group
   $ sudo supervisorctl start laravel-worker:*
   
   #Get all process status info.
   $ sudo supervisorctl status
   
   #Stop all processes in a group
   $ sudo supervisorctl stop laravel-worker:*
   ```