# JAVA-8

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

# SUBLIME

__REPOSITORY__
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install sublime-text-installer
```

# RUBY
```
sudo apt-get install ruby-full
```

# APACHE TOMCAT


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

# REDIS

```
sudo add-apt-repository ppa:chris-lea/redis-server
sudo apt-get update
sudo apt-get install redis-server
```


