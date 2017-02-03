



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
* 0.00 means there's no traffic on the proc at all  
* 1.00 means the proc is exactly at capacity  
* over 1.00 means there's overflow  
In our case traffik on system was increased during last 15 minutes  

***  
###Report table

|  	| Issue | How to find 	|Time to find 	|   How to fix	|  Time to fix 	|
|----------	|:-------------:	|------:	|---	|---	|---	|
| 1	| Site isn't working |Try to enter the site 	| 1 min 	|   watch IPTABLE rules 	|  5 min  	|
| 2	|  Site with 503 error	| Try command curl -sL -w "%{http_code}" $url -o /dev/null	|  2 min 	| Look into httpd.conf and delete Rewrite |   5 min	|
| 3 | Tomcat is not started	|Try to get tomcat under 8080 port | 2 min	| Change owner of *logs* dir 	|  3 min 	|
| 4 |  Httpd isn't give right page 	|curl localhost	| 2 min	| Correct workers and vhost.conf  |  7 min 	|
| 5 |   Java isn't work	| tomcat is not working correctly  	|  1 min 	| update-alternatives java and choose correct dir	| 5 min|
| 6 |  tomcat isn't start after reboot 	|  Reboot system 	| 5 min  	| Run command chkconfig tomcat on and correct /etc/init.d/tomcat file  	|  5 min 	|
| 7 |    Can't read httpd logs 	|  Try to read logs  	| 1 min  	| chmod -R 755 /etc/log/httpd  	|  2 min 	|

