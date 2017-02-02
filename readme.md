



# Questions


#### 1.What java version is installed?

*java -version*

#### 2.How was it installed and configured?
Download two version of java archive, unpack it into /opt/oracle/java 

#### 3.Where are log files of tomcat and httpd?
 *Httpd logs* - /var/log/httpd  
 *Tomcat logs* at the same folder as other tomcat's files.  

#### 4.Where is JAVA_HOME and what is it?
JAVA_HOME is just a variable to find path where Java is installed.
#### 5.Where is tomcat installed?
*echo $CATALINA_HOME*
#### 6.What is CATALINA_HOME?
This variable shows us the way of tomcat's home directory.
#### 7.What users run httpd and tomcat processes? How is it configured?
Httpd is started by root because it needs to use port 80, as we know ports between 0 and 1024 can be used only by root
Tomcat hasn't such need and we run it by user "tomcat".
#### 8.What configuration files are used to make components work with each other?
Here we use mod_jk to connect **httpd** with **Tomcat** under  AJP protocol.
#### 9.What does it mean: “load average: 1.18, 0.95, 0.83”?
* 0.00 means there's no traffic on the bridge at all  
* 1.00 means the bridge is exactly at capacity  
* over 1.00 means there's overflow  
In our case traffik was increased during last 15 minutes
---  
|   	|   	|   	|   	|   	|
|---	|---	|---	|---	|---	|
|   	|   	|   	|   	|   	|
|   	|   	|   	|   	|   	|
|   	|   	|   	|   	|   	|  
