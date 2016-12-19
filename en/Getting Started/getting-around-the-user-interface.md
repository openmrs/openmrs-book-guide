# Getting Around the User Interface

_An OpenMRS implementer-programmer gives a demonstration of the system as his clinic._
![](/assets/gettingaround.png)

This chapter gives a brief overview of key parts of the OpenMRS user interface, which will be helpful as you read the chapters to follow.

## Logging in to the system

OpenMRS runs as a web application, meaning you use it via a web browser. Before you can access any pages in the system, you need to log in. To do this the first time, you will need to know the administrator password that you chose during first-time setup. Refer to the chapter "Installation and Initial Setup" for those details.

![](/assets/around-login.png)

Users that forget their password may reset it if they have configured a secret question and know the answer. TheSign up link is provided by the_Request Account_ module, if you have it installed.

## Home

In the default installation of OpenMRS, all users see the same home page after logging in. To customize different home pages for different types of users, you can use theRole Based Home Pagemodule.

![](/assets/around-home.png)

As shown in the OpenMRS home page above, all pages allow you to:

1. Log outand edit your profile, or

2. Change your language for the current session.

You can configure the allowed languages via a setting in theAdministration &gt; Maintenance &gt; Settingspage.

## Administration

As a system administrator or manager for an OpenMRS installation, you will frequently need to access the configuration and administration functions accessible through theAdministrationpage.

![](/assets/around-admin_1.png)

1. You can access theAdministrationpage from anywhere in the application by clicking its link in the top-right of the screen.

2. Configuration pages for the OpenMRS core functionality are listed in the left and center columns.

3. Configuration pages for functionality in add-on modules are listed in the right column.

4. You add/remove/start/stop add-on modules from theManage Modules page.


## Viewing and creating patients

One of the most common actions for non-administrative users of the system is to find and open existing patient records. If the desired patient record is not found, users may be able to create new ones if they have sufficient privileges.

You can search for a patient by ID number. Clicking on the search result will open that patient's dashboard. If a user does not find a patient by ID number or name, you may create a new patient.

![](/assets/around-find_2.png)

## Patient dashboard

Data entry staff will spend a lot of time on the patient dashboard page. This gives access to different parts of a patient's record and allows you to enter forms into the record.

![](/assets/updated-patient-dashboard.png)

The workflow of the patient dashboard page is not efficient for a clinician who wants to access a patient's record at the point of care. To support those workflows you should consider downloading and installing the Clinical Summarymodule or theHTML Form Flowsheetmodule.

The patient dashboard page is described in more detail in the chapter entitled "The Patient Dashboard In Depth".

