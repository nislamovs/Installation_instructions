# Software installation instructions

### Summary:
1. [Disabling linux workstation automatic update](#1-disabling-linux-automatic-update)
2. [Default linux apps](#2-default-linux-apps)
3. [Firefox](#3-install-firefox-browser-and-plugins)
4. [Skype](#4-install-skype)
5. [Weather control](#5-weather-control)
6. [Storage on second hdd](#6-storage-on-second-hdd)
7. [Enable additional software repositories](#7-enable-additional-software-repositories)
8. [Install terminator](#8-terminator)
9. [Install java8](#9-install-java-8)
10. [Install maven3](#10-install-maven-3)
11. [Install google chrome](#11-install-google-chrome)
12. [Install MongoDB](#12-install-mongodb)
13. [Install power management utils](#13-install-power-management-utils)
14. [Install Postgresql database](#14-install-postgresql-database)
15. [Install grsync](#15-install-grsync)
16. [Install MySql database](#16-install-mysql-database)
17. [Install telegram](#17-install-telegram)
18. [Dropbox client](#18-dropbox-client)
19. [Install jenkins](#19-install-jenkins)
20. [Install TOR client](#20-install-tor-client)
21. [Install webmin](#21-install-webmin)
22. [Install inxy (system info)](#22-install-inxy-system-info)
23. [Install latex](#23-install-latex)
24. [Install nodejs and npm](#24-install-nodejs-and-npm)
25. [Install IntellijIdea](#25-install-intellijidea)
26. [Install Pinegrow](#26-install-pinegrow)
27. [Install JBoss](#27-install-jboss)
28. [Install gedit plugins](#28-install-gedit-plugins)
29. [Install JIRA](#29-install-jira)
30. [Install Confluence](#30-install-confluence)
31. [Install Bitbucket](#31-install-bitbucket)
32. [Install SoapUI](#32-install-soapui)
33. [Install Yarn](#33-install-yarn)
34. [Install Tomcat 8](#34-install-tomcat-8)
35. [Install Squirrel](#35-install-squirrel)
36. [Install MsSql](#36-install-mssql)
37. [Install Virtualbox](#37-install-virtualbox)
38. [Install Openldap](#38-install-openldap)
39. [Install Chrome](#39-install-chrome)
40. [Install Gradle](#40-install-gradle)
41. [Install Firefox ESR](#41-install-firefox-esr)
42. [Install gImageReader](#42-install-gimagereader)
43. [Install proFTPd](#43-install-proftpd)
44. [Install KiCad](#44-install-kicad)
45. [Install GNS3](#45-install-gns3)

----------
#### 1. Disabling linux automatic update

- Open file ```sudo vim /etc/apt/apt.conf.d/10periodic```
- Change ```APT::Periodic::Update-Package-Lists "1";``` to ```APT::Periodic::Update-Package-Lists "0";```

[Back](#summary)

----------
#### 2. Default linux apps

- Copy this to terminal
```
sudo apt-get install -y tree
sudo apt-get install -y git
sudo apt-get install -y vim
sudo apt-get install -y trash
sudo apt-get install -y htop
sudo apt-get install -y meld
sudo apt-get install -y gnumeric
sudo apt-get install -y tasksel
sudo apt-get install -y openssh-server
sudo apt-get install -y sshpass 
sudo apt-get install -y alien
sudo apt-get install -y filezilla
sudo apt-get install -y p7zip-full
sudo apt-get install -y aptitude
sudo apt-get install -y pandoc
sudo apt-get install -y ntp
sudo apt-get install -y tor
sudo apt-get install -y gmountiso
sudo apt-get install -y keepass2
sudo apt-get install -y hydra

sudo apt-get install -y sendmail
sudo sendmail config
```

[Back](#summary)

----------
#### 3. Install firefox browser and plugins

- Install firefox
- Install following plugins:
  - firessh
  - httprequester
  - pdfmage
  - JSONLite
  - text editor
  - simple youtube mp3 button
  - fireftp
  - youtube flash player

[Back](#summary)

----------
#### 4. Install skype

- Run the following commands from terminal:
  
```
sudo dpkg --add-architecture i386
sudo apt-get update
wget -O skype-install.deb http://www.skype.com/go/getskype-linux-deb
sudo dpkg -i skype-install.deb

sudo apt-get install -y skype 
```

[Back](#summary)

----------
#### 5. Install weather control

- Run the following commands from terminal:
  
```
sudo add-apt-repository ppa:atareao/atareao
sudo apt-get update
sudo apt-get install my-weather-indicator
```

Uses too much of system resources.

[Back](#summary)

----------
#### 6. Storage on second hdd

If necessary to create a partition use gparted: ```sudo apt-get install gparted``` 
During partition creation process select Device -> create partition table type -> gpt

- Create if not created:
    ```
    sudo mkdir /storage
	 sudo chmod a+w /storage
	```
- Run ```sudo vim /etc/fstab``` and add line :
	```/dev/sdb1                                 /storage        ext4    defaults          0       0```
- Then mount storage:
    ```
	 sudo mount /storage
	```
	
[Back](#summary)

----------
#### 7. Enable additional software repositories

- Open terminal and enter command: ```sudo vim /etc/apt/sources.list```

- Remove hash (#) for remote repository entries (lines which start with # deb http...) and save file.

- Update repo metadata, upgrade system, clean up packages and clean cached files with command in terminal:
    ```
    sudo apt-get update;
    sudo apt-get dist-upgrade;
    sudo apt-get autoremove;
    sudo apt-get clean
    ```
    press Enter to confirm operations

[Back](#summary)

----------
#### 8. Terminator

- Copy this to terminal
```
sudo apt-get install -y terminator
```

[Back](#summary)

----------
#### 9. Install java 8

- Copy this to terminal
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
sudo apt-get install oracle-java8-set-default
export _JAVA_OPTIONS=-Xmx1024M
```
- Test result with command: ```java -version```

----

- Newer versions of Linux:
```
sudo apt update
sudo apt install openjdk-8-jdk openjdk-8-jre
```

[Back](#summary)

----------
#### 10. Install maven 3

- If necessary uninstall maven2: ```sudo apt-get purge maven```

- Add this to /etc/apt/sources.list
```
deb http://ppa.launchpad.net/natecarlson/maven3/ubuntu precise main
deb-src http://ppa.launchpad.net/natecarlson/maven3/ubuntu precise main
```

- Then run command:
```
sudo apt-get update
sudo apt-get install maven3
sudo apt install maven
```

[Back](#summary)

----------
#### 11. Install google chrome

- Run the following commands from terminal:

```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list'
sudo apt-get update
sudo apt-get install google-chrome-stable
```

[Back](#summary)

----------
#### 12. Install mongodb

- Run the following commands from terminal:

```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6
echo "deb [ arch=amd64,arm64 ] http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list

sudo apt-get update
sudo apt-get install -y mongodb-org
```

[Back](#summary)

----------
#### 13. Install power management utils

- Run the following commands from terminal:

```
sudo apt-get install powermanagement-interface
sudo pm-suspend
sudo pm-hibernate
```

[Back](#summary)

----------
#### 14. Install postgresql database

Installation of postresql db server, client(pgAdmin) and creating of test db.

Additional info: 

https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-14-04

- Run the following commands from terminal:

```
sudo apt-get update
sudo apt-get install postgresql postgresql-contrib
sudo apt-get install pgadmin3
```
- Create test database:
```
sudo -i -u postgres
psql
CREATE DATABASE testdb;
CREATE TABLE playground (
    equip_id serial PRIMARY KEY,
    type varchar (50) NOT NULL,
    color varchar (25) NOT NULL,
    location varchar(25) check (location in ('north', 'south', 'west', 'east', 'northeast', 'southeast', 'southwest', 'northwest')),
    install_date date
);
#Show table
\d
#or
\dt
#exit
\q
#exit from user 
exit
```

[Back](#summary)

----------
#### 15. Install qrsync

Installation of qrsync (rsync with gui)

- Run the following commands from terminal:

```
sudo apt-get install grsync
```

[Back](#summary)

----------
#### 16. Install mysql database

Installation of mysql db server, db client, creating of test db.

Additional info: 

https://www.linode.com/docs/databases/mysql/install-mysql-on-ubuntu-14-04

- Check yout hostname:
```
hostname -f
```

- Run the following commands from terminal:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install mysql-server

pass : root
```

- Creating test db:

```
mysql -u root -p

create database testdb;
create user 'yourname'@'localhost' identified by '81126f0afcf5a95115f397567f1066d1';
grant all on testdb.* to 'yourname';
use testdb;
create table customers (customer_id INT NOT NULL AUTO_INCREMENT PRIMARY KEY, first_name TEXT,last_name TEXT);
```

- Restart service:

```
sudo service mysql stop
sudo dpkg-reconfigure mysql-server-5.5
sudo service mysql start
```

- Additional setup:

To make connections for external servers to db, run: 

```
sudo vim /etc/mysql/my.cnf
```
Change line:
```bind-address = 127.0.0.1```
to :
```bind-address = 0.0.0.0```

- Installation of Mysql Workbench

```sudo apt-get install mysql-workbench```

For ubuntu 16.04 download deb file from mysql site.

- Mysql performance tuner setup:

```
sudo apt-get install mysqltuner
```

[Back](#summary)

----------
#### 17. Install telegram

Installation of telegram

- Run the following commands from terminal:

```
sudo add-apt-repository ppa:atareao/telegram
sudo apt-get update
sudo apt-get install telegram
sudo apt-get install orville-write
```

[Back](#summary)

----------
#### 18. Dropbox client

- Copy this to terminal
```
mkdir -p ~/bin
wget -O ~/bin/dropbox.py "https://www.dropbox.com/download?dl=packages/dropbox.py"
chmod +x ~/bin/dropbox.py

sudo apt install nautilus-dropbox
dropbox start -i

~/bin/dropbox.py start
```
Additional info
http://www.dropboxwiki.com/tips-and-tricks/using-the-official-dropbox-command-line-interface-cli

[Back](#summary)

----------
#### 19. Install jenkins

- Copy this to terminal
```
wget -q -O - http://pkg.jenkins-ci.org/debian/jenkins-ci.org.key | sudo apt-key add -
sudo su
echo "deb http://pkg.jenkins-ci.org/debian binary/" >> /etc/apt/sources.list
apt-get update
apt-get install jenkins
```
- To change default port:
As root open file : ```/etc/default/jenkins``` and change line : ```HTTP_PORT=8081```

- Admin account setup:
  - Username:	username  
  - Password:	passwd
  - Full name:	Nizami Islamovs
  - E-mail address:	nizamiislamovs@gmail.com
  
- Catlight installation

Download deb file from ```https://catlight.io/downloads``` and launch

If necessary:
```
sudo apt install gdebi
wget http://launchpadlibrarian.net/201330288/libicu52_52.1-8_amd64.deb
sudo gdebi libicu*.deb;
```

- Update Jenkins

   - Download the new version (2.107 at the moment of writing this post). From ```/home/user/backup/``` execute: ```wget http://updates.jenkins-ci.org/download/war/2.107/jenkins.war``` 
   - Backup the old version (Jenkins war is installed in ```/usr/share/jenkins```):
     ```sudo cp /usr/share/jenkins/jenkins.war /home/user/backup/jenkins-2.8.war```
   - Overwrite the old jenkins.war: ```sudo cp /home/user/backup/jenkins.war /usr/share/jenkins/jenkins.war``` 
   - Restart jenkins : ```sudo service jenkins restart```
   
- Work from console

   First download jenkins-cli.jar from jenkins web-interface
   
   - Authentication
   ```
   java -jar jenkins-cli.jar -s http://Box15:8081/ who-am-i --username nizami --password qwerty1234
   ```
   - Launching the command (help)
   ```
   java -jar jenkins-cli.jar -s http://Box15:8081/ -auth nizami:qwerty1234 help
   ```
   - getting list of jobs
   ```
   java -jar jenkins-cli.jar -s http://Box15:8081/ -auth nizami:qwerty1234 list-jobs
   ```
   - Importing job
   ```
   java -jar jenkins-cli.jar -s http://Box15:8081/ -auth nizami:qwerty1234 create-job newmyjob < job1.xml
   ```
   - Exporting job
   ```
   java -jar jenkins-cli.jar -s http://Box15:8081/ -auth nizami:qwerty1234 get-job Deployment\ to\ Box15 > job1.xml
   ```
   - Launching job with param (s1)
   ```
   java -jar jenkins-cli.jar -s http://box15:8081/ -auth nizami:qwerty1234 build JobWithParams -v -s -p s1=pizdec
   ``` 
   
[Back](#summary)

----------
#### 20. Install TOR client

Visit this page :
```https://www.torproject.org/docs/debian.html.en```

- You need to add the following entry in ```/etc/apt/sources.list``` or a new file in ```/etc/apt/sources.list.d/```:
    ```
    deb http://deb.torproject.org/torproject.org trusty main
    deb-src http://deb.torproject.org/torproject.org trusty main
    ```
- Then add the gpg key used to sign the packages by running the following commands at your command prompt:
    ```
    gpg --keyserver keys.gnupg.net --recv A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89
    gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
    ```
- You can install it with the following commands:
    ```
    sudo apt-get update
    sudo apt-get install tor deb.torproject.org-keyring
    ```

Additionally:
```sudo apt-get install libevent-dev```

[Back](#summary)
#### 21. Install webmin

- Add new repo ```deb http://download.webmin.com/download/repository sarge contrib``` to sources list ```sudo vim /etc/apt/sources.list```:

- Copy this to terminal
    ```
    wget -q -O - http://www.webmin.com/jcameron-key.asc | sudo apt-key add -
    sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libdigest-md5-perl
    sudo apt-get update
    sudo apt-get install webmin
    ```

[Back](#summary)

----------
#### 22. Install inxy (system info)

- Copy this to terminal
    ```
    sudo apt-get install inxi
    ```

[Back](#summary)

----------
#### 23. Install latex

- Copy this to terminal
    ```
    sudo apt-get install texlive texlive-full
    sudo apt-get install imagemagick
    sudo apt-get install gedit-latex-plugin
    sudo apt-get install gummi
    sudo apt-get install texmaker
    ```

[Back](#summary)

----------
#### 24. Install nodejs and npm

- Copy this to terminal
    ```
    sudo apt-get update
    sudo apt-get install nodejs
    sudo apt-get install npm
    sudo apt-get install build-essential libssl-dev
    mkdir -p ~/Desktop/nvm; cd $_
    curl -sL https://raw.githubusercontent.com/creationix/nvm/v0.31.0/install.sh -o install_nvm.sh
    chmod a+x install_nvm.sh
    source ~/.profile
    ```
- Then run this command : (For ubuntu 16.04)
    ```
    curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
    sudo apt-get install -y nodejs
    ```
    
Info from here:
```https://askubuntu.com/questions/426750/how-can-i-update-my-nodejs-to-the-latest-version```
    
[Back](#summary)

----------
#### 25. Install IntellijIdea

- Download IntellijIDEA archive (tar.gz) from Jetbrains site
- Unpack it
- Append new path to path variable: ```PATH=$PATH:/tmp/mozilla_yourname0/idea-IU-171.4424.56/bin```
- Install plugins
    
[Back](#summary)

----------
#### 26. Install Pinegrow

- Copy this to terminal
```
cd ~/Downloads;
wget http://pinegrow.s3.amazonaws.com/PinegrowLinux64.2.951.zip

sudo unzip PinegrowLinux64.2.51.zip -d /opt/pinegrow
sudo ln -s /opt/pinegrow/Pinegrow\ Web\ Designer /usr/local/bin/pinegrow  
pinegrow 
```
    
[Back](#summary)

----------
#### 27. Install JBoss

- Additional info could be found here:
```
http://findnerd.com/list/view/How-To-Install-JBoss-On-Ubuntu/2987/
https://www.digitalocean.com/community/tutorials/how-to-install-jboss-on-ubuntu-12-10-64bit
```

- Copy this to terminal
```
cd ~/Desktop/; mkdir jboss; cd jboss;
wget http://download.jboss.org/jbossas/7.1/jboss-as-7.1.1.Final/jboss-as-7.1.1.Final.tar.gz
tar xfvz jboss-as-7.1.1.Final.tar.gz
mv jboss-as-7.1.1.Final /usr/local/share/jboss
adduser appserver
chown -R appserver /usr/local/share/jboss
su appserver
cd /usr/local/share/jboss/bin	
./add-user.sh
```
    
pass : appuser
```
What type of user do you wish to add? 
 a) Management User (mgmt-users.properties) 
 b) Application User (application-users.properties)
(a): a

Enter the details of the new user to add.
Realm (ManagementRealm) :    
Username : app1
Password : 
Re-enter Password :
```
pass : appuser

- Then launch:
```
./standalone.sh -Djboss.bind.address=yourserverip -Djboss.bind.address.management=yourserverip&
```
or
```
./standalone.sh -Djboss.bind.address=0.0.0.0 -Djboss.bind.address.management=0.0.0.0&
```
- Console
```http://yourserverip:9990/console``` or ```http://yourserverip:8080/``` 

[Back](#summary)

----------
#### 28. Install gedit plugins

- Copy this to terminal
    ```
    mkdir geditplugin; cd $_
    wget http://tapioca-voip.sourceforge.net/regexsearch_gedit_plugin.tar.gz
    tar xzvf regexsearch_gedit_plugin.tar.gz
    sudo su -
    cd /usr/lib/gedit/plugins
    cp -rf /home/student/Desktop/regexsearch* .
    ```

[Back](#summary)

----------
#### 29. Install JIRA

- Download binary from the site

- Copy this to terminal

    ```
    rsync -azP /home/yourname/Downloads/atlassian-jira-software-7.3.0-x64.bin yourname@box14:/home/yourname/Downloads/temp
    chmod a+x atlassian-jira-software-X.X.X-x64.bin
    sudo ./atlassian-jira-software-X.X.X-x64.bin
    ```
    
- Set data during installation:

    ```
    Where should JIRA Software be installed?
    [/opt/atlassian/jira]
    
    Default location for JIRA Software data
    [/var/atlassian/application-data/jira]
    
    HTTP: 9090, Control: 9005
    ```
    
- Create user in database:

    ```
    sudo -i -u postgres
    psql
    CREATE USER jiradbuser WITH password '99336d87ce79e2';
    CREATE DATABASE jiradb WITH ENCODING 'UNICODE' LC_COLLATE 'C' LC_CTYPE 'C' TEMPLATE template0;
    GRANT ALL privileges ON DATABASE jiradb TO jiradbuser;
    ```
        
- Make changes in configuration files:
    - In file ```/etc/postgresql/9.2/main/postgresql.conf``` find string ```#listen_addresses = 'localhost'``` and change to ```listen_addresses = '*'```
    - In file ```/etc/postgresql/9.2/main/pg_hba.conf``` find and modify string ```host    all    all    192.168.0.1/16    md5```
    
- Restart service:
    ```
    sudo service postgresql restart
    ```
    
- Additional db setup:
    ```
    #psql --host=localhost --port=5432 --username=jiradbuser --password --dbname=jiradb
    #SELECT pg_terminate_backend(pg_stat_activity.pid) FROM pg_stat_activity WHERE pg_stat_activity.datname = 'jiradb' AND pid <> pg_backend_pid();
    ```
    
[Back](#summary)

----------
#### 30. Install Confluence


- Download binary from the site

- Copy this to terminal

    ```
    rsync -azP /home/yourname/Downloads//home/yourname/Downloads/atlassian-confluence-6.0.3-x64.bin yourname@box14:/home/yourname/Downloads/temp
    chmod a+x /home/yourname/Downloads/atlassian-confluence-6.0.3-x64.bin
    sudo ./atlassian-confluence-6.0.3-x64.bin
    ```
    
- Set data during installation:

    ```
    Where should Confluence 6.0.3 be installed?
    [/opt/atlassian/confluence]
    
    Default location for Confluence data
    [/var/atlassian/application-data/confluence]
    
    HTTP Port Number : 9080
    Control Port Number : 9000
    ```
    
- Create user in database:

    ```
    sudo -i -u postgres
    psql
    CREATE USER confluencedbuser WITH password 'e12876989fcb9d52';
    CREATE DATABASE confluence WITH ENCODING 'UTF8';
    GRANT ALL privileges ON DATABASE confluence TO confluencedbuser;
    ```

[Back](#summary)

----------
#### 31. Install Bitbucket

- Download binary from the site

- Copy this to terminal

    ```
    rsync -azP /home/yourname/Downloads/atlassian-bitbucket-4.4.1-x64.bin yourname@box14:/home/yourname/Downloads/temp
    chmod a+x atlassian-bitbucket-4.4.1-x64.bin
    sudo ./atlassian-bitbucket-4.4.1-x64.bin
    
    cd /storage/
    mkdir -p atlassian/application-data/bitbucket
    ```
    
- Set data during installation:

    ```
    Where should Bitbucket be installed?
    [/opt/atlassian/bitbucket/4.4.1]
    
    The location for Bitbucket data.
    This will be the default location for repositories, plugins, and other data.
    Ensure that this location is not used by another Bitbucket installation.
    [/var/atlassian/application-data/bitbucket]
    /storage/atlassian/application-data/bitbucket
    
    HTTP Port Number    : 7990
    Control Port Number : 8006
    ```
    
- Create user in database:

    ```
    sudo -i -u postgres
    psql
    CREATE ROLE bitbucketuser WITH LOGIN PASSWORD 'a65f42172e78a2c1cd' VALID UNTIL 'infinity';
    CREATE DATABASE bitbucket WITH ENCODING='UTF8' OWNER=bitbucketuser CONNECTION LIMIT=-1;
    GRANT ALL privileges ON DATABASE bitbucket TO bitbucketuser;
    ```

[Back](#summary)

----------
#### 32. Install SoapUI

Java must be preinstalled

- Copy this to terminal
    ```
    cd ~/Desktop;
    mkdir soapui
    cd $_
    wget http://cdn01.downloads.smartbear.com/soapui/5.3.0/SoapUI-5.3.0-linux-bin.tar.gz
    sudo tar -xzf SoapUI-5.3.0-linux-bin.tar.gz  -C /opt/
    cd /opt/SoapUI-5.3.0/bin/
    ./soapui.sh
    ```

[Back](#summary)

----------
#### 33. Install Yarn

- Copy this to terminal
    ```
    curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
    echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
    sudo apt-get update && sudo apt-get install yarn
    ```

[Back](#summary)

----------
#### 34. Install Tomcat 8

- Copy this to terminal
    ```
    sudo apt-get install tomcat8 tomcat8-docs tomcat8-admin tomcat8-examples
    ```
- In file : ```tomcat-users.xml``` add user roles:

    ```
    sudo vim /etc/tomcat8/tomcat-users.xml
    ```
    Add this:
    ```
    <tomcat-users>
        <user username="admin" password="password" roles="manager-gui,admin-gui"/>
        <user username="adm" password="passwd" roles="manager-script"/>
    </tomcat-users>
    ```
- Restart Tomcat:

    ```
    sudo service tomcat8 restart
    ```
    
[Back](#summary)

----------
#### 35. Install Squirrel

- Download jar file from : ```http://www.squirrelsql.org```
- Launch it : ```java -jar squirrel-sql-3.3.0-install.jar```
- Install drivers for databases

[Back](#summary)

----------
#### 36. Install MsSql

- Copy this to terminal
```
sudo su
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server.list > /etc/apt/sources.list.d/mssql-server.list
sudo apt-get update
apt-cache search mssql-server
sudo apt-get install mssql-server
```

[Back](#summary)

----------
#### 37. Install Virtualbox

- Copy this to terminal
```
sudo apt-get install linux-headers-generic build-essential dkms
sudo apt-get remove --purge -y virtualbox-dkms
sudo apt-get install -y virtualbox-dkms
sudo aptitude install virtualbox-guest-x11
```

- Additional info:
```
https://askubuntu.com/questions/920689/how-to-issue-modprobe-vboxdrv-error-in-virtualbox
https://blogs.oracle.com/oswald/entry/importing_a_vdi_in_virtualbox
```

[Back](#summary)

----------
#### 38. Install Openldap

- Copy this to terminal
```
sudo apt-get install slapd
```
pass : root
```
sudo apt-get install ldap-utils
sudo /etc/init.d/slapd restart
```

[Back](#summary)

----------
#### 39. Install chrome

- Installation

Info from here : ```http://askubuntu.com/questions/510056/how-to-install-google-chrome```

```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add - 
sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list'
sudo apt-get update 
sudo apt-get install google-chrome-stable
```

- Update
```
sudo apt-get --only-upgrade install google-chrome-stable
```

[Back](#summary)

----------
#### 40. Install gradle

Java must be preinstalled.

- Installation

```
sudo apt-get install gradle
```

- Update
```
sudo add-apt-repository ppa:cwchien/gradle
sudo apt-get update
sudo apt upgrade gradle
```

[Back](#summary)

----------
#### 41. Install firefox esr

Necessary for selenium to work

- Installation

```
sudo add-apt-repository ppa:jonathonf/firefox-esr
sudo apt-get update
sudo apt-get install firefox-esr
```

[Back](#summary)

----------
#### 42. Install gImageReader

OCR for linux

- Installation

```
sudo apt-get install gImageReader
```

[Back](#summary)

----------
#### 43. Install proFTPd

- Installation

```
sudo apt-get install proftpd
```
type: stand alone

In file ```/etc/proftpd/proftpd.conf``` find and modify string: ```PassivePorts                  6100 70000```

[Back](#summary)

----------
#### 44. Install KiCad

- Installation

```
sudo add-apt-repository --yes ppa:js-reynaud/kicad-5
sudo apt update
sudo apt install kicad --install-recommends kicad
# If you want demo projects
sudo apt install kicad-demos
```

- Additional info:

`https://kicad-pcb.org/download/ubuntu/`

[Back](#summary)

----------

#### 45. Install GNS3

- Installation

```
sudo add-apt-repository ppa:gns3/ppa
sudo apt-get update
sudo apt-get install gns3-gui
```

[Back](#summary)

----------
