---
order: 80
---
# Maintenance

![_OpenMRS server room in Webuye, Kenya._](/assets/maintenance.png)

Once you have installed and configured OpenMRS and it is being used to support day-to-day clinical operations, there is still work to be done. To ensure the system runs smoothly and error-free, use the following tips as a starting point to create a maintenance plan for your OpenMRS installation. We recommend documenting this plan and reviewing it regularly.

## Server management

Although outside the scope of this book, it is important to keep both your OpenMRS server(s) and client systems updated with the latest security patches. In Windows, you should use the Windows Update tool to review and install critical system updates. If you use Linux, use either **apt-get upgrade** or **yum update**, depending on what distribution of Linux you use.

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

You may need to adjust some settings in OpenMRS. To do this, use the **Maintenance &gt; Advanced Settings** page under the OpenMRS **Administration** section, find the desired setting and clear or change its value as described in the following tips, then click the **Save** button at the bottom of the page.

![](/assets/globalprop-regex.png)

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

  * If running Tomcat as a Windows service, launch the Tomcat Monitor application. Go to Configure &gt; Java &gt; Java Options and add the following to the listed settings:

    ```
    -Xmx512m -Xms512m -XX:PermSize=256m -XX:MaxPermSize=256m -XX:NewSize=128m
    ```

  * If running Tomcat as a Linux service, edit the **/etc/init.d/tomcat** \(or equivalent\) script and modify the line for **CATALINA\_OPTS** to read as follows:

    ```
    CATALINA_OPTS="-Djava.library.path=/opt/tomcat/lib/.libs  -Xmx512m -Xms512m -XX:PermSize=256m -XX:MaxPermSize=256m  -XX:NewSize=128m"
    ```

* Adjust Tomcat to prevent potential memory leaks. Tomcat has a default setting that often causes memory leaks. To turn it off, open the configuration file.

  > &lt;TOMCAT_HOME&gt;/conf/web.xml

  In JSP servlet definition add the following element:

  ```html
  <init-param>
  <param-name>enablePooling</param-name>
  <param-value>false</param-value>
  </init-param>
  ```

* Experiment with better garbage collection in Tomcat to prevent PermGen out of memory errors. To use a newer version of Tomcat garbage collection, you need to add the following to **CATALINA_OPTS**, as was shown above in the previous step.


### MySQL

Optimizing MySQL database settings will help OpenMRS to run more efficiently, especially as your installation grows in the size of data you are storing.

Increase theinnodb\_buffer\_pool\_size. It is the size in bytes of the memory buffer InnoDB uses to cache data and indexes of its tables. The larger you set this value, the less disk I/O is needed to access data in tables. On a dedicated database server, you may set this to up to 80% of the machine physical memory size. However, do not set it too large because competition for physical memory might cause paging in the operating system. Modify the following in MySQL'smy.inifile, or add it if it is not present.

```
max_allowed_packet=64M
```

Increase themax\_allowed\_packet size. When MySQL attempts to work with a packet of data larger than specified, it causes apacket too largeerror and closes the connection, causing OpenMRS to stop working. Increasing this value allows MySQL to handle larger sets of data. Modify the following in MySQL'smy.inifile, or add it if it is not present.

```
innodb_buffer_pool_size=3G
```

You may also consider running a MySQL performance-tuning script and making adjustments to your MySQL configuration file based on its suggestions. One such script is available here:

[https://wiki.openmrs.org/display/docs/Performance+Tuning](https://wiki.openmrs.org/display/docs/Performance+Tuning)

## Replication options

Replication of your OpenMRS installation across multiple servers or multiple sites is an advanced topic that is outside the scope of this book. However, you should be aware that several options exist if you require access to your OpenMRS data from alternate locations.

### MySQL replication

The MySQL database offers methods for replicating your database across multiple servers, meaning it is possible to have multiple synchronized copies of your OpenMRS data. Please consult the MySQL documentation for details. If you point an identically-configured OpenMRS server at this replicated database, you will have a mirrored instance of OpenMRS. It is important to ensure that if you make changes to the primary system, those same changes take place on all servers.

### Sync module

Another option is available for OpenMRS installations with multiple sites. The community-developed **Sync** module is available from the OpenMRS module repository, and allows data to be synchronized across a network (or external data storage) using tools within OpenMRS itself. Please search the OpenMRS Wiki for more information about the **Sync** module.

## Upgrading OpenMRS

The OpenMRS implementer and developer communities provide application and customization support via mailing lists, IRC, and other means. See "Getting Help from the OpenMRS Community" for more information.

When the development team release a new upgrade for OpenMRS, they will provide either a new version of the OpenMRS Standalone installer or the OpenMRS Enterprise installer file to run on your server. If using the Standalone version, follow the upgrade instructions included with the application. If using the Enterprise version, you should be able to undeploy the OpenMRS webapp in Apache Tomcat, and deploy the new version.

Be sure to test any upgrades on a server other than the primary server you use for normal clinical support. Always be sure to back up your system before upgrading.

## Updating modules

Supported community-developed OpenMRS modules are regularly updated, and those new versions are published in the OpenMRS module repository. You should check for upgraded modules regularly. Go to [http://modules.openmrs.org/](http://modules.openmrs.org/) or view the "Manage Modules" page from the OpenMRS **Administration** page. From there, you can upgrade a module with updates automatically by clicking **Install Update**, or you may manually upload the new version by following the instructions on the page.

## Amani's maintenance plan

![](/assets/case-study.png)

As part of his responsibilities as ICT infrastructure manager for the clinic, Daniel created a written maintenance plan. In this document, he has included daily, weekly, and monthly tasks. The only daily task is an automated one -- Daniel created a script on his Ubuntu server to stop OpenMRS, backup MySQL and other OpenMRS files, and restart the application. This script runs overnight while the clinic is closed. Weekly, Claudine manually checks the disk space and runs `apt-get upgrade` to update system components. Every month, Claudine checks the OpenMRS web site for OpenMRS upgrades and upgrades to the modules the clinic uses.