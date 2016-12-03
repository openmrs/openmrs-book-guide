# A Brief History

![](http://write.flossmanuals.net/openmrs/a-brief-history/static/AMPATH-2004.png)

_One of OpenMRS's birthplaces--Moi University Teaching and Referral Hospital, Eldoret, Kenya \(2004\)_

Throughout the 1990s, an academic partnership flourished between Indiana University School of Medicine in the United States and Moi University in Eldoret, Kenya, providing Kenyan medical students with access to health care training. This program continued to grow for several years until a severe outbreak of HIV/AIDS in Western Kenya caused the program to rethink its goals, at which point the Academic Model for Prevention and Treatment of HIV/AIDS \(AMPATH\) was created. The number of patients in Kenya continued to grow, and basic IT systems including Microsoft Access were used to monitor patient care.

In February 2004, the amount of data had become too large for AMPATH's existing systems, so their medical director invited Burke Mamlin, from the Regenstrief Institute in Indianapolis, United States, to visit the site and evaluate how improvements in medical informatics technology could improve AMPATH's data management. Regenstrief had long been recognized as a leader in medical informatics research, and Burke brought his colleague Paul Biondich along with him on the visit to Kenya. It quickly became apparent that a new system was needed. Paul and Burke began to design the data model for a new medical records system for AMPATH, which would go on to become OpenMRS.

At the same time, a Boston-based non-profit named Partners In Health \(PIH\) was pioneering the use of web-based EMRs in developing countries. They had built the PIH-EMR, which they were using to support the treatment of multi-drug resistant tuberculosis in Peru and HIV in Haiti. But Hamish Fraser, PIH's director of the EMR project, was worried: PIH was about to expand into Rwanda, Lesotho, and Malawi, and he feared it would be difficult to maintain their home-built system in 5 countries.

In September 2004, Paul and Burke met Hamish at the World Congress on Medical and Health Informatics \(MedInfo\) conference in San Francisco. It became apparent that the three shared similar goals and needs, so they agreed to work collaboratively to develop a system that would be suitable for the various needs of humanitarian work in African nations and beyond.

Paul and Burke hired developer Ben Wolfe to begin work on programming an early prototype of OpenMRS, based on their previous work at AMPATH and Regenstrief. Several months later, PIH's lead developer Darius Jazayeri joined the project, merging PIH-EMR's functionality into the new system. The previous systems at AMPATH focused on data entry, while at PIH, the focus was more on clinical workflow. The new system combined features of both the AMPATH and PIH systems.

Because of the strong cooperation between PIH and Regenstrief and the long distances involved, it became clear that an open source software model of development was the best way to sustain and grow the platform, and the OpenMRS project was born.

While the collaboration between Regenstrief and PIH continued and the new system was being designed, the groups were looking for additional support in Africa. They turned to their colleague Chris Seebregts, from the South African Medical Research Council \(MRC\). Chris was already heavily involved in the field of medical informatics throughout sub-Saharan Africa, and brought with him a wealth of knowledge about the needs of informatics implementations. Seebregts had been adapting OpenMRS for use in South Africa and started to build up a community of implementers of the software around the world. His work led to massive growth of the OpenMRS community \(now nearly 2,000 strong as of late 2011\). In February 2006, AMPATH launched OpenMRS in Kenya, and PIH brought it to Rwinkwavu, Rwanda, in August of the same year. The South African MRC first switched on the system at Richmond Hospital in KwaZulu-Natal at the end of 2006.

As both the OpenMRS application and open source community grew, they gathered the attention of many other large projects and agencies. Some of these have extended both financial and consulting support over the past several years, including:

* The United States Center for Disease Control \(CDC\)

* The United States Center for Disease Control \(CDC\)

* Canada's International Development Research Centre \(IDRC\)

* National Institutes of Health Fogarty International Centre


* The Millennium Villages Project of the Earth Institute, Columbia University

* The Rockefeller Foundation

* World Health Organization


In an effort to broaden participation in the project around the world, OpenMRS began participating in the Google Summer of Code \(GSoC\) program in 2007. GSoC provides university students who wish to participate in open source development projects with a stipend and a close mentoring relationship with an experienced project team member. Participation in the program has continued since then--OpenMRS is now one of the larger open source projects in the program, boasting a large class of alumni, a number of whom continue to contribute to the project. Many of these alumni come from the developing world, and some have gone on to successful software development careers.

![](http://write.flossmanuals.net/openmrs/a-brief-history/static/implmenters-early.png)

_Any early gathering of OpenMRS implementers and developers in Cape Town, South Africa._

One of the aims of the OpenMRS community is to help build local capacity in the places where it is used. To that end, participants in the community are encouraged to develop programs and processes that encourage entrepreneurship and the creation of partnerships to grow the field of medical informatics, particularly in the developing world. For example, in Kigali, Rwanda, Partners In Health jump-started a local training program known as E-Health Software Development and Implementation \(EHSDI\). This 9-month course conducted in partnership with the Rwanda Development Board and the Kigali Institute of Science and Technology \(KIST\) was designed to teach students to develop medical information systems. It includes extensive training in using the OpenMRS platform.

The number of individual and organizational volunteers who participate in the OpenMRS community has continued to grow, tripling in size between 2010 and 2011. These individuals participate in various ways, from documentation and bug reports, from training and providing support to other community members. The release of OpenMRS 1.8 was made possible by the assistance of over 50 contributors.

Further, collaborations with other open source software organizations such as Open Data Kit and Pentaho have produced volunteer contributions to OpenMRS, and commercial consulting organizations such as ThoughtWorks Inc. have contributed many hours to developing and improving OpenMRS.

At the close of 2011, the OpenMRS community is preparing to launch an independent not-for-profit organization to help support the project's needs as it grows. The goal of this organization will be to provide technical infrastructure and community management, to assist collaboration and cooperation of project volunteers throughout the world, and to provide training and support to those who seek to implement OpenMRS as a key part of a medical informatics strategy in clinics, hospitals, and government health organizations.

From its humble beginnings as a solution to a problem in a small African town, OpenMRS has become the largest open source health care project on the planet. Between 2006 and 2011, OpenMRS at AMPATH in Kenya has recorded over 111,000,000 points of data for over 180,000 patients, helping to save many thousands of lives. Every day, similar stories are retold somewhere else around the world with the assistance of thousands of volunteers. The OpenMRS community continues to grow, and we are excited that you're interesting in joining us. Regardless of your background or interests, there is a way for you to both contribute and gain from the work of others in the OpenMRS community.

### What's New in Version 1.9

This version of OpenMRS includes a new concept,Visit. A visit is comprised of at least oneEncounter. Encounter has been redefined in this version as a transaction between a patient and at least one health care provider to provide service or assess a patient's health status.

**OpenMRS Attributes** now allows for implementation-specific customizations of certain types of OpenMRS data. In earlier releases, only Person could be customized. Now, you can also customize Provider, Visit, and Location data.  

**Concept Mapping** has been improved in this release, now allowing you to define how your system's concepts relate to external concepts and standards. 



