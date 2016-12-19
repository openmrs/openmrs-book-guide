# Sharing Concepts and Metadata

_Working with OpenMRS forms at Hôpital Albert Schweitzer, Deschapelles, Haiti._
![](/assets/forms.png)

Instead of creating concepts, forms and other metadata yourself, you are highly encouraged to use some which are publicly available. You can use complete concept dictionaries like MCL or MVP as well as metadata packages which include just a fraction of dictionaries, forms, locations, etc.

Sharing forms entails sharing associated concepts and other metadata. To facilitate this task, the **Metadata Sharing** module was created. It allows all kinds of metadata \(concepts, forms, locations, roles, programs, etc.\) to be exchanged between different OpenMRS installations.

Any dependent metadata will be packaged along with the exported item. For example, if you export a concept which has coded answers, the module will package the initial concept along with all the coded answer concepts, class and datatype. If you export a form, it will package the form along with the encounter type, all concepts used on that form, etc.

The import process is designed in a way to help identify items in your system that are semantically the same as the ones included in a package so that you can skip importing them and use yours.

You can find some published forms at:

[https://wiki.openmrs.org/display/RES/Form+Bank](https://wiki.openmrs.org/display/RES/Form+Bank)

![](/assets/case-study.png)

Let's see an example of importing a form with the Metadata Sharing module. The **Amani Antenatal History** form will be presented in detail in the "Data Entry" chapter.

After installing the Metadata Sharing module, go to **Administration &gt; Import Metadata**.

![](/assets/mds_import_1.png)

1. Import a new package

2. See a list of previously imported packages you are subscribing

To start, click the **Import package** button and on the next screen, point to a file you want to import.

![](/assets/mds_import_file.png)

1. Choose a local file you want to import

2. Enter a subscription URL

![](/assets/mds_import_level.png)

The next step is to choose a trust level. As stated before, while importing a package you will have a chance to use concepts, locations, etc. which exist in your system rather than creating new ones from the package. If you choose to do so, you can either overwrite your existing items or keep the ones you already have. If you choose **Require Confirmation**, you will be asked to review most of the metadata before importing and decide what you want to do. The **Trust Incoming** option in most cases will default to overwrite your existing metadata and will not require confirmation. Click **Next** to proceed.

![](/assets/mds_import_assess_1.png)

1. Items needing assessment

2. Items to be created

3. Items to skip

4. Items in your system which will be used instead

5. Items which will be overwritten

6. Opens the assessment screen

7. All items in the package


On the next screen, you will see some details about the package and clicking **Next** again will bring you to the **Import Summary** page where you can assess items. As in our example, you will have to review twenty-nine concepts.

![](/assets/mds_import_assess_item.png)

The assessment screen depending on the case allows you to choose **Create New**, **Skip if Possible**, **Choose Existing - Keep Mine**, and **Choose Existing - Overwrite**. If you select **Choose Existing** you will be able to search for an existing item on your system by clicking **Choose replacement**. In this example, you cannot select **Create New** as it would violate a restriction that there cannot be two concepts in the system with the same name.

Once reviewing all the items which need to be assessed, you can import the package.

A good source of concepts is the Maternal Concept Lab:

[http://www.maternalconceptlab.com](http://www.maternalconceptlab.com/)

It allows you to find concepts you need and download them as metadata packages. You can then import them directly to your OpenMRS installation as needed with the help of the Metadata Sharing module.

The Metadata Sharing module promotes decentralized management of metadata where everyone can both create and import metadata packages.

