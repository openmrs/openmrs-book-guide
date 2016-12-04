# Maintenance

![](http://write.flossmanuals.net/openmrs/maintenance/static/maintenance.png)

_OpenMRS server room in Webuye, Kenya._

Once you have installed and configured OpenMRS and it is being used to support day-to-day clinical operations, there is still work to be done. To ensure the system runs smoothly and error-free, use the following tips as a starting point to create a maintenance plan for your OpenMRS installation. We recommend documenting this plan and reviewing it regularly.

## Server management

Although outside the scope of this book, it is important to keep both your OpenMRS server\(s\) and client systems updated with the latest security patches. In Windows, you should use the Windows Update tool to review and install critical system updates. If you use Linux, use either **apt-get upgrade** or **yum update**, depending on what distribution of Linux you use.

Before upgrading MySQL, Java, or Apache Tomcat \(and of course, OpenMRS\) you should check with the OpenMRS community to see how those upgrades might effect how OpenMRS runs on your server. See the "Getting Help" section for more information.

You should also periodically check to ensure your server has plenty of free disk space. Additionally, if you are running a Windows server, ensure your system has anti-virus software installed and it is up-to-date.

## Backups

You should ensure your system has a backup strategy. Much has been written on this subject and general knowledge about backups is beyond the scope of this book. However, there are some specific items to consider when backing up your OpenMRS server.

Most importantly, you need to create a backup strategy for your MySQL database. Perhaps the simplest way to do this is by using the **mysqldump** utility that ships with the database. Ideally, you will want to shut down OpenMRS before backing up, and restart it once the backup has completed. If you are not able to do so, or wish to have the system remain in a "read-only" mode, you may want to use the options of **mysqldump** to lock tables. Consult the MySQL documentation for details.

You should also ensure you are backing up the **.OpenMRS** directory. This directory, which stores modules and configuration files, is stored in the home directory of the user that runs the Tomcat server on Windows or Linux.



## Performance tuning

Over the past several years, implementers of OpenMRS around the world have compiled information about improving the performance of their systems. There are several components of the system that may need to be tuned to ensure optimal performance. Please use the information in the following sections as a guide and a starting point -- you will need to explore what settings work best for your system.

### OpenMRS settings

Note:From version 1.9 and above, "global properties" will be referred to as "settings" in the guide.

You may need to adjust some settings in OpenMRS. To do this, use the **Maintenance &gt; Advanced Settings** page under the OpenMRS **Administration** section, find the desired setting and clear or change its value as described in the following tips, then click the **Save** button at the bottom of the page.

![](http://write.flossmanuals.net/openmrs/maintenance/static/globalprop-regex.png)

* Clear out the **patient.identifierRegex** setting to disable regular expression identifier searches.

* Clear out the **patient.identifierPrefix** and **patient.identifierSuffix** settings to disable "like" identifier searches.

* Make sure that the **dashboard.regimen.displayDrugSetIds** setting has concept ID numbers and not names. In other words, use "1085,1159" instead of "ANTIRETROVIRAL DRUGS,TUBERCULOSIS TREATMENT DRUGS".

* Set the **searchWidget.batchSize**, **searchWidget.runInSerialMode** and **searchWidget.searchDelayInterval** settings to tune your searches for better performance and suit your implementation's environment. You may wish to consider the speed of your network connection, typing skills and average number of simultaneous users on a typical work day. You might also consider reducing the value of the settings person.searchMaxResults and **searchWidget.batchSize** to reduce the load on the search widgets and server for better performance.


### Apache Tomcat

Tomcat has several settings that may be adjusted to optimize its use of memory:

* Experience has shown it is best to install Tomcat from the download section at [http://tomcat.apache.org/](http://tomcat.apache.org/) rather than any other source. If using Ubuntu Linux, we do not recommend using the apt-get installer.

* Increase the amount of memory allocated for Tomcat. Depending on how you start or run Tomcat, use one of the following methods:

  * If running Tomcat from the command line, add the following parameters:

   ```
-Xmx512m -Xms512m -XX:PermSize=256m -XX:MaxPermSize=256m -XX:NewSize=128m
   ```

  * If running Tomcat as a Windows service, launch the Tomcat Monitor application. Go to Configure > Java > Java Options and add the following to the listed settings:

   ```
-Xmx512m -Xms512m -XX:PermSize=256m -XX:MaxPermSize=256m -XX:NewSize=128m
   ```
  * If running Tomcat as a Linux service, edit the **/etc/init.d/tomcat** (or equivalent) script and modify the line for **CATALINA_OPTS** to read as follows:

   ```
CATALINA_OPTS="-Djava.library.path=/opt/tomcat/lib/.libs  -Xmx512m -Xms512m -XX:PermSize=256m -XX:MaxPermSize=256m  -XX:NewSize=128m"
   ```

* Adjust Tomcat to prevent potential memory leaks. Tomcat has a default setting that often causes memory leaks. To turn it off, open the configuration file. 

  > <TOMCAT_HOME&gt;/conf/web.xml 

  In JSP servlet definition add the following element: