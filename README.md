# Ubuntu_15.10_setup
Setup Instructions to load java, ruby, rails, redis, mongo, node, tomcat and eclipse on ubuntu 15.10 

# JAVA-8


[webupd8-team](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html)


__REPOSITORY__
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```
__JAVA-HOME-PATH__

```
sudo update-alternatives --config java
```

___eg:  /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java___
Choose the part before /jre/bin/java

```
pico /etc/environment
```
add the lines 

```
JAVA_HOME="/usr/lib/jvm/java-6-openjdk-amd64"
```

then source from /etc/environment
```
source /etc/environment
```

---

# SUBLIME


[webupd8-team](http://www.webupd8.org/2013/07/sublime-text-3-ubuntu-ppa-now-available.html)


__REPOSITORY__
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install sublime-text-installer
```

---

# RUBY

[official ruby-lang page](https://www.ruby-lang.org/en/documentation/installation/)

```
sudo apt-get install ruby-full
gem install bundler
```

---


# APACHE TOMCAT

[Liquid-Web](http://www.liquidweb.com/kb/how-to-install-apache-tomcat-7-on-ubuntu-14-04/)

```
cd $HOME/Downloads
wget http://mirror.cc.columbia.edu/pub/software/apache/tomcat/tomcat-7/v7.0.54/bin/apache-tomcat-7.0.54.tar.gz
tar xvzf apache-tomcat-7.0.54.tar.gz
mkdir /opt/tomcat
mv ./apache-tomcat-whatever /opt/tomcat
pico /etc/environment
CATALINA_HOME="/opt/tomcat"
chmod -R 777 /opt/tomcat
```
test if it works by doing:

```
cd /opt/tomcat/apache-tomcat-whatever/bin/startup.sh
```

it should say tomcat started
go to browser and check if 
localhost:8080 produces tomcat working page.

---


# REDIS


[DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-configure-a-redis-cluster-on-ubuntu-14-04)


```
sudo add-apt-repository ppa:chris-lea/redis-server
sudo apt-get update
sudo apt-get install redis-server
```
---

# NODE-JS


[How to Install Node.js on Ubuntu 14.04](http://www.hostingadvice.com/how-to/install-nodejs-ubuntu-14-04/#ubuntu-package-manager)


```
sudo apt-get install nodejs
sudo apt-get install npm
sudo ln -s /usr/bin/nodejs /usr/bin/node
```

---

# MONGODB
[blog - guide](https://rohan-paul.github.io/mongodb_in_ubuntu/2015/09/03/How_to_Install_MongoDB_Iin_Ubuntu-15.04.html)

======

Step-A

From Ubuntu’s official package page install the mongodb version 2.6.10 (at this point, this is the latest MongoDB version for which Ubuntu 15.10 (wily) has an official Mongodb package) through Software Center.

Post installation, check the version number with mongod --version

Step-B

Create a systemd startup file in - /lib/systemd/system/mongodb.service with the following content -

```
[Unit]
Description=High-performance, schema-free document-oriented database
Documentation=man:mongod(1)
After=network.target

[Service]
Type=forking
User=mongodb
Group=mongodb
RuntimeDirectory=mongod
PIDFile=/var/run/mongod/mongod.pid
ExecStart=/usr/bin/mongod -f /etc/mongod.conf --pidfilepath /var/run/mongod/mongod.pid --fork
TimeoutStopSec=5
KillMode=mixed

[Install]
WantedBy=multi-user.target
```


Now enable this mongodb.service file and start it with the following command

sudo systemctl enable mongodb.service

Step-C

Create a folder /data/db in your machine; i.e. run sudo mkdir -p /data/db

And then take ownership of the /data/db directory by running - sudo chown -R mongodb /data/db

Now open the mongodb configuration file with sudo gedit /etc/mongod.conf and change the “dbpath” line as below

Replace dbpath: /var/lib/mongodb TO dbpath: /data/db and then save the file.

Step-D

Now running sudo service mongodb start should start mongodb normally.

To check if mongodb started by open the log file at /var/log/mongodb/mongodb.log. The log file’s last line should show something like :-

“[initandlisten] waiting for connections on port 27017”



======


---

# Eclipse

###Download Mars1
[Link](http://www.eclipse.org/downloads/packages/eclipse-ide-java-ee-developers/mars1)



###Install


Double click the archive -> extract it -> open it -> lock to launcher to automatically build the shortcut



###Basic


Import existing projects as General projects - not maven.
build path may reference an older jre - this will throw a build path error.
To fix it go to __build path -> Libraries -> Add Library__ 
The __oracle-java-8__ defined above should already be checked
__Click Finish -> Apply__


### Setting up Tomcat + Eclipse
Servers Tab -> New Server -> Apache Tomcat - 7 -> choose /opt/tomcat/apache-tomcat-7 -> finish


---





