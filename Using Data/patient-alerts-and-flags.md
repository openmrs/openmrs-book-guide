---
order: 10
---
# Patient Alerts and Flags

It's important to actively use your data to provide feedback to users of the system, both for clinical purposes and data quality purposes. One way to do this is with the **Patient Flags** module, which can display **Flags** on a patient dashboard when certain criteria are met, and to find all patients that match a set of criteria. We will briefly describe this module here, but you can find further documentation at the following location:

[https://wiki.openmrs.org/display/docs/Patient+Flags+Module](https://wiki.openmrs.org/display/docs/Patient+Flags+Module)

Using this module requires significant technical knowledge. This chapter assumes that you are familiar with CSS, SQL, Groovy/Java, and the OpenMRS API.

First, you need to install **Patient Flags** module from the OpenMRS module repository, and then go to its section on the **Administration** page. First, define categories of alerts \[1\]. Then, you can define logic and messages for these alerts \[2\].

![](/assets/flags-admin.png)

## Categorizing flags by priorities

From the Manage Priorities link, you can define different categories of alerts, each of which can be decorated with custom CSS.

In this example we define two different categories of alerts, the more critical of which will be highlighted in orange, and the other in gray. Note that you need to include **thestyle="..."** in your style property.

![](/assets/flags-priority_1.png)

## Defining flags

To set up a flag, you need to define a calculation that returns the cohort of patients for whom the flag should be shown. There are multiple ways to do this, each requiring a different type of technical knowlege.

All flags, regardless of how they are calculated, let you specify text and a **Priority**. The text is displayed on a patient dashboard for patients to whom the flag applies, and the **Priority** controls the formatting of the flag if displayed.

Finally, you can decide whether flags are **Real-Time**, which means that the flags to be displayed are calculated whenever you view a patient dashboard. If you don't make a flag real-time, you can still execute the flag calculations on demand as a batch.

### SQL flags

The calculation behind this type of flag is a SQL statement that will be executed against the database, and must include a **select (something).patient_id ...** statement. The results of this query will be intersected with all non-voided patients to produce the Cohort for the flag.

Many system administrators know how to write SQL queries, and over time they become familiar with the OpenMRS data model, making this type of flag very accessible. At the same time, writing this type of flag can be error-prone. There is nothing to prevent you from omitting a clause, such as to ensure you are only looking at non-voided data.

In this example we are searching for all patients who have carried at least 4 pregnancies.

Since SQL flags must include **.patient_id** in their **select** clause, we have to join the **obs** table against the **patient** table, even though we aren't using that table.

![](/assets/flags-sql.png)

### Groovy flags

The most powerful type of flag allows you to write Groovy or Java code, which can call OpenMRS's Java API and perform complex calculations on patient data. The advantage of writing flags in Groovy is that the OpenMRS API takes care of details like ensuring you are only getting non-voided data. The limitation is that most managers of OpenMRS systems do not know how to write Groovy/Java code.

A Groovy flag returns a cohort of all patients that match the calculation. In this example we find all patients who are expected to give birth in the next 3 months, but who have_not_had an encounter in the last 3 months.

![](/assets/flags-groovy.png)

