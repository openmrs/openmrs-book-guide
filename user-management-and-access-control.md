# User Management and Access Control

**Roles** and **Privileges** are controlled through the **Administration** page, under the **Manage Users** section.

OpenMRS uses privileges and roles to control access to data within the system. Privileges define what can or cannot be done in the system \(e.g., **Edit Patients** or **Add Users**\), while roles are used to group privileges into more manageable groupings. To make the system easier to manage, roles can contain other roles as well as privileges. Roles inherit all the privileges of their parent roles.

We will use this example: you are working with several privileges related to patient data—e.g., **View Patients**, **Edit Patients**, and **Add Patients**. TheView Patientsprivilege lets users look at patients in the system, the **Edit Patients** privilege lets users edit information about existing patients, and the **Add Patients** privilege allows users to create a completely new patient record within the system.

Now imagine that you need to assign the proper rules to three people: Mary the Medical Student, Bob the Data Assistant, and Erica the Data Manager. You want medical students to be able to view patients, but not edit or add them. Data assistants should be able to not only view, but also edit patient data. And you want your data managers to be able to create new patients within your system.

## Designing role and privilege schemes

In order to give these privileges to the relevant users, you must define a role for each of these types of user.

<table>
  <tbody>
    <tr>
      <th>Role</th>
      <th>Privilege(s)</th>
    </tr>
    <tr>
      <td>
        Medical Student
      </td>
      <td>
        <p>View Patients</p>
      </td>
    </tr>
    <tr>
      <td>Data Assistant</td>
      <td>
        <p>View Patients</p>
        <p>Edit Patients</p>
      </td>
    </tr>
    <tr>
      <td>Data Manager</td>
      <td>
        <p>View Patients</p>
        <p>Edit Patients</p>
        <p>Add Patients</p>
      </td>
    </tr>
  </tbody>
</table>

Now, by defining the main roles for users of your system and assigning users to those roles, you have a much easier system to manage and users will automatically inherit all privileges given to their role\(s\). Of course, some users will have multiple roles. Now, let's take this process one step further. While it may not seem necessary in this simple example, as your system grows, you will likely end up with a large number of different roles. Very often, certain roles can be defined as a combination of other roles. In our example, a **Data Manager** oversees the **Data Assistants** and therefore should have all of their privileges plus some additional privileges. So, let's redesign our roles slightly to show how this might work.

<table>
  <tbody>
    <tr>
      <th>Role</th>
      <th>Inherit Privileges from Role(s)</th>
      <th>Additional Privilege(s)</th>
    </tr>
    <tr>
      <td>
        Medical Student
      </td>
      <td></td>
      <td>
        View Patient
      </td>
    </tr>
    <tr>
      <td>Data Assistant</td>
      <td></td>
      <td>
        <p>View Patient</p>
        <p>Edit Patient</p>
      </td>
    </tr>
    <tr>
      <td>Data Manager</td>
      <td>
        Data Assistant
      </td>
      <td>
        Add Patient
      </td>
    </tr>
  </tbody>
</table>


You can see that the **Data Manager** role can be more clearly defined as a **Data Assistant** with the extra ability to add patients to the system. In addition, if you should change or enhance the privileges of the **Data Assistant** role at any time in the future, the **Data Manager** will automatically adapt to those changes — for example, if you decided a month later to allow any **Data Assistant** to **Edit Encounters**\(by adding the **Edit Encounters** privilege to the **Data Assistant** role\), the **Data Manager** role would automatically gain the ability to edit encounters as well.

In a common deployment scenario, you will have several roles that use the same privileges with only a few differences. It is simpler to manage these privileges by defining a new role from which the others can all inherit. For example, you may have roles like **Clinician**, **Data Assistant**, and **Caregiver**  that all have the same rules about viewing patient data.  You might benefit from creating a new Patient Data Viewer role, assigning it to each of those other roles, and then managing the privileges in one place \(under that new role\).  When there is a policy change about viewing patient data, or a new module is added that adds new functions for viewing data, you would update the Patient Data Viewer role. All the inheriting roles would automatically use the new settings.







### Built-in roles

There are some special roles that are predefined within OpenMRS and cannot be deleted:Anonymous, Authenticated,andSystem Developer. Any privileges granted to theAnonymousrole will be available to people without logging into the system. Generally,Anonymousprivileges should be kept very restricted, since patient information might otherwise be compromised. Privileges granted to theAuthenticatedrole are granted to anyone that logs into your system, no matter what other role\(s\) they might be assigned. Granting privileges to theAuthenticatedrole is an easy way to grant privileges to all users of the system. TheSystem Developerrole is automatically granted full access to the system and should only be granted to system administrators.

Super users\(system administrators\) are automatically granted all privileges in the system; therefore, you must be very careful to protect your system administrator password.

Some privileges are built into the system and cannot be deleted. Other privileges may be added by modules. It is unlikely that you will be adding new privileges yourself, since privileges are only useful when they are understood and used by the system. On the other hand, you will definitely be creating new roles to fit your needs and will be managing privileges within those roles.

## Creating roles

You create roles throughAdministration &gt; Manage Roles.

![](http://write.flossmanuals.net/openmrs/user-management-and-access-control/static/manage_roles.png)

1. Allows to add a new role

2. Lists all roles present in the system

3. Click a role to edit it.


If you then follow theAdd Rolelink, you will see a form for adding a new role.

![](http://write.flossmanuals.net/openmrs/user-management-and-access-control/static/add_role.png)

1. Enter Role Name

2. Choose Roles Privileges of which you want to inherit

3. Choose Privileges which you want this Role to have


## Creating users

To create these users, we'll go throughAdministration &gt; Manage Users. This page also lets you find and edit existing users.

![](http://write.flossmanuals.net/openmrs/user-management-and-access-control/static/manage_users.png)

1. Create a new User

2. Search Users by Name or Roles

3. Search results

4. Edit a single User


Users in OpenMRS need to be associated with Persons. You either need to create a new Person, or attach the user account to an existing one.

![](http://write.flossmanuals.net/openmrs/user-management-and-access-control/static/add_user.png)

In both cases you will be taken to the sameAdd/Edit Userscreen. \(If you selected an existing person, the fields in theDemographic Infosection will be filled out for you.\)

![](http://write.flossmanuals.net/openmrs/user-management-and-access-control/static/add_edit_user.png)



## Managing Providers

For every Encounter you must enter one or moreProviders, the person who provided the care or services. Forms usually include a dropdown box to select a provider.

The system administrator must explicitly identify Providers. This is done throughAdministration &gt; Providers &gt; Manage Providers.

There are two kinds of providers. In OpenMRS 1.8 and earlier, a provider had to be associated with a user or, less often, a patient. The administrator had to create a user, and then search for them with the Person dropdown box. This is most useful when a provider has a user login. 

At many OpenMRS sites, only a few users log into the system. Often, treatment notes are entered by data clerks after an encounter, and clinicians never log in. Perhaps there are hundreds of providers who volunteer at the clinic only briefly. From OpenMRS 1.9 on, these providers can be entered as a name, and a user login is not required.

For system security, patient privacy, and ease of maintenance, it's best to enter providers only as a Provider Name when possible. You should create a user if the provider needs to log in or be given special permissions through a role. You can assign a user to a provider at a later time if it becomes necessary.

To create a Provider, go toAdmin &gt; Manage Providersand clickAdd Provider.

![](http://write.flossmanuals.net/openmrs/user-management-and-access-control/static/managing_users_add_provider.png)

The identifier is a unique word or number that you provide.  It's recommended that you create identifiers in a way that's simple and easy, such as using the provider's last name and first name.

Next, decide if this provider will be associated with a Person, or only be entered as a provider name.  If you choose the Person style, you must have already created a User for them. Begin typing their name in the Person field, and select them from the auto-complete list of matching users. For a Provider who is simply a Provider Name, enter their name in the Provider Name field.  

Click Save to save the provider. 

