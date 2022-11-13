## Simple linux command

- Linux environment is up to date with the latest updates:

    ```bash
  $ sudo apt update
  $ sudo apt upgrade
  ```

- If you feel bored to give password repeatedly: ``sudo su``
- To create the folder: ``mkdir <folder name>``
- To create the file: `` touch <file name>``
- To go to the root directory: `` cd /``
  - To go to the home directory: `` cd``
  - To go to the previous directory: `` cd ..``


- To view all files and folders from the current directory: `` ls``
  - To print the detailed information of the files/directories: `` ls -al``
  - To print subdirectories of a directory: `` ls -R``
  - Get the hidden files: `` ls -a``
  

- To view all folders from the current directory: `` dir``
- To clean the terminal: `` clear``
- Present working directory in which I am operating: ``pwd``
- Show the content of any file: ``cat <file name>``
- Save the content of multiples files to one file: ``cat file1.txt file2.txt > output.txt``
- Remove the specific file from a directory: ``rm <file name>``
- Remove the empty directory: ``rmdir <folder name>``
- Wget command to download the content from the internet: ``wget <url>``
- The list of commands executed: ``history``
- Install or remove packages: 
  ```bash
    $ sudo apt install [packagename]
    $ sudo apt remove [packagename]
    ```
- Display the user details that are currently logged into the system: ``w``
- Move directory in Linux: ``mv source dest``
- Regular user to be able to modify files in these directories: ``sudo chown -R $USER:$USER /var/www/nayem/``
  
## Set Up Browser
### Brave
```bash
$ sudo apt install apt-transport-https curl
$ sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg
$ echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main"|sudo tee /etc/apt/sources.list.d/brave-browser-release.list
$ sudo apt update
$ sudo apt install brave-browser
```
### Chrome
[https://www.google.com/chrome/](https://www.google.com/chrome/)

## Set Up GitHub SSH
[Any help needed?](https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/GitHub-SSH-Key-Setup-Config-Ubuntu-Linux)
```bash
$ cd ~/.ssh
$ ssh-keygen -o -t rsa -C "email@example.com"
$ cat id_rsa.pub
```

## Getting Started with Vim Editor in Linux

- To install vim ubuntu run the command:
  ```bash
  $ sudo apt-get install vim
  ```
- To open a file in vim editor just write the file name after the vim command:``vim filename.txt``
- Write into file: ``i``
- Save and Exit: ``:wq!``
- Exit without saving the file: ``q!``
- You can see this tutorial by command vimtutor into the terminal: ``vimtutor``