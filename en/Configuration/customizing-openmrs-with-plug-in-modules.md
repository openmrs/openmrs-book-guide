# Customizing OpenMRS with Plug-in Modules

![](/assets/customized-openmrs.png)

OpenMRS has a modular architecture, which allows special functionality to be easily added or removed from the system. Modules have full access to the system and can modify or enhance the behavior of the system. For example, the **Sync** module adds the ability for an OpenMRS server to synchronize its data with other OpenMRS servers; the **HTML Form Entry **module provides a way to create web-based forms for collecting data; and the **Flowsheet** module adds a new way for viewing information. Modules also provide a mechanism for adapting OpenMRS to local needs. For more information about published modules visit the OpenMRS Wiki:

[https://wiki.openmrs.org/display/docs/Modules/](https://wiki.openmrs.org/display/docs/Modules)

## Module repository

You can view available modules in the OpenMRS Module Repository:

[http://modules.openmrs.org/](http://modules.openmrs.org/)

It is a place where you can find published modules. Each module has a page with a description, a link for downloading, and a link to the module's documentation.

Some modules may be under development, but not yet published in the module repository. Many of these can be seen by browsing [GitHub](https://github.com) for repositories starting with "openmrs-module-" in their name. Many community modules can be found under the OpenMRS organization on GitHub:

[https://github.com/openmrs/](https://github.com/openmrs/)

## Managing modules

You can see available modules under **Administration** page, **Manage Modules**. The listing contains all the installed modules. You can see their status \(if they are started, stopped or failed to start\) as well as uninstall them.

![](/assets/manage_modules_3.png)

To uninstall a module:

1. Stop the module

2. Start the module

3. Uninstall the module

A module is distributed as a single file with the **.omod** extension. You can install it from the dedicated **Manage Modules** section on the **Administration** page.

You can either point to a local path to the **.omod** file or find and install a module directly from the **Install from Module Repository** section which connects to the module repository.

![](/assets/add_module_3.png)

To install a module:

1. Choose a file and click **Upload**

2. Search for a module by name

3. Install the chosen module

If uploads are not allowed from the web, you can copy the **.omod** file into the folder:

**~/.OpenMRS/modules**

\(where **~/.OpenMRS** is assumed to be the **Application Data** directory which the running OpenMRS is currently using. You can find the exact location under **Administration &gt; Module Properties**.\) After moving the file to that location, restart OpenMRS. The module will be loaded and started.

## Bundled modules

OpenMRS is delivered with some bundled modules which are included in a standard installation. The list may differ from version to version. Some examples:

### HTML Form Entry

Allows anyone with basic HTML programming skills and knowledge of the OpenMRS system to create forms which can be entered without any proprietary tools directly from a web browser. It is a preferred form entry module. HTML Forms allow a lot of control over the form's layout. 
[https://wiki.openmrs.org/display/docs/HTML+Form+Entry+Module](https://wiki.openmrs.org/display/docs/HTML+Form+Entry+Module)

### XForms

Allows data entry to be done directly from any JavaScript enabled browser. The module converts an OpenMRS form to an XForm. XForms are well suited to forms that will be filled out on mobile devices.

[https://wiki.openmrs.org/display/docs/XForms+Module](https://wiki.openmrs.org/display/docs/XForms+Module)

### HTML Widgets

Provides a set of reusable HTML form field widgets that encapsulate the common input requirements for OpenMRS. It is meant to be something that developers can utilize in their code.
[https://wiki.openmrs.org/display/docs/HTML+Widgets+Module](https://wiki.openmrs.org/display/docs/HTML+Widgets+Module)

### Reporting

Provides a feature-rich and user-friendly web interface for managing reports within OpenMRS.
[https://wiki.openmrs.org/display/docs/Reporting+Module](https://wiki.openmrs.org/display/docs/Reporting+Module)

### Reporting Compatibility

Contains pages and features that were previously included into OpenMRS core code itself and are needed to run the Reporting module. It was written for the 1.5 and later releases of OpenMRS.
[https://wiki.openmrs.org/display/docs/ReportingCompatibility+Module](https://wiki.openmrs.org/display/docs/ReportingCompatibility+Module)

## Other popular modules

### Clinical Summary

Allows you to create clinical summaries.
[https://wiki.openmrs.org/display/docs/Clinical+Summary+Module](https://wiki.openmrs.org/display/docs/Clinical+Summary+Module)

### Groovy

Was created as a proof of concept \(for embedding Groovy into OpenMRS\) and to serve as a base module for other modules that want to use Groovy scripting as well.
[https://wiki.openmrs.org/display/docs/Groovy+Module](https://wiki.openmrs.org/display/docs/Groovy+Module)

### HTML Form Flowsheet

Allows you to generically model a paper flowsheet. Provides basic functionality for embedding small HTML Forms inside of larger HTML Forms, where each small HTML Form represents one row in a patient chart. Additionally, the module allows you to specify any number of tabs in a tab-based layout, each containing a distinct HTML Form.
[https://wiki.openmrs.org/display/docs/HtmlFormFlowsheet+Module](https://wiki.openmrs.org/display/docs/HtmlFormFlowsheet+Module)

### HTML Form Entry Designer

WYSIWYG Form Designer for the HTML Form Entry module.
[https://wiki.openmrs.org/display/docs/HTML+Form+Entry+Designer+Module](https://wiki.openmrs.org/display/docs/HTML+Form+Entry+Designer+Module)

### ID Generation

Provides a facility for managing identifier generation and allocation within an OpenMRS implementation. Introduces different identifier generation strategies including automatic and pooled.
[https://wiki.openmrs.org/display/docs/Idgen+Module](https://wiki.openmrs.org/display/docs/Idgen+Module)

### Metadata Sharing

Allows all kinds of metadata \(concepts, HTML forms, locations, roles, programs, etc.\) to be exchanged between different OpenMRS installations.
[https://wiki.openmrs.org/display/docs/Metadata+Sharing+Module](https://wiki.openmrs.org/display/docs/Metadata+Sharing+Module)

### Request Account

Allows users to request their own accounts, specifying their own preferred username and preferred password. An administrator can then approve or deny pending account requests.
[https://wiki.openmrs.org/display/docs/Request+Account+Module](https://wiki.openmrs.org/display/docs/Request+Account+Module)

### REST Webservices

Exposes the OpenMRS API as REST web service.
[https://wiki.openmrs.org/display/docs/REST+Web+Services+API+For+Clients](https://wiki.openmrs.org/display/docs/REST+Web+Services+API+For+Clients)

### Role-based Home Page

Allows for administrators to define a custom "home page" for each defined role within the system. These home pages may be simply pages that already exist, and which particular users would be best served to have as their default. For example, system administrators may want the Administration page as their default home. Alternatively, administrators can "author" new pages within the running application for their users.
[https://wiki.openmrs.org/display/docs/Role+Based+Homepage+Module](https://wiki.openmrs.org/display/docs/Role+Based+Homepage+Module)

### Synchronization

Fits in scenarios when you have multiple sites using OpenMRS with separate databases and you want them to copy data to each other that will keep them synchronized.
[https://wiki.openmrs.org/display/docs/Sync+Module](https://wiki.openmrs.org/display/docs/Sync+Module)

## Writing your own module

This section covers basics of writing your own module. We encourage to contribute modules you write to the Module Repository. You can also use our code repository for your module. For more information, please visit this page

[https://wiki.openmrs.org/display/docs/Creating+Modules](https://wiki.openmrs.org/display/docs/Creating+Modules)

In order to develop and test a module, you will need to have OpenMRS installed in a version on which you want to run your module.

It is best to use a dedicated Maven archetype to create a new module. Before you start you will need to install Maven. See the Maven web site at [http://maven.apache.org/](http://maven.apache.org/) for more instructions.

The next step is to update the **settings.xml** file to point Maven to the **Maven Module Archetype**. You can find the file in one of the following locations:

* Linux: **~/.m2**

* Windows XP: **C:\Documents and Settings\user\_name.m2**

* Windows Vista/7: **C:\Users\user\_name.m2**


If the settings file does not exist you need to create one. Add the following content:

```html
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"

  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
                      http://maven.apache.org/xsd/settings-1.0.0.xsd">

  <pluginGroups>
    <pluginGroup>org.openmrs.maven.plugins</pluginGroup>
  </pluginGroups>
  <profiles>
    <profile>
      <id>OpenMRS</id>
      <activation>
        <activeByDefault>true</activeByDefault>
      </activation>
      <properties>
        <archetypeCatalog>http://mavenrepo.openmrs.org/nexus/service/local/repositories/releases/content/archetype-catalog.xml</archetypeCatalog>
      </properties>
      <repositories>
        <repository>
          <id>openmrs-repo</id>
          <name>OpenMRS Nexus Repository</name>
          <url>http://mavenrepo.openmrs.org/nexus/content/repositories/public</url>
        </repository>
      </repositories>
      <pluginRepositories>
        <pluginRepository>
          <id>openmrs-repo</id>
          <name>OpenMRS Nexus Repository</name>
          <url>http://mavenrepo.openmrs.org/nexus/content/repositories/public</url>
          <snapshots>
            <enabled>false</enabled>
          </snapshots>
        </pluginRepository>
      </pluginRepositories>
    </profile>
  </profiles>

</settings>
```


Maven is a command line tool, so open a console and enter the folder in which to create a project for your new module. The command you need to run is:

```
mvn module-wizard:generate
```

Follow the steps of the wizard by answering the questions. At the end, a new Maven project will be generated. To build it you just need to enter the project folder and run:

```
mvn install
```

You will find the produced **.omod** file for your module in the directory **omod/target**.

Developing a module requires from you to be familiar with the Spring framework. Read the Spring web site at [http://www.springsource.com/](http://www.springsource.com/)for more details. There are also a few things specific to the OpenMRS platform which you will need to remember:

* The Spring web context file can be found at **omod\src\main\resources\webModuleApplicationContext.xml**.

* Modules are able to add and modify tables in the OpenMRS database. The files **omod\src\main\resources\sqldiff.xml** and **omod\src\main\resources\liquibase.xml** hold the SQL commands which can be executed as a module is installed.

* Modules can extend OpenMRS core JSP pages via extension points. A module registers an extension in **omod\src\main\resources\config.xml** for each extension point in the system to which it wants to add content.


You should find extension points in the JSP pages you want to extend. Look for:

```
<openmrs:extensionPoint pointId="..."
```

It is best to learn by example, so you should look at some other modules in the OpenMRS code repository for code snippets to reuse in your own work. Consider examining the **Webservices.rest** module.

