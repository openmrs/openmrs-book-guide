# Reporting

This chapter describes how to use the **Reporting** module to produce a simple report on several indicators--the type you might use for monitoring and evaluating a program.

Although this chapter will cover the basics, as your OpenMRS implementation grows, you'll want to take advantage of the Reporting module's additional features like:

* Multiple types of indicator-based reports

* Quick ways to break down indicators based on gender, age groups, etc.

* Several kinds of patient reports

* The ability to schedule regular reporting

* Easy formatting options for printed output using Excel templates

* An API that Java developers can extend to add custom reports, indicators, and displays.


The module's full functionality is beyond the scope of this book. You can find further documentation on the OpenMRS Wiki:

[https://wiki.openmrs.org/display/docs/Reporting+Module](https://wiki.openmrs.org/display/docs/Reporting+Moduleg)

This chapter follows after the ones on Data Entry, because you cannot actually build reports without some data to run them on. But while planning the project you should follow the best practice of determining what_outputs_ you want, and working backwards from there to determine the minimal set of data that you need to collect to produce those outputs.

## Background and terminology

The reporting module is built around the idea of **Definitions** that are evaluated to produce output.

### Reports and data sets 

In general a **Report Definition** can have multiple **Data Set Definitions**. When run, this will produce a report with multiple data sets, which is rendered to a format chosen by the user.

### Cohorts

Almost all reports produced with OpenMRS refer to groups of patients. A report may be run on different patient groups, or require identifying or counting sub-groups of patients. The module lets you define cohort queries \(as discussed in the chapter "Cohort Builder"\). When the report is run, these queries will be evaluated to produce actual cohorts of patients.

### Indicators

In this chapter, we look at a report that is based on **Indicators**, and specifically indicators that look at the count of patients in a cohort in a period of time.

### Parameters and mapping

Unlike in the OpenMRS Cohort Builder, reports and their underlying queries are intended to be created once, and reused. To support this idea, reports and queries usually take parameters. For example, a report intended to be run monthly would have **Start Date** and **End Date** parameters, and the user would be asked for these when they generate the report.

The underlying queries in the report also typically take parameters. If the report is going to display the number of patients enrolled in the Child Nutrition Study at the end of a given month, it would need to have an underlying Cohort Query for "patients enrolled in Child Nutrition Study on a date." p;\[/0" +{}hat date would be an Effective Date parameter.

When the user runs the report, they are asked for a **Start Date** and an **End Date**, but they are not asked to specify an **Effective Date**. When designing the report, you will need to define how parameters in the underlying queries obtain their values, based on the values provided by the user when running the report. This process is called mapping.

The idea of mapping parameters is complicated. The following resources include more information about why it is necessary, and how to do it:

* [http://go.openmrs.org/book-mapping](http://go.openmrs.org/book-mapping)

* [http://go.openmrs.org/book-mapvid](http://go.openmrs.org/book-mapvid)


## Amani Clinic's weekly report

![](http://write.flossmanuals.net/openmrs/reporting/static/case-study.png)

Before adopting OpenMRS, Amani Clinic used to spend significant time at the end of every month tabulating paper registers and patient charts to produce a monthly report for the Ministry of Health. When planning their OpenMRS implementation, they decided that to improve their program, they needed more immediate feedback. The clinic and Ministry of Health met and decided on five indicators on which they wanted a report every week. They modified their paper data collection forms to make sure that they were capturing the right data to produce those indicators, as well as the periodic Ministry of Health reports.

We'll focus on two of the indicators they calculated:

1. Number of female patients seen during the week, and

2. The percentage of those who were &gt;16 years old, not pregnant, and using appropriate family planning 


## Defining the Underlying Cohort Queries

Calculating the first of those indicators was very straightforward: they defined this to be any female patient having an encounter between the start and end of the week.

The second indicator was more complicated: they had to break down both the numerator and the denominator into multiple cohort queries. For the denominator they needed:

* Not pregnant \("no obs for Estimated Date of Confinement with a value in the future"\)

* Female

* Age &gt; 16 at the end of the week

* Had an encounter during the week \(same as the query for the first indicator\)


The numerator required just one more cohort query, for patients who self-reported use of contraceptive methods other than "Natural Planning / Rhythm" during the week.

## Building the report in the user interface

Having determined how to calculate their indicators, they proceeded to build them in the Reporting module's user interface. First, they built the low-level queries \[1\]. They then composed the two indicator definitions \[2\] from those cohort queries. Finally, they created a report definition \[3\] that included the two indicators.

![](http://write.flossmanuals.net/openmrs/reporting/static/report%20admin.png)

## Building cohort queries

TheCohort Querymanagement page shows you the different types of queries available. Clicking on any of the\[+\]links lets you create a new query of that type.

![](http://write.flossmanuals.net/openmrs/reporting/static/report%20cohort%20queries.png)

The simplest query built by Amani Clinic included only female patients:

![](http://write.flossmanuals.net/openmrs/reporting/static/report%20females.png)

The rest of the queries needed to include parameters. For example, the query to find patients with any encounter between two given dates, the "on or after" and "on or before" fields were set as aParameter\[1\] and user-friendly names "Start Date" and "End Date" were provided.

![](http://write.flossmanuals.net/openmrs/reporting/static/report%20encounters.png)

Some of the queries built in this example included parameters that were not directly equivalent to theStart Date andEnd Date of the report. The "not pregnant" query was aDate Observation Query that included a single parameter, which they later mapped to theEnd Date of the report.

![](http://write.flossmanuals.net/openmrs/reporting/static/report%20pregnant.png)

### Combining cohort queries

After Amani Clinic staff created the underlying queries that their report required, they built several Composition Cohort Queries to tie them together. The most complicated query calculated the denominator of the second indicator, "non-pregnant women, age &gt; 16, seen during the week."

This is their composition query, which includes the two parameters Start Date and End Date. It includes four underlying queries, with values in those queries mapped to these two parameters. Finally, the queries are combined with AND to run them all together. 

![](http://write.flossmanuals.net/openmrs/reporting/static/report%20composition.png)

Here, we see the seven cohort queries they built:

![](http://write.flossmanuals.net/openmrs/reporting/static/report%20all%20cohort%20queries.png)

### Indicators

Having built cohort queries to do the underlying calculations, they used these to build the two indicators. TheIndicatorspage is accessed from theManage Report Definitions section of theAdministrationpage.

Since indicators are generally calculated over a time period, at a particular location, the indicators they created contain the defaultStart Date,End Date, andLocation parameters. \(Since the Amani Clinic was only managing a single site in OpenMRS, they ignored the Location parameter.\)

#### Count indicators

The simplest type of indicator is aCount indicator, which counts the number of patients who match a cohort query.

They used aCountindicator to build their first indicator, shown below. The underlying cohort query is a composition query including "Females" and "Any Encounter Between Dates." 

![](http://write.flossmanuals.net/openmrs/reporting/static/report%20seen%20indicator.png)

#### Fraction indicators

The most useful type of indicator for monitoring program progress is theFraction indicator, which takes two cohort definitions, representing a numerator and a denominator, and displays this as a fraction. \(It ensures that the numerator patients are a subset of the denominator.\)

Amani Clinic built their second indicator as a fraction indicator. The underlying cohort query for the numerator was a simple Coded Observation Query, while the denominator was the Composition Query described above.

![](http://write.flossmanuals.net/openmrs/reporting/static/report%20indicator%20contraception.png)

### Period indicator report

Having created their indicators, they built a report that combined them. They used aPeriod Indicator Report, which is a simple way to show the indicators you have already defined.

![](http://write.flossmanuals.net/openmrs/reporting/static/report%20indicator%20report.png)

## Running the report

To run this report, the Amani Clinic data manager clicks theReporting link on the top of the screen and selects theProgram Monitoring Report. They must enter the start and end date of the week for which to generate the report.

![](http://write.flossmanuals.net/openmrs/reporting/static/report%20run.png)

The output of the report includes clickable links to the lists of patients matching each indicator.

![](http://write.flossmanuals.net/openmrs/reporting/static/report%20run%20results.png)

