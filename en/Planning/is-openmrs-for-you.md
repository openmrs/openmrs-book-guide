# Example: Amani Clinic

We assume if you're reading this book that you're interested in deploying OpenMRS to support clinical care in the real world. To bridge the divide between theory and practice, and to illustrate the sometimes challenging process of deploying a large health-care information system, we have used the example of the fictional Amani Clinic as a case study throughout this book.

![](http://write.flossmanuals.net/openmrs/example-amani-clinic/static/case-study.png)

Every time you see this image in the book, you will learn how Amani Clinic used the information discussed to plan and implement OpenMRS.

While a single example could never possibly capture all the complexity of the many different contexts in which OpenMRS might be used, we hope it will serve as inspiration to think about how your environment may be similar or different. We also hope that as you read, you will start to consider the questions you need to ask to begin to design and implement your own installation of OpenMRS.

## About the Amani Clinic

![](http://write.flossmanuals.net/openmrs/example-amani-clinic/static/clinic.png)

Kisiizi is a small town in southwest Uganda, over 40 kilometers from the nearest large city. Much of the fame of Kisiizi is based on its hydroelectric power generating station and its relatively large hospital, which handles most of the health care for the region.

Just over two years ago, a European-based NGO provided funding to help launch a new health care facility we'll call "Amani Clinic" in the town. This clinic was opened specifically to address the need for maternal and child health \(MCH\) care in Kisiizi and the surrounding areas.

Since its opening, the clinic has been very successful in establishing itself, and has attracted a full staff of doctors, nurses, and assistants. New patients, both pregnant women and new mothers, are continually being registered in the clinic, but there is very little information available about the efficacy of the work in the clinic, or the outcomes for its patients. Therefore, the funding agency has requested that the clinic work to implement an information system, to help better monitor and evaluate the health care outcomes of the patients over time, and to help the clinic scale up to see more patients more efficiently. The agency recommended that the clinic consider using OpenMRS, which had been successfully used by other projects funded by that agency in other countries.

The funding model provided for some information and communication technology \(ICT\) infrastructure to get the project started, as well as for some staffing support. However, deciding how to allocate this money was left up to the clinic's local management. After receiving the grant funding, the director of the site hired Claudine, a graduate of a medical informatics training program in neighboring Rwanda, to help lead the effort. This newly-hired informatics manager, in turn, hired Daniel, recent university graduate from Kampala with expertise in ICT infrastructure and system administration.

Since the clinic was opened, doctors and nurses have used paper forms to collect data about their patients. These forms are stored in folders and kept in a locked file room until a patient's appointment. When the patients arrive, they are given their folder to carry with them as they talk with the various health care providers they will see during their visit. Each of these providers completes the relevant paper forms to add information about the visit. The forms are added to the patient's folder, which is returned at the end of their visit.

Clinical staff were concerned when they heard about the upcoming deployment of OpenMRC, because of the possibility of changes to the way they are used to working. However, the informatics manager has assured them that they can continue to use the familiar paper forms. When a patient arrives at the clinic, they will be registered by a patient registration clerk. After the patient's visit is complete, a data entry clerk will enter the information from that visit into OpenMRS.

Many people in Kisiizi have basic ICT skills, and there is a local Internet cafe, supported by an NGO that provides basic ICT training to local residents. Two recent students have been hired as the first patient registration and data entry clerks for the clinic.

Meanwhile, the system administrator has finished his preparation work and has deployed a basic local area network \(LAN\) to connect a server that will host the OpenMRS application to PCs in the file room, in the clinic manager's office, and in the ICT room. The LAN is connected to the Internet, although the connection isn't very fast and often goes offline. The server is powered by an uninterruptible power supply \(UPS\), that will ensure it stays running despite any fluctuations in the local power grid.

Through the rest of this book, you will follow the progress of the people at the Amani Clinic as they install OpenMRS, customize it to fit the needs of their clinic, and use OpenMRS from day to day, first to enter data and then to extract it for patient visits and for reporting to their funding agency on an ongoing basis.

