# Installation and Initial Setup

![](http://write.flossmanuals.net/openmrs/installation-and-initial-setup/static/installing.png)

You can download OpenMRS from the OpenMRS web site.

[http://openmrs.org/download/](http://openmrs.org/download/)

There are two ways to install OpenMRS: Standalone, and Enterprise. You must have Java 6 or higher installed on your system to run OpenMRS.

OpenMRS Standalone provides a simplified installation option with an embedded database and web server. It is a great way to evaluate and explore OpenMRS, letting you get a local version up and running within minutes, and includes download options with sample data. OpenMRS Standalone should run fine for smaller installations \(fewer than 10,000 patient records\), but if you are setting up a larger installation, we recommend using the Enterprise installation. If you are not sure which makes sense, you can start with a Standalone installation and migrate your data to the Enterprise version later.

OpenMRS Enterprise is appropriate for larger installations. If you already have a Java servlet container and a database installed, and you want to set up OpenMRS to use these resources, you should use OpenMRS Enterprise.

## OpenMRS Standalone

To install the standalone version, download the ZIP file and decompress it, then double-click the **openmrs-standalone.jar** file to run it. The first time you run this file, it will install OpenMRS and open your browser to the new OpenMRS instance.

During setup, there is an option to install demo data. You may choose to install a demo concept dictionary, which can jump-start your form creation process.  You may also install demo patient data, which will provide a better demonstration of patient encounters and demographics.

**Do not delete or rename any files or folders **after decompressing the ZIP file. These files and folders are required by the standalone installer.

Alternatively, from the command line, you can navigate to the decompressed folder and run the following command:

```
java -jar standalone-1.1.jar
```

On Linux, you can also double-click on the file named **run-on-linux.sh**. If you are prompted for how to run it, just select **run**. Alternatively, you can use a command line shell to navigate to the decompressed folder and run the following command:

```
./run-on-linux.sh
```

### Upgrading Standalone

To upgrade a copy of OpenMRS Standalone, do the following:

1. Stop the previous version of OpenMRS Standalone and exit the application.

2. Download and extract the most recent version of OpenMRS Standalone.

3. Copy your **database** directory from the previous version to this new OpenMRS directory.

4. Copy your **openmrs-standalone-runtime.properties** from the previous version to this new OpenMRS directory.

5. Install OpenMRS Standalone as described above. The new version of OpenMRS will run with your old data.


### Logging in

By default, the initial username and password are as follows:

* Username: admin

* Password: Admin123


You must immediately change the admin password after installation for security purposes. To change your password, click **My Profile** in the upper right of OpenMRS, and choose the **Change Login Info tab**. Update your password, then click **Save Options**. You can also change your username, and provide your real name, on this screen.

### Stopping and restarting

As long as OpenMRS is running, you can return to the application by opening the following URL in your browser.

```
http://localhost:8081/openmrs-standalone/
```

Before you change certain preferences, such as the port on which MySQL or Tomcat runs, you must stop the application.

To stop the application, use the **Stop** button in the user interface, or choose **File &gt; Quit**. Alternatively, run the JAR file on the command line with a **-stop** parameter.

You can restart the GUI by clicking **Start**, or double-clicking on the JAR file again. Alternatively, you can run the JAR file with a-startparameter.

By default, OpenMRS runs the MySQL database on port 3316, and the Tomcat server on port 8081. To use a different port, stop the application, then change the port number in the** openmrs-standalone-runtime.properties **file or in the GUI, and restart. To override the port from the command line, run the JAR file with a **-tomcatport** or **-mysqlport** parameter.

Changing the port number will change the URL used to access the application. To access the application, you can choose **File &gt; Launch Browser**, or run the JAR file with a **-browser** parameter.

## OpenMRS Enterprise

You must have Apache Tomcat and MySQL installed on your system before installing the enterprise version of OpenMRS.

Download the Enterprise WAR package from

[http://openmrs.org/download/](http://openmrs.org/download/)

Navigate to the Tomcat Web Application Manager and enter your Tomcat administrator credentials.

```
http://localhost:8080/manager/html
```

Browse to the location of the **openmrs.war** package, and deploy it.

The initial setup which follows may take some time. At the end of the process, the Web Application Manager will refresh, and/openmrsshould be displayed in the list of applications. Tomcat should also start the application \(Running = True\).

Open the OpenMRS web application to complete the initial setup process.

```
http://localhost:8080/openmrs
```

### Getting Started with OpenMRS Enterprise

The first time you run OpenMRS, the setup wizard will help you configure your installation. Follow the instructions in this wizard to set up your database and populate it with test data if necessary.

To change your configuration later, stop the application, edit the file **openmrs-runtime.properties**, and restart the application. On Windows, you can probably find this file in this location:

**C:\Documents and Settings\YOURUSERNAME\Application Data\OpenMRS**

or

**C:\Windows\system32\config\systemprofile\Application Data\OpenMRS**

On Mac OS X or Linux systems, it is probably located in this location:

**~/.OpenMRS**

or

**/usr/share/tomcatX/.OpenMRS**

After you have finished configuring OpenMRS, reload the application in the Web Application Manager. Open the login page, typically at this URL.

```
http://localhost:8080/openmrs
```

If Tomcat is installed on another server or another port, replace **localhost** or **8080** as applicable.

Use the administrator username and password you specified in the configuration wizard to log in. If you did not specify a username and password, try using the default username **admin** and password **Admin123**.

### Upgrading OpenMRS Enterprise

To upgrade a copy of OpenMRS Enterprise, do the following:

1. Use the Tomcat Web Application Manager to stop the previous version of OpenMRS.

2. Download the most recent version of OpenMRS Enterprise.

3. Install OpenMRS as described above. The new version of OpenMRS will run with your old data.


## Amani chooses the Enterprise version

![](http://write.flossmanuals.net/openmrs/installation-and-initial-setup/static/case-study.png)

Although Amani Clinic is small, they decided to install the Enterprise version. Claudine is very familiar with Apache Tomcat and MySQL, and decided she would like more control over the system. She installed Ubuntu Linux on the physical server, then installed Java 6, MySQL, and Tomcat. After doing so, she downloaded the **openmrs.war **file and installed it in the Tomcat application server. Excluding download time for the software, she was able to complete the process in less than one hour.

