---
order: 40
---
# HTML Forms

This chapter will discuss only the HTML Form entry method. This is the simplest and most straightforward approach to data entry. It is supported by the **HTML Form Entry** module, which is included with the default distribution of OpenMRS. 

## Basic HTML form structure

Every HTML form must have the following minimal elements:

```html
<htmlform>
    <p>Date of encounter: <encounterDate  /> </p>
    <p>Health center: <encounterLocation /> </p>
    <p>Clinician's name: <encounterProvider role="Provider" /> </p>
...
    <p>Name of observation: <obs conceptId="x" /> </p>
    <p><submit /></p>
</htmlform>
```

### Form header

It is easiest to leave these essential elements in a form header section that you re-use at the top of each form. The mandatory observation element is included below.

![](/assets/form-header-s.jpg)

## Case study: Amani Clinic

![](/assets/case-study.png)

The clinicians at the Amani Clinic needed a way to capture patient history as part of their maternal and child health \(MCH\) program. They had been in contact with the Millenium Villages Project \(MVP\) via the OpenMRS implementers mailing list. MVP staff shared their Antenatal Visit form. The implementation team decided to use the History section from the MVP form as a basis for their MCH history form.

The MVP Antenatal History section looked like this:

![](/assets/mvp-antenatal-history.jpg)

### Step 1: Identify and create concepts

Before you create a form, you must ensure that all reference concepts are present in the concept dictionary. Because the MVP team already had a concept dictionary, the Amani Clinic were able to import the concepts they needed. If you don't have access to an appropriate concept dictionary, you can also create new concepts directly, following the steps outlined in the chapter [Managing Concepts and Metadata](../Configuration/managing-concepts-and-metadata.md).

The MVP form included fourteen different Question Concepts, as well as Answer Concepts for \[1\], \[3\], \[6\], \[9\], \[11\], \[13\], and \[14\].

![](/assets/form-concepts.jpg)

### Step 2: Create the form

To create a form, click on the **Manage HTML Forms** link on the **Administration** page.

![](/assets/form-admin.jpg)

ClickNew Form.

![](/assets/form-new.jpg)

Enter the basic form information and click **Save**.

![](/assets/form-enter.jpg)

### Step 3: Create visual form structure with HTML

HTML forms allow you to create a structure that closely resembles your paper forms, although it may not be precisely the same.

The degree to which your form resembles the paper form depends on your HTML layout skills--all HTML tags are supported. Table layout is beyond the scope of this guide, but there are many resources available online.

This is the basic structure of the example HTML form, with a placeholder label inserted for each observation:

![](/assets/form-skeleton.jpg)

### Step 4: Insert observation elements

Next, insert a form tag for each observation in your forms. These **obs** tags are not HTML tags, but are required by OpenMRS. The following sections provide examples of each concept datatype used on the example form. The HTML Form Entry module provides a wide variety of other tags. Please consult the HTML Form reference on the wiki for full documentation along with other examples.

[https://wiki.openmrs.org/display/docs/HTML+Form+Entry+Module+HTML+Reference](https://wiki.openmrs.org/display/docs/HTML+Form+Entry+Module+HTML+Reference)

**Note**: The Concept Identifier numbers used in this example will not match the Concept Identifiers in your local OpenMRS instance.

### Example 1: Date observation

![](/assets/form-date-s.jpg)

To insert a Date Observation, include the Question Concept ID of any date-based Concept. The formatting label behind the Date Box cannot be removed.

```html
<table>
    <tr>
        <td>
            <b>Last Menstrual Period:</b>
        </td>
        <td>
            <obs conceptId="1427"/>
        </td>
    </tr>
</table>
```

### Example 2: Boolean observation

![](/assets/form-boolean-s.jpg)

To insert a Boolean observation, include the question concept ID of any boolean concept. There are several different styles available for Boolean types.

```html
...
<table>
    <tr>
        <td>
            <b>High-Risk Sex:</b>
        </td>
        <td>
            <obs conceptId="1355" style="yes_no"/>
        </td>
    </tr>
</table>
....

```

### Example 3: Coded observation with radio buttons

![](/assets/form-radio-s.jpg)

This **obs** element is inserted with the radio button style. You must specify each answer concept ID even though they are already recorded in the system as answers for the question concept. If you want to use a name other than the concept name for an answer concept, you must include the answer concept label.

To render the radio buttons vertically, insert **&lt;br \/&gt;** at the end of each label for the previous button.

```html
...
<table>
    <tr>
        <td>
            <b>Reason For Visit:</b>
        </td>
        <td>
            <obs conceptId="1433" style="radio" answerConceptIds="1435,1434,5622" answerLabels="Planning Pregnancy&lt;br \/ &gt;, Currently Pregnant&lt;br \/ &gt;, Other"/>
        </td>
    </tr>
</table> 
...

```

### Example 4: Coded observation with multi-select checkboxes

![](/assets/form-multi-s.jpg)

This **obs** element is inserted with the checkbox button style. You must specify each Answer Concept ID even though they are already recorded in the system as answers for the question concept. If you want to use a name other than the concept name for an answer concept, you must include the answer concept label.

Each checkbox selected actually represents an individual observation; the question concept is common but each answer concept is unique.

```
...
<table>
    <tr>
        <td>
            <b>Recent Contraceptive Use:</b>
            <br/>
            <obs conceptId="1635" answerConceptId="1107" answerLabel="None" style="checkbox"/>
            <br/>
            <obs conceptId="1635" answerConceptId="780" answerLabel="Oral Contraception" style="checkbox"/>
            <br/>
            <obs conceptId="1635" answerConceptId="190" answerLabel="Condoms" style="checkbox"/>
            <br/>
            <obs conceptId="1635" answerConceptId="5277" answerLabel="Natural Planning / Rhythm" style="checkbox"/>
            <br/>
            <obs conceptId="1635" answerConceptId="5278" answerLabel="Diaphragm" style="checkbox"/>
            <br/>
            <obs conceptId="1635" answerConceptId="1378" answerLabel="Depo-Provera" style="checkbox"/>
            <br/>
            <obs conceptId="1635" answerConceptId="1359" answerLabel="Norplant" style="checkbox"/>
            <br/>
            <obs conceptId="1635" answerConceptId="1388" answerLabel="Surgery" style="checkbox"/>
            <br/>
            <obs conceptId="1635" answerConceptId="5622" answerLabel="Other" style="checkbox"/>
            <br/>
        </td>
    </tr>
</table>
...

```

### Complete form

![](/assets/form-full.jpg)

See Appendix B for Full HTML source.

## Enter Patient Data Using an HTML Form

Click on **Find/Create Patient** from anywhere within OpenMRS.

![](/assets/form-find-patient.jpg)

Begin typing the patient's ID number or name, then select the patient for whom you are entering data.

![](/assets/form-select-patient.jpg)

Click the **Form Entry** tab.

![](/assets/form-click-tab.jpg)

Select the appropriate form as shown below, then fill in the patient data and click the **Enter Form** button on the page that appears.

![](/assets/form-select-form.jpg)

You can now see the completed form under the **Form Entry** tab of the patient's chart.

![](/assets/form-view-form.jpg)

