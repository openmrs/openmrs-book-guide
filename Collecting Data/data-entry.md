---
order: 60
---
# Data Entry

![](/assets/data-entry.png)

An electronic medical records system has many advantages compared to a traditional paper-based system. Data is collected using electronic forms, and a standard template means that each user sees the same structure, simplifying the representation of the underlying information structure and complexity. Electronic forms also allow for basic data validation.

An administrator must design the form templates that data clerks will use. There are three forms modules in OpenMRS.  An OpenMRS installation may use more than one style, but for simplicity, it's recommended you begin with one.  They are compared below.

<table>
  <tbody>
    <tr>
      <th>Form Type</th>
      <th>Advantages</th>
      <th>Disadvantages</th>
    </tr>
    <tr>
      <td>HTML Forms</td>
      <td>
        <ul>
          <li>Easy to use</li>
          <li>Ongoing development of new features</li>
          <li>Supports complex logic operations</li>
          <li>Extendable</li>
          <li>Allows review of forms after submission</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>Requires HTML knowledge</li>
          <li>Not supported on mobile devices</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>XForms</td>
      <td>
        <ul>
          <li>Open source</li>
          <li>Easy to use</li>
          <li>Works well on mobile devices</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>Does not support some complex logic operations</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>InfoPath</td>
      <td>
        <ul>
          <li>Original approach to data entry via forms</li>
          <li>Others may already be familiar with the technology</li>
        </ul>
      </td>
      <td>
         <ul>
          <li>Not open source</li>
          <li>Runs only on Windows</li>
          <li>Requires payment of license fees</li>
          <li>No new development by the OpenMRS team</li>
        </ul>
</td>
    </tr>
  </tbody>
</table>


The next chapters describe HTML Form Entry and XForms in more detail.

InfoPath forms, created with the FormEntry module and Microsoft InfoPath, are not recommended.  Microsoft InfoPath is proprietary software, and the forms are difficult to troubleshoot.  InfoPath forms will continue to work, but there will be no new development.

