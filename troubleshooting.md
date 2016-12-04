# Troubleshooting Your Installation

![](http://write.flossmanuals.net/openmrs/troubleshooting/static/troubleshooting.png)

Unfortunately, sometimes things do not go exactly planned. This chapter can help you deal with the most common problems.

We recommend using Apache Tomcat 6.0.29 to run OpenMRS. Any J2EE-compliant Java servlet container should be able to run it, but most people who use OpenMRS are running it with Tomcat, which may make it easier to get support if you encounter problems.

If you are not yet using Tomcat 6.0.29, consider upgrading Tomcat before you continue. We recommend getting Tomcat from this link.

[http://tomcat.apache.org/](http://tomcat.apache.org/)

When troubleshooting Tomcat, your first step should always be to review the Tomcat logs. In Windows, these are stored at the following location.

> C:\Program Files\Apache Software Foundation\Tomcat 6.0\logs

Historically, MySQL has been recommended as the database of choice to use with OpenMRS. The newer database from the open source project MariaDB should also be compatible with OpenMRS. Work is underway in the OpenMRS community to provide support for other databases such as Oracle, Microsoft SQL Server, and others, but these databases are not yet supported.

You may not be able to resolve your problem with OpenMRS using the troubleshooting material in this chapter. That is OK -- the OpenMRS community is available to help! Check out the [Getting Help from the OpenMRS Community](/getting-help-from-the-openmrs-community.md) chapter for more information about how to communicate with others, ask questions, and get answers.

## Some possible problems and solutions

### OpenMRS fails to install with message "Error creating bean with name 'messageSourceServiceTarget'"

MySQL must be running before starting and installing OpenMRS. If it is not, you may see the following error message in your web browser and log files when you attempt to install OpenMRS:

```
org.springframework.beans.factory.BeanCreationException:Error creating bean with name 'messageSourceServiceTarget' defined in class path resource applicationContext-service.xml
```

Ensure MySQL is installed and running before attempting to start and install OpenMRS. 

### MySQL Configure Instance hangs on starting the service, or reports Error 1045

On Windows, the computer may stop responding while running the MySQL Configure Instance tool. Most commonly, this occurs before the tool marks **Starting the service** as complete, because there is already a MySQL service running. 

To fix this, you should delete the pre-existing MySQL service in Windows, and try the installation again. You can find instructions on how to do delete a MySQL service at this link.

[http://www.howtogeek.com/howto/windows-vista/how-to-delete-a-windows-service-in-vista-or-xp/](http://www.howtogeek.com/howto/windows-vista/how-to-delete-a-windows-service-in-vista-or-xp/)

Alternatively, you may see a MySQL Error 1045, if your computer has previously had a MySQL instance installed. This means that the root password is incorrect, and is most commonly caused by residual data from the previous installation.

To fix this, you should delete the MySQL data directory. On Windows 7, you may need to reboot and delete the directory, or to use an unlocking program in order to delete this directory.

You can also change the password that OpenMRS uses to access your MySQL database, by editing the **openmrs-runtime.properties** file, as described later in this chapter.

### Starting Tomcat service on Windows fails

If you cannot start the Tomcat service on Windows, try checking the Tomcat logs. You can find the logs in the following directory.

> &lt;TOMCAT HOME&gt;\logs

### Errors like "Failed creating java C:\Program Files\Java\jre1.6.0\bin\client\jvm.dll"

To fix this problem, search for **msvcr71.dll** on your hard drive, and copy that file to this location.

> C:\Windows\System32 

### Installing OpenMRS or running database updates fails with message “Could not acquire change log lock”

To prevent conflicting updates, liquibase begins each update by creating a row in the **liquibasechangeloglock** table. This row acts as a lock. If OpenMRS or Apache Tomcat crashes while an update is in progress, the update may fail to complete

and this row will not be removed from the table.

You may see the following error message in your web browser or in the Tomcat logs, the next time you start up or attempt to install or update OpenMRS:

```
"Error Could not acquire change log lock"
```

Deleting this row from the **liquibasechangeloglock** table will solve the problem, and allow installation or updates to proceed normally. To delete rows from the **liquibasechangeloglock** table using a command line SQL client, run either of the following SQL commands:

```
truncate table liquibasechangeloglock;
```

```
delete from liquibasechangeloglock;
```

If you prefer to use a GUI client for MySQL, you should navigate to the **liquibasechangeloglock** table and delete all rows from that table. When you have cleared the table, restart Tomcat if necessary, and restart OpenMRS.

### Problems connecting to Tomcat on port 8080

Other installed programs may already be using port 8080. This will prevent Tomcat using this port. Some software may also use port 8005, which should not interfere with running Tomcat, but may prevent it from starting up correctly.

If you know what program is using these ports, you may choose to stop or remove that program. Alternatively, you can configure Tomcat to run on a different port by editing Tomcat’s **server.xml** file to change 8080 to a different value \(eg 8090\).

If you need further help, see the "Getting Help from the OpenMRS Community" chapter for more information.

### Permission problems when running Tomcat as a service on Ubuntu

If you are trying to run Tomcat as a server on Ubuntu, you may run into permission issues. The following error is typical of these problems:

```
java.security.AccessControlException: access denied (java.io.FilePermission /usr/share/tomcat6/webapps/openmrs/WEB-INF/dwr-modules.xml delete)
```

The easiest way to solve this issue is to disable the Java security manager or similar startup script, which you can find at this location.

> /etc/init.d/tomcat6

Edit the file and set **TOMCAT6\_SECURITY** to **no**.

```
# Use the Java security manager? (yes/no)
TOMCAT6_SECURITY=no
```

### Tomcat stops responding after updating or reloading OpenMRS in the Web Application Manager

Tomcat and the JVM allocate memory to a webapp each time you use the **Update** or **Reload** functions in the **Web Application Manager**. When the app is destroyed or recreated, some of this memory may not be released. If you update or reload the webapp too many times, Tomcat may run out of allocated memory, and will stop responding. You will also see the following error in the Tomcat logs:

```
java.lang.OutOfMemoryError: PermGen space
```

It is not possible to completely avoid this problem. However you can mitigate it by allowing Tomcat to use more memory, or by restarting Tomcat if you have to repeatedly update or reload a webapp.

### Deploying OpenMRS using the Tomcat Manager web application fails

For various reasons, trying to deploy OpenMRS using the Tomcat Manager web application may fail. If this occurs, you should undeploy OpenMRS using the Tomcat Manager, then stop Tomcat.

You can do this on the command line under Linux or OS X. First, find the process ID \(PID\) by running the following command:

```
ps ax | grep tomcat
```

This may return several lines, each starting with a number. Look for a long line that contains something like /usr/local/tomcat or /opt/tomcat. The PID is the first number on that line. Stop Tomcat with the following command:

```
kill -9 PID
```

Finally, you can restart Tomcat as follows:

```
service tomcat6 start
```

Log back into the Tomcat Manager web application and deploy OpenMRS normally.

### OpenMRS \(openmrs.war\) deploys successfully but fails to start

If there are issues with the OpenMRS settings for application\_data\_directory, openmrs.war may successfully deploy, but then fail to start. The following messages are seen in Tomcat's logs:

```
SEVERE: Error listenerStart
SEVERE: Context [/openmrs] startup failed due to previous errors
```

Ensure that the runtime properties file exists, and that the application\_data\_directory is specified in this file. Then ensure that the directory exists, and that Tomcat has read and write permissions to the directory.

If the directory exists as specified in the runtime properties file and Tomcat has the appropriate permissions, you may have security violation problems in your Tomcat configuration. If you need further advice, consider seeking help from the community, as described in the chapter "Getting Help from the OpenMRS Community".

**Unable to log in to Tomcat Manager due to lost password**

The Tomcat admin password is required to log in to the Tomcat Manager web application, and to deploy and undeploy applications, including OpenMRS.

If you have forgotten, lost, or misplaced this password, you can retrieve it from the file **tomcat-users.xml**. On Windows, this is probably located at this location.

> C:\Program Files\Apache Software Foundation\Tomcat 6.0\conf\

### The database password or other properties are set incorrectly

If you have installed the OpenMRS Standalone application, you can modify settings by editing the **openmrs-standalone-runtime.properties** file in the directory where you extracted the ZIP package.

To modify settings for the OpenMRS Enterprise version, you should edit the file **openmrs-runtime.properties**. You should find this file in one of the following locations:

On Windows systems:

* C:\Documents and Settings\YOURUSERNAME\Application Data\OpenMRS

* C:\Windows\system32\config\systemprofile\Application Data\OpenMRS


On Mac OS X or Linux systems:

* ~/YOURUSERNAME/.OpenMRS

* /usr/share/tomcatX/.OpenMRS


### The OpenMRS administrator account password has been forgotten

In general, when a user is locked out, the password should be reset by the administrator using the "Edit User" page from the OpenMRS **Administration** page. In rare situations in which the administrator's account has been forgotten, the only way to reset the password is to directly modify the OpenMRS database. This should only be attempted by advanced users, and you should always back up your database before making changes.

You will need to modify the **users** table in the OpenMRS database schema. Find the row for the user in question and change the **password** and **salt** values to the following:

* **password**: 4a1750c8607d0fa237de36c6305715c223415189

* **salt**: c788c6ad82a157b712392ca695dfcf2eed193d7f   


### Some module pages throw **java.lang.ClassNotFoundException**

There are currently some issues with compatibility between OpenMRS and versions of Apache Tomcat later than 6.0.29. OpenMRS modules that rely on certain custom expression language functions will throw ajava.lang.ClassNotFoundException exception.

If you encounter this issue using a version of Tomcat greater than v6.0.29, you may need to disable any modules that rely on custom expression language functions, or install Tomcat 6.0.29 for use with OpenMRS.

### Starting OpenMRS fails with message “Module file does not have the correct .omod file extension”

OpenMRS will not start if there are non-modules in the modules directory. You may find a message in the logs similar to these:

```
org.openmrs.module.ModuleException: Module file does not have the correct .omod file extension Module: derby.log
```

```
org.openmrs.module.ModuleException: Module file does not have the correct .omod file extension Module: velocity.log
```

To solve this problem, delete or move any files in the modules directory that are not modules with an.omodextension. 

In particular, the **BIRT Runtime** creates various log files in the modules directory when the **BIRT** module is stopped. If you are using the **BIRT Report** module, there may be non-module files in the OpenMRS modules directory--typically, **derby.log** or **velocity.log**. These files can safely be moved to another location or deleted.

To prevent thederby.logfrom being created in future, delete the directory **org.apache.derby.core\_10.1.2.1** which is located under the following directory. 

> birt-runtime-2\_2\_0/ReportEngine/plugins/

### MySQL packet length errors, or MySQL Error 2006

These errors occur when the client or server tries to handle data larger than the maximum packet length. The default maximum packet length is 1MB. Some items \(such as form data\) can easily exceed this maximum, causing errors when importing data into or exporting data from the OpenMRS database.

To increase the maximum packet length allowed by your MySQL server, you should stop the server, edit the configuration file, then restart the server. The configuration file is typically located at one of these locations.



* Windows: C:\Program Files\MySQL\MySQL Server x.x\my.ini

* Linux or Mac OS X: /etc/my.cnf




This file should already contain a section with the header **\[archive:mysqld\]**. You can add the following line below that header:

```
max_allowed_packet=64M
```

You can also increase the maximum packet length using the MySQL Administrator application, by opening the Health section and changing the **max\_allowed\_packet** setting on the System Variables tab. This setting can be increased up to a maximum of **1024M** as necessary.

Depending on your MySQL client, you may also need to adjust the maximum packet length of the client. If you are using the MySQL command line client, you can start it with an increased **max\_allowed\_packet** by adding the following after the MySQL command:

```
--max_allowed_packet=64M 
```

### Problems connecting to MySQL on a system with multiple MySQL installations

If MySQL is already installed and running on your system, OpenMRS Standalone's initial setup may be unable to create the OpenMRS user and database. You may also encounter this problem after installation, if you have installed a "traditional" MySQL server and try to run OpenMRS Standalone.

This problem happens because MySQL clients on UNIX-based systems always use UNIX sockets to connect to MySQL when **localhost** is specified in the connection URL. This is a known issue/limitation/bug in MySQL and is documented in more detail by the MySQL project.

[http://bugs.mysql.com/bug.php?id=31577](http://bugs.mysql.com/bug.php?id=31577)

It is possible to run OpenMRS in a separate database instance than the one already existing on your system \(for example, to run OpenMRS Standalone on a system where MySQL is already installed\). To do so, you must first ensure that the new database instance is running on a different port.

Then, ensure that you are connecting to MySQL via TCP/IP instead of using the same UNIX socket as the existing instance. The easiest way to do this is to use **127.0.0.1** instead of **localhost** in the connection string. An alternative is to add **&server.port=XXXX** to the value of **connection.url** in the **openmrs-runtime.properties** file, where **XXXX** is the port used by the OpenMRS MySQL instance.

For example, if the MySQL instance used by OpenMRS is running on port **4242**, the **openmrs-runtime.properties** file should include one of the following lines:

```
connection.url=jdbc:mysql://127.0.0.1:4242/openmrs?autoReconnect=true&sessionVariables=storage_engine=InnoDB&useUnicode=true&characterEncoding=UTF-8
```

```
connection.url=jdbc:mysql://localhost:4242/openmrs?autoReconnect=true&sessionVariables=storage_engine=InnoDB&useUnicode=true&characterEncoding=UTF-8&server.port=4242
```

### Tomcat error log contains IOException while loading persisted sessions

Apache Tomcat tries to restore the exact memory state after each restart. OpenMRS does not depend on this feature, so you can ignore any warnings printed to the Tomcat logs that look similar to the following:

```
SEVERE: IOException while loading persisted sessions: java.io.WriteAbortedException: writing aborted; java.io.NotSerializableException:
```

If you find these messages annoying, you can turn off session persistence. Edit the **&lt;TOMCAT\_HOME&gt;/conf/server.xml** file and uncomment the line that includes:

```
<Manager pathname="" />
```

### Java Heap Size errors

OpenMRS uses a lot of memory for caching. Certain tasks, such as exporting data, may cause a Java Heap Size error. You can mitigate this by increasing the default memory allocation in Tomcat.

If you are starting Tomcat on the command line, you should pass the following parameters to increase the default memory allocation: 

```
-Xmx512m -Xms512m -XX:PermSize=256m -XX:MaxPermSize=256m -XX:NewSize=128m
```

If you are running Tomcat as a Windows Service, you can increase the memory allocation by adding this same line to the list of start parameters. Make sure that you add this to the end of the existing parameters exactly. An extra space at the end of the line can prevent Tomcat from starting properly. You can find the list of start parameters in the Tomcat Monitor application, by going to **Configure Tomcat &gt; Java &gt; Java Options**, or via the **Control Panel &gt; Services &gt; Apache Tomcat &gt; Properties &gt; Start Parameters**. 

If you are running a 64-bit version of Tomcat as a Windows Service, you must edit the Windows Registry to add that line to the **HKEY\_LOCAL\_MACHINE\SOFTWARE\Apache Software Foundation\Procrun 2.0\Tomcat5\Parameters\JavaJVM** settings in the Registry.

If you are running Tomcat on Ubuntu, edit its startup script such as **/etc/init.d/tomcat6** and make the following changes:

```
if [ -z "$JAVA_OPTS" ]; then
        JAVA_OPTS="-Djava.awt.headless=true -Xmx128M"
fi
```

```
if [ -z "$JAVA_OPTS" ]; then
        JAVA_OPTS="-Djava.awt.headless=true -Xmx1024M -Xms1024M -XX:PermSize=256m -XX:MaxPermSize=256m -XX:NewSize=128m"
fi
```

If you are running Tomcat as a Linux service, open the **/etc/init.d/tomcat** script and append change the **CATALINA\_OPTS** variable:

```
CATALINA_OPTS="-Djava.library.path=/opt/tomcat/lib/.libs -Xmx512m -Xms512m -XX:PermSize=256m -XX:MaxPermSize=256m -XX:NewSize=128m"
```

### Memory leaks

After troubleshooting, you may determine that Tomcat or OpenMRS is having problems with memory leaks.

To mitigate memory leak problems in Tomcat, consider enabling pooling by adding the following element to the JSP servlet definition in the file **&lt;TOMCAT\_HOME&gt;/conf/web.xml**:

```
<init-param><param-name>enablePooling</param-name><param-value>false</param-value></init-param>
```

If you believe you have discovered a memory leak in OpenMRS and are comfortable looking at the OpenMRS application code to identify where the leak is located, you may like to troubleshoot further to find out the cause. OpenMRS developers use YourKit Profiler to discover and debug memory and CPU consumption issues. 

YourKit is kindly supporting members of the OpenMRS community with its full-featured Java Profiler product. If you have development skills you may want to use this tool to understand why the application is leaking memory or consuming too many processor resources. As an active participant in the OpenMRS community, you can request a license by opening a support desk ticket

[http://go.openmrs.org/helpdesk](http://go.openmrs.org/helpdesk)

## Bugs in OpenMRS

If you believe you have discovered a problem that may be a bug in OpenMRS, we encourage you to report that bug. The OpenMRS development team takes bug reports seriously and continually fixes as many bug reports as possible for future releases. Please see our bug report page on the OpenMRS wiki for further details and instructions:

[https://issues.openmrs.org/](https://issues.openmrs.org/)

