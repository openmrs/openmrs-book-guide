# The Patient Dashboard In Depth

The Patient Dashboard is the place to view or edit a patient record, and add new Visits and Encounters.

The Patient Dashboard appearance may be changed by modules. This chapter will show the dashboard as it looks without modules.  



### Finding or Creating a Patient

To begin, we must find or create a patient. This is done from the Find/Create Patient link on the top menu.

![](http://write.flossmanuals.net/openmrs/the-patient-dashboard-in-depth/static/around%20find_2.png)

Creating patients is explained in the [Registering Patients](registering-patients.md) chapter.



### Header

 The header bar appears at the top of the dashboard. It contains a summary of some patient details:  name, ID number, gender, age and birthdate, weight, and regimen. There will be a link to any visit in progress.  If no visits are in progress, one can be begun with the **Start Visit** button.

![](http://write.flossmanuals.net/openmrs/the-patient-dashboard-in-depth/static/patient_dashboard_header_1.png)



### Overview Tab

![](http://write.flossmanuals.net/openmrs/the-patient-dashboard-in-depth/static/patient_dashboard_overview.png)

_The Overview tab on the Patient Dashboard._



The Overview tab gives access to several patient features. 

If a patient is a member of any Program \(configured in Administration &gt; Programs\), it will be displayed here.

The **Exit Patient from Care** button in the Patient Actions section will end the patient's participation in any program.

The **Relationships** tab shows relationships between the Patient and other patients, providers, or users in the OpenMRS installation. The default relationship types include parent-child, sibling, doctor-patient, and aunt/uncle-niece/nephew. You can add relationship types in Administration &gt; Person &gt; Manage Relationship Types.

Allergies are listed in the **Allergies** box.

Use the **Problem List** to highlight ongoing health problems.



### Regimens Tab

![](http://write.flossmanuals.net/openmrs/the-patient-dashboard-in-depth/static/patient_dashboard_regimens_tab.png)

_The Regimens tab on the Patient Dashboard._

The Regimens tab shows a patient's current and completed treatment regimens. 





### Visits/Encounters Tab

![](http://write.flossmanuals.net/openmrs/the-patient-dashboard-in-depth/static/patient_dashboard_visits_tab.png)

_The Visits/Encounters tab on the Patient Dashboard._

The Visits tab shows all of the patient's encounters, grouped into visits. If the Visits feature is disabled, the tab will be named Encounters.  

To start a new visit, click the **Add Visit** link in the Visits tab, or the **Start Visit** button in the header.

To view a visit, click the link with the visit's name. If a user has editing privileges, the visit will open in edit mode. 

![](http://write.flossmanuals.net/openmrs/the-patient-dashboard-in-depth/static/visit_edit_visit.png)

_A visit, opened in edit mode._

In edit mode, you can add or remove encounters from the visit.



To view an encounter, return to Patient Dashboard  &gt; Visits tab. Click on the View icon to the left of the encounter. If a user has editing privileges, the encounter will open in edit mode. 



![](http://write.flossmanuals.net/openmrs/the-patient-dashboard-in-depth/static/encounter_edit_encounter.png)

_An encounter opened in edit mode. For this example, we used the FormEntry module to create and display the encounter._



### Demographics Tab

View the patient's address and names from the Demographics tab. The **Edit Patient** links will let you edit the patient's information, including identifiers, birth and death dates, and relationships.

![](http://write.flossmanuals.net/openmrs/the-patient-dashboard-in-depth/static/patient_dashboard_demographics.png)

_The Demographics tab on the Patient Dashboard._



### Graphs Tab

 The Graphs tab can display graphs of patient information such as CD4 counts.



### Form Entry Tab

![](http://write.flossmanuals.net/openmrs/the-patient-dashboard-in-depth/static/patient_dashboard_form_entry_tab.png)

_The Form Entry tab on the Patient Dashboard._



To add or edit encounters, select the **Form** tab. The last three encounters are listed at the top.

To add a new encounter, select a form from the Enter Form box. Form setup and use is described in more detail in the chapters on Data Entry, HTML Forms, and XForms.

