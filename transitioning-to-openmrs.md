# Transitioning to OpenMRS

![](http://write.flossmanuals.net/openmrs/transitioning-to-openmrs/static/transitioning.png)

_A paper-based patient register book at an African OpenMRS clinic._

This chapter outlines steps that typically make up a OpenMRS project, and should be read by people about to embark on a OpenMRS implementation. Some of this information may be obvious to experienced project managers. A comprehensive guide to project management is beyond the scope of this book, but we have included some high-level process considerations to get you started thinking about what needs to happen.

We recommend you try to build a structured implementation process. It's important to plan carefully--the decisions you make during this process require substantial investments of resources, and you will be living with your choices for the foreseeable future.

When you start out on a new OpenMRS project, you should spend time thinking about \(at minimum\):

* Which people will be involved in the project

* Business goals of using OpenMRS

* How you will approach the initial configuration

* What ongoing support you will need

* Costs associated with ICT infrastructure

* Training and documentation

* Change management


## People and the project team

Your project implementation team should include clinic staff:

1. **Management** are aware of funding obligations and third party reporting requirements.

2. **Health care providers** are focused on improving patient care.

3. **Administrative staff** are specialists of workflow issues and clinic processes.


The team could also include the following people that may or may not be from the clinic:

1. A **system administrator** is in charge of installing and maintaining OpenMRS inside of the clinic's ICT infrastructure.

2. **Medical informatics expert\(s\)** create clinical documentation and ensure that data is managed properly in the system. Develop reports.

3. \(Optional\) A **project manager or coordinator**. For larger implementations, this person works to hold people accountable to finishing their work in a timely manner, and ensures the project is on track.

4. \(Optional\) **Software developers** may be needed for locations that decide to customize the system.


It is very important to include clinical staff \(for example nurses, data entry clerks, and others\) in your implementation team from the earliest phases of the project so that the resulting deployment is useful for them and easy for them to use.

Managing an OpenMRS project will require a major time investment from people within your organization, even if you employ an external consultant. Organizations often underestimate the amount of time that will be required from their staff in implementing an enterprise ICT project. This time investment includes items such as training, modifying existing processes, and providing new or updated information to relevant people. Deploying OpenMRS is no different. It's not something that can be added to the end of an already busy schedule, and we urge you to keep this in mind and take it into consideration when planning.

## Goals

By this point in the project, you should have a good idea of what indicates a successful OpenMRS implementation for your clinic. This could be something like reducing time to prepare month-end reports by 50%, or increasing antiretroviral treatment \(ART\) in HIV-infected pregnant women by 25%. Your goals should be specific, measurable, attainable, relevant, timely--or SMART.

These goals will help you in directing and managing your project. For example, if the project group wants some customization that requires budget and effort, your overall goals will help you decide whether or not to consider that customization. Your goals will help you to focus on why you are implementing OpenMRS and what you want to achieve in the long run.

## Incremental adoption

It often makes sense to divide the implementation process into smaller, more manageable sections, which can be implemented in discrete stages or iterations. Implementing in stages allows people to get used to changes gradually without feeling overwhelmed, and allows your implementation team to be responsive to feedback from users during the process.

Another reason people choose to develop iteratively is that it is very hard for users to correctly or fully explain their requirements at the beginning of the project. Giving people hands-on experience of an early version of the system helps them understand how it works and what might be possible. They can then provide you with valuable feedback, and they might identify new requirements.

![](http://write.flossmanuals.net/openmrs/transitioning-to-openmrs/static/case-study.png)

The Amani Clinic chose to introduce change iteratively. First they started using the system for patient registration. This affected only the administrative staff without impacting the clinical staff. Later they started doing retrospective data entry, which included paper forms for clinicians that had minor changes, as well as training a new data entry clerk.

### Pilot projects

Larger multi-site implementations may wish to develop a pilot approach to help reduce risk. In this scenario, you would only deploy OpenMRS at one site and learn about the process in a more controlled way. You can then incorporate what you've learned into a coordinated implementation process for other sites.

## Ongoing support and development

It is a mistake to think about an OpenMRS project as a one-off installation that will meet the needs of your organization for the foreseeable future. Organizations are always changing and evolving. Your medical record system should evolve with you, otherwise it will eventually become out of sync with the organization.

Once you have been using OpenMRS for a while and staff are comfortable with it, you will likely want to take advantage of additional functionality. Each improvement or new piece of functionality you decide to implement in OpenMRS will take resources, so you will want to plan ahead for these.

Even if your organizational needs don't change, you need to plan for ongoing support of OpenMRS, including:

* Keeping your system up-to-date with security patches

* Upgrading to the latest version of OpenMRS \(not always necessary, but OpenMRS is continually improving usability and adding functionality\)

* Upgrading the modules you use to fix bugs and improve features

* Maintenance of your server and network infrastructure


For more information, see the "Maintenance" chapter.

## Training

Training is also an important part of any OpenMRS implementation project. Your training could take many forms depending on the needs of your users, but it often makes sense to spend resources \(e.g., time and money\) on formal and reusable training resources such as user guides, lesson plans, and other materials.

Trying to cover everything in one training session probably won't be effective. People will want and need time to digest the new ideas they learn and use them in their daily work, and you must anticipate staff turnover. Instead, consider holding smaller training sessions that introduce concepts and specific functionality, followed by periods of testing, piloting and feedback. Customize your training for your audience--not everyone needs to sit through a two-hour training session on data entry if only a single person is responsible for this role. When possible, train people to become trainers. This increases peoples' sense of ownership in your OpenMRS implementation, and helps people to better remember what they learn.

Training is an ongoing process. New employees will need to be trained when they start, and people familiar with the system can benefit from learning about more advanced topics. People may need further training when there are significant upgrades or new functionality is added to OpenMRS.

## Change management

Introducing an electronic medical record system will cause changes in workflow and processes at your organization. These changes may be "political" and cause challenges in your organization, or they may be more practical and technical changes. Either way, too much change at the same time is often difficult and stressful.

To help, give people time to accept and support each change so that they share in ownership of the new system, rather than feeling as if something has been forced on them. Focus on simple tasks at the beginning of deployment and introduce more difficult tasks as people start to better understand OpenMRS. Show staff how the new system will make their work easier and where their feedback has been incorporated.

Good planning can minimize the risks around change, but it is important to be flexible within your plan. Unforeseen things often occur, and a plan that is too rigid could prevent you from reaching the best solution.

