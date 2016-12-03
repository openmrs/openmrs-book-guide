# OpenMRS Information Model

![](http://write.flossmanuals.net/openmrs/openmrs-information-model/static/infomodel.png)

_Reference books line a shelf in a rural African clinic._

This chapter explains terms and concepts which are useful to understand as you install and use OpenMRS.

## Data

The actual information you want to record in OpenMRS is calledData. Examples of Data in OpenMRS are Patients, Encounters, and Observations. To support this data, and describe its meaning, you need additionalMetadata.

When a user deletes a piece of data in OpenMRS, the information actually remains in the database. It is marked asvoided, so that it will not show up in the interface, but it is not immediately deleted from the database. If a user deletes a piece of data by accident, an administrator canunvoid it to return it to the system. To permanently delete data from the database, an administrator must purge that data. Typically, this should never be done in a production system.

## Metadata

The fundamental expectation of OpenMRS's design is that you will customize it for your clinical program's use case. The system has no built-in idea of the patient's weight or seeing the patient in an outpatient visit. Instead, you can configure these things yourself, to match your project's workflow. Generally speaking, the things that you need to configure in order to describe the real patient information you will be capturing are referred to asmetadata. An example of a piece of metadata is a Location that represents a hospital.

An administrator may alsoretire metadata in OpenMRS. This does not mean that the metadata is deleted, but rather that it is not intended to be used going forward. Old information that refers to the retired metadata remains valid. An administrator mayunretire metadata if it becomes relevant to active use again. If no actual data refers to a piece of metadata, an administrator maypurge the metadata to permanently remove it from the database.

For example, the hospital you refer patients to closes. Therefore, you can no longer refer patients there. This Location can now be retired in OpenMRS. This would not invalidate the fact that many patients were referred there in the past.

## Concepts and concept dictionary

The most important part of the system's metadata is theConcept Dictionary, which is a list of all the medical and program-related terms that you will use as questions and answers in Observations. This dictionary does not need to be complete when you begin using OpenMRS. You should expect new terms to be added and old terms to be retired as your use of the system evolves. It is better to start with a pre-populated Concept Dictionary, rather than starting from scratch yourself. See the chapter "Sharing Concepts and Metadata" for more details.

Every question you ask about a patient needs to be defined by aConcept. \(For example, to record a patient's weight you need a concept likeWeight in kilograms.\)

If you want to ask a question that has a fixed set of coded answers, those answers are also Concepts. \(For example, the question concept Blood Typemay have 4 different answer concepts: A, B,AB, andO\)

## Persons

Every individual who is referred to in a patient record in OpenMRS is stored in the system as aPerson. These include Patients, any patient relative or caretaker, Providers, and Users.

All Persons have these characteristics.

### Names

A person can have one or more names, one of which must be marked as thepreferred name. The preferred name will be displayed in search results and patient screens.

### Addresses

A person may have zero or more contact addresses. You may configure the format of these addresses for your particular locale.

### Person Attributes

To support your local needs, you can define additional pieces of information about the people in your system, on top of those that are natively supported by OpenMRS. You can define the datatype of a Person Attribute, as well as any constraints on the possible values, using metadata. This metadata is called a Person Attribute Type.

Person Attributes are suitable for storing other information. But historical values of person attributes are not retained. For example, you should use a person attribute to record a patient's contact telephone number. This information may change, but if it does so, the system need only store the most recent value, and need not retain previous values. It is not appropriate to use a person attribute to store something like the patient's height, which is recorded at a given point in time, but can be expected to change and should be tracked as it does so.

## Patients

Anyone who receives care in OpenMRS must be a Patient \(for example, anyone who has an Encounter or who is enrolled in a Program\). Every Patient must have at least one Identifier, which is explained below.

A Patient is also a Person, meaning they must have at least one name and they may have addresses.

### Patient Identifier

The Patient Identifier is a medical record number assigned by your facility, used to identify and re-identify the patient on subsequent visits.

APatient Identifier Type defines the format of a particular kind of patient identifier. For example, you might define thatAmani ID is an identifier type that is required for every patient; the format is 2 letters followed by 6 digits and uses a particular check digit algorithm.

ACheck Digit is an extra digit that is added to the end of an identifier, and depends on the rest of the identifier. It allows OpenMRS to determine whether an identifier has been mistyped. For example using a Luhn check digit, "1234-1" is valid, but "1234-5" is incorrect. It is a strongly recommended best practice to use check digits in all patient identifiers that you assign. For more information about check digits, see[http://en.wikipedia.org/wiki/Check\_digit](http://en.wikipedia.org/wiki/Check_digit)

## Relationships

![](http://write.flossmanuals.net/openmrs/openmrs-information-model/static/case-study.png)ARelationshipis a bidirectional link between two Persons in OpenMRS.

The metadata that describes a particular kind of relationship is aRelationship Type. It defines the names of each direction of the relationship. Typical Relationship Types are Parent/Child and Doctor/Patient.

At the Amani Clinic, it is necessary to use relationships to link a mother's patient record to the patient record of her children. One might also use relationships to record the link between a patient and their primary care provider.

## Visits

AVisit in OpenMRS represents exactly what it sounds like: a time period when a patient is actively interacting with the healthcare system, typically at a location. The metadata differentiating different types of visits is aVisit Type. Visit Types are displayed in the user interface, and can be searched against.

A visit contains encounters, which store more granular data about treatments or services.

At the Amani Clinic, a patient might typically check-in at registration, be seen by a doctor, and receives medication dispensed in the pharmacy. This would be recorded as one visit of type ofOutpatient, and contain three encounters \(Registration,Consultation, andDispensing\).

## Encounters

A moment in time where a patient is seen by providers at a location, and data are captured. Generally speaking, every time you enter a form in OpenMRS this creates anEncounter. Encounters typically belong to a visit, but they may also stand alone.

The metadata that describes a kind of encounter is anEncounter Type. These are displayed in the user interface, and you may also search against them.

During a typical  Amani Clinic Outpatient Visit, a patient checks in at registration, is seen by a doctor, and receives meds dispensed in the pharmacy. This would be recorded as one visit containing three encounters, whose types areRegistration,Consultation, andDispensing.

## Providers

AProvider is a person who  provides care or services to patients. A provider may be a clinician like a doctor or nurse, a social worker, or a lab tech. Generally speaking, any healthcare worker that a patient can have an encounter with is a provider.

Providers may have full records in OpenMRS as persons, or they may just be a simple name and ID number.

## Locations

ALocationis a physical place where a patient may be seen.

Locations may have a hierarchy, for exampleChildren's Ward might be a location within the locationAmani Clinic.

You might also store physical areas \(for exampleEastern Province, orCalifornia\) as Locations. You should not use locations to represent logical ideas likeAll District Hospitals.

## Observations

AnObservationis one single piece of information that is recorded about a person at a moment in time.

Every observation has a Concept as its question, and depending on the datatype of the concept, it has a value that is a number, date, text, Concept, etc.

Most of the information you store in OpenMRS is in the form of Observations, and most Observations happen in an Encounter. When you enter a form in OpenMRS, typically one Encounter is created with anywhere between tens or hundreds of Observations.

Note that an individual Observation is valid only at one moment in time, and it does not carry forward. You may query the system for the last observation forpregnancy status but this does not tell you whether or not the patient is pregnant at any point after the moment of that observation.

Examples of observations includeSerum Creatinine of 0.9mg/dL orReview of cardiopulmonary system is normal.

### Observation groups

Sometimes a single Observation is not sufficient to capture an entire piece of patient information, and you need to use multiple Observations that are grouped together.

For example, recording that a patient had a rash as an allergic reaction to penicillin would need to be stored as two observations plus a third one that groups the previous two together:

1. Concept = "Allergen", coded value = "Penicillin", group = \(3\)

2. Concept = "Reaction", coded value = "Rash", group = \(3\)

3. Concept = "Allergic Reaction Construct", group members = \(1\), \(2\)


## Orders

AnOrderis an action that a provider requests be taken regarding a patient.

For example a provider could order a Complete Blood Count laboratory panel for a patient.

An Order only records an intention, not whether or not the action is carried out. The results of an Order are typically recorded later as Observations.

Prescribing a medication is aDrug Order. A drug order can be placed for a generic drug, represented by a Concept \(for example, 500mg of Ciprofloxacin, twice a day\). If you are using OpenMRS to manage a formulary of specific medications \(i.e.,Drugs in OpenMRS\), you may also recordDrug Ordersagainst those. For example, a drug order might beOne 500mg tablet of Ciprofloxacin, twice a day.

## Allergy lists

OpenMRS lets you manually maintain anAllergy Listfor a patient, including the allergen, reaction, severity, etc.

This list is managed separately from Observations: observing an allergic reaction to a drug does not automatically add an Allergy to the list.

Unlike an Observation \(which happens at one moment in time\), an Allergy is longitudinal data, with start and end dates.

## Problem lists

OpenMRS lets you manually maintain aProblem Listfor a patient. This list is managed separately from Observations: observing that the patient has "Diagnosis Present = Diabetes" does not automatically add a problem to the list. Unlike an observation \(which happens at one moment in time\), a problem is longitudinal data, with start and end dates.

## Program enrollments, workflows, and states

AProgramrepresents an administrative program or study that a patient may be enrolled in \(for example, Child Nutrition Study orDOTS Tuberculosis Treatment Program\).

AProgram Enrollmentrepresents the fact that a patient is enrolled in one of these programs over a time period at a Location. This is longitudinal data with a start date and end date.

A Program can also define administrativeWorkflows, and possibleStatesthe patient may have within those workflows. AnInitial State is one that a patient is allowed to start in when they are first enrolled in a program. ATerminal State is one that closes the program enrollment if the patient is placed in it.

For example a research study on infant nutrition might have a workflow calledStudy Enrollment Status with the states:

* Patient Identified \(initial\)

* Mother Consented to Study

* Study Complete \(terminal\)

* Lost to Followup \(terminal\)


These states are meant to represent administrative statuses, not clinical ones. For example putting a patient in aLoss to Followup state represents an official declaration and will not happen automatically even if no encounters are entered for the patient for several months.

## Forms

AFormrepresents an electronic form that may be used for entering or viewing data. The basic OpenMRS system does not define a specific technology for entering forms. You will need to use one of the community-developed form entry modules. See the chapter "Data Entry" for more details.

The Form Entry \(Infopath\) and XForms modules rely on aForm Schema, where you define which Concepts are used on the Form. The HTML Form Entry module does not require you to manage the schema.

## Users, roles, and privileges

AUserin OpenMRS is an account that a person may use to log into the system.

The real-life person is represented by a Person record in OpenMRS, and a person may have more than one user account. If you want a patient to be able to view her own record in OpenMRS, then you need to create a user account and link it to the patient.

ARolerepresents a group of privileges in the system. Roles may inherit privileges from other roles, and users may have one or more roles.

APrivilegeis an authorization to perform a particular action in the system. The list of available privileges are defined by the core system and by add-on modules \(for example, Delete Patients and Manage Encounter Types\), but you need to configure which roles have which privileges while you are configuring your system.

## The information model in use at Amani Clinic

![](http://write.flossmanuals.net/openmrs/openmrs-information-model/static/case-study.png)

A patient named Asaba arrives at Amani Clinic, where the registration clerk James creates her electronic record and stores her contact phone number as 312-555-7890. On paper the Nurse, Kissa, records Asaba's weight as 61.5kg and orders a pregnancy test. James enters these onto an electronic screen.

From the perspective of the OpenMRS model, we have the following metadata:

* The nurse, Kissa \(a Provider\)
* The registration clerk, James \(a User\)
* Contact Phone Number \(a Person Attribute Type\)
* Weight, in kilograms \(a Concept, with class Finding and datatype Numeric\)
* Urine Pregnancy Test \(a Concept, with class Test\)
* Amani Clinic \(a Location\)
* Outpatient Visit \(an Encounter Type\)
* Outpatient Triage Form \(a Form\)

When Asaba is first seen at the registration desk, James creates the following data:

* A Patient \(Asaba\)
* A Person Attribute \(type = Contact Phone Number, value = 312-456-7890\).

After Asaba sees the nurse, who gives a paper form to James, he creates more data:

* An Encounter with:
  * patient = Asaba
  * type = Outpatient Visit
  * form = Outpatient Triage Form
  * location = Amani Clinic
  * provider = Nurse Kissa
  * creator = Registration Clerk James

* An Observation \(in that encounter\), of Weight in kilograms = 61.5.
* An Order \(in that encounter\), for Urine Pregnancy Test



