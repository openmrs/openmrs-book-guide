# Configuring Visits

A patient may receive several kinds of care and services while at a health clinic. For example, they may see a clinician, have an X-ray taken, and be given a lab test. Each of these services is an Encounter, recorded in a form. OpenMRS uses Visits to collect these related encounters into one group.

Visits are managed in Administration &gt; Visits. Here you can define the kinds of visits and their attributes, and set the default behavior for how visits are created.

### Manage Visit Types

A Visit Type is a name and description of a kind of visit. Every visit has a type. You should create visit types that match how your health site classifies visits, such as "Outpatient," "Hospitalization," "Dental," "Patient Education," or "TB Clinic."

### Manage Visit Attribute Types

If you wish to record extra information about visits, you can create Visit Attributes and assign them to Visit Types. For example, you might create attributes for "Followup Visit,"or "Distance Patient Traveled."

### Configure Visits

There are several settings for the Visit feature.

![](http://write.flossmanuals.net/openmrs/configuring-visits/static/visits_configure_1.png)

Visit is enabled by default, but is an optional feature. While Visit is enabled, the patient dashboard will show a tab called Visits and group all encounters by visit. If disabled, the patient dashboard will show the Encounters tab and list encounters chronologically with no grouping.

A visit has a start time and an end time. The start date and time is automatically set when a visit is created. The end date and time is left blank by default. It is set manually by a data clerk. 

The **Start auto close visits task** option changes this. If enabled, auto-close will automatically set the end date to the start date, and the end time to 23:59. 

Auto-close is useful for visit types that never last more than a day, such as outpatient or dental visits, or where the exact end time isn't important. Auto-close is not recommended for visit types that last multiple days, such as hospitalization, or where an exact duration might be important, such as an emergency room visit.

The **Encounter Visit Handler** controls visit creation and encounter assignment when an encounter is created. The default option will automatically link the encounter to a matching visit, or create one if none exists. To match, a visit must be at the same location, and the encounter dates must be between the visit start and end times. The second option assigns an encounter to a matching Visit if one exists, but does not create a new one. The third option will not assign encounters to anything.

The Encounter Visit Handler will only affect new encounters, and only while enabled. It does not affect existing visits. If you turn the feature off, or if you upgrade from an earlier version of OpenMRS,  it will not retroactively create visits.

