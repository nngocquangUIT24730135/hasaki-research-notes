Chapter 1: Introduction to BPM
Contents
1. Processes Everywhere
2. Ingredients of a Business Process
3. Origins and History of BPM
1. The Functional Organization
2. The Birth of Process Thinking
3. The Rise and Fall of BPR
4. The BPM Lifecycle
5. Recap
SEITE 1

Chapter Overview
▪ Business Process Management (BPM) is the art and science of overseeing how work is
performed in an organization to ensure consistent outcomes and to take advantage of
improvement opportunities.
▪ The term “improvement” may take different meanings depending on the objectives of the
organization, e.g. reducing costs, reducing execution times, and reducing error rates, but also
gaining competitive advantage through innovation.
▪ Improvement initiatives are one-off or continuous; incremental or radical.
▪ BPM is about managing processes, i.e. entire chains of events, activities, and decisions.
▪ In this chapter, we describe typical processes that are found in contemporary organizations.
▪ We provide a definition of business process and BPM.
▪ We then provide a historical overview of the BPM discipline.
▪ Finally, we discuss the BPM lifecycle, around which the book is structured.
SLIDE 2

Chapter 1: Introduction to BPM
Contents
1. Processes Everywhere
2. Ingredients of a Business Process
3. Origins and History of BPM
1. The Functional Organization
2. The Birth of Process Thinking
3. The Rise and Fall of BPR
4. The BPM Lifecycle
5. Recap
SEITE 3

Examples of Processes in Many Organizations
▪ Order-to-Cash
▪ Quote-to-Order
▪ Procure-to-Pay
▪ Issue-to-Resolution
▪ Application-to-Approval
SLIDE 4

Example: Construction Company BuildIT
Construction Site of WU Vienna‘s New Campus opened in 2013.
Source: Wikimedia Commons

Equipment Rental Process at BuildIT
▪ BuildIT is a construction company specialized in public works, such as roads, bridges,
pipelines, tunnels and railroads. Within BuildIT, it often happens that engineers working at a
construction site (called site engineers) need a piece of equipment, such as a truck, an
excavator, a bulldozer, a water pump, etc. BuildIT owns very little equipment and instead it
rents most of its equipment from specialized suppliers.
▪ The existing business process for renting equipment goes as follows. When site engineers
need to rent a piece of equipment, they fill in a form called “Equipment Rental Request” and
send this request by email to one of the clerks at the company’s depot. The clerk at the depot
receives the request and, after consulting the catalogs of the equipment suppliers, selects the
most cost-effective equipment that complies with the request. Next, the clerk checks the
availability of the selected equipment with the supplier via phone or email. Sometimes the
selected option is not available. In these cases, the clerk has to select an alternative piece of
equipment and check its availability with the corresponding supplier.
▪ After finding a suitable and available piece of equipment, the clerk adds the details of the
selected equipment to the rental request. Each rental request has to be approved by a works
engineer, who also works at the depot. In some cases, the works engineer rejects the
equipment rental request. Some rejections lead to the cancelation of the request, i.e., no
equipment is rented at all. Other rejections are resolved by replacing the selected equipment
with another equipment – such as a cheaper piece of equipment or a more appropriate piece of
equipment for the job. In this latter case, the clerk needs to lodge another availability request.

Equipment Rental Process at BuildIT
▪ When a works engineer approves a rental request, the clerk sends a confirmation to the
supplier. This confirmation includes a Purchase Order (PO) for renting the equipment. The PO
is produced by BuildIT’s financial information system using information entered by the clerk.
The clerk also records the equipment rental in a spreadsheet that is used to monitor rentals.
▪ In the meantime, the site engineer may decide that the equipment is no longer needed. In this
case, the engineer asks the clerk to cancel the request for renting the equipment.
▪ In due time, the supplier delivers the rented equipment to the construction site. The site
engineer then inspects the equipment. If everything is in order, the site engineer accepts the
engagement and the equipment is put into use. In some cases, the equipment is sent back
because it does not comply with the requirements of the site engineer. In this case, the site
engineer has to start the rental process all over again.
▪ When the rental period expires, the supplier comes to pick up the equipment. Sometimes, the
site engineer asks for an extension of the rental period by contacting the supplier via email or
phone one to two days before pick-up. The supplier may accept or reject this request.
▪ A few days after the equipment is picked up, the supplier sends an invoice to the clerk by email.
At this point, the clerk asks the site engineer to confirm that the equipment was indeed rented
for the period indicated in the invoice. The clerk also checks if the rental prices indicated in the
invoice are in accordance with those in the PO. After these checks, the clerk forwards the
invoice to the financial department. The financial department eventually pays the invoice.

Chapter 1: Introduction to BPM
Contents
1. Processes Everywhere
2. Ingredients of a Business Process
3. Origins and History of BPM
1. The Functional Organization
2. The Birth of Process Thinking
3. The Rise and Fall of BPR
4. The BPM Lifecycle
5. Recap
SEITE 8

Definition of Business Process
A business process as a collection of inter-related
events, activities, and decision points that involve
a number of actors and objects, which collectively
lead to an outcome that is of value to at least one
customer.
SLIDE 9

Ingredients of a Business Process
SLIDE 10

Exercise 1.1: University Admission Process
WU Vienna‘s New Campus opened in 2013. Source: Wikimedia Commons

Exercise 1.1: University Admission Process
▪ Consider the process for the admission of international graduate students at a university.
▪ In order to apply for admission, students first fill in an online form. Online applications are
recorded in an information system to which all staff members involved in the admissions
process have access. After a student has submitted the online form, a PDF document is
generated and the student is requested to download it, sign it, and send it by post together with
the required documents, which include:
▪ certified copies of previous degree and academic transcripts,
▪ results of English language test,
▪ curriculum vitae,
▪ two reference letters.

Exercise 1.1: University Admission Process
▪ When these documents are received by the admissions office, an officer checks the
completeness of the documents. If any document is missing, an email is sent to the student.
The student has to send the missing documents by post. Assuming the application is complete,
the admissions office sends the certified copies of the degrees to an academic recognition
agency, which checks the degrees and gives an assessment of their validity and equivalence in
terms of local education standards. This agency requires that all documents be sent to it by
post, and that all documents be certified copies of the originals. The agency sends back its
assessment to the university by post as well. Assuming the degree verification is successful,
the English language test results are then checked online by an officer at the admissions office.
If the validity of the English language test results cannot be verified, the application is rejected
(such notifications of rejection are sent by email).

Exercise 1.1: University Admission Process
▪ Once all documents of a given student have been validated, the admissions office forwards
these documents by internal mail to the corresponding academic committee responsible for
deciding whether to offer admission or not. The committee makes its decision based on the
academic degrees and transcripts, the CV, and the reference letters. The committee meets
once every three months to examine all applications that are ready for academic assessment at
the time of the meeting.
▪ At the end of the committee meeting, the chair of the committee notifies the admissions office
of the selection outcomes. This notification includes a list of admitted and rejected candidates.
A few days later, the admissions office notifies the outcome to each candidate via email.
Additionally, successful candidates are sent a confirmation letter by post.
▪ With respect to the above process, consider the following questions:
1. Who are the actors in this process?
2. Which actors can be considered as customers in this process?
3. What value does the process deliver to its customers?
4. What are the possible outcomes of this process?

Definition of Business Process Management
BPM as a body of methods, techniques, and tools
to identify, discover, analyze, redesign, execute,
and monitor business processes in order to
optimize their performance.
SLIDE 15

Related Disciplines
▪ Total Quality Management (TQM)
▪ Focus on continuously improving and sustaining the quality of products and
services.
▪ TQM puts emphasis on products and services themselves, while BPM focuses
on improvement of processes.
▪ Applications of TQM are primarily in manufacturing while BPM more in service
organizations.
▪ Operations Management
▪ Concerned with managing physical and technical functions of organization,
particularly those relating to production and manufacturing.
▪ Using probability theory, queuing theory, decision analysis, mathematical
modeling, and simulation for optimizing efficiency of operations.
▪ Such techniques are also useful in.
▪ Often concerned with controlling an existing process, while BPM making
changes to an existing process in order to improve it.
SLIDE 16

Related Disciplines
▪ Lean
▪ Originates from manufacturing, in particular Toyota Production System.
▪ Eliminates waste, i.e., activities that do not add value to the customer.
▪ BPM puts more emphasis on use of information technology as a tool to improve
business processes and to make them more consistent and repeatable.
▪ Six Sigma
▪ Originates from manufacturing, in particular from production practices at Motorola.
▪ Focuses on minimization of defects (errors).
▪ Strong emphasis on measuring output of processes, especially in terms of quality.
▪ Popular approach to blend Lean with Six Sigma, leading to Lean Six Sigma.
SLIDE 17

Chapter 1: Introduction to BPM
Contents
1. Processes Everywhere
2. Ingredients of a Business Process
3. Origins and History of BPM
1. The Functional Organization
2. The Birth of Process Thinking
3. The Rise and Fall of BPR
4. The BPM Lifecycle
5. Recap
SEITE 18

How process moved out of focus through ages
SLIDE 19

Adam Smith: Processes and Division of Labour
“To take an example, the trade of a pin-maker: But in the way in which this
business is now carried on, it is divided into a number of branches:
• One man draws out the wire; another straights it;
• a third cuts it; a fourth points it; a fifth grinds it at the
• top for receiving the head; to make the head requires
• three operations; to put it on is a peculiar business;
• to whiten the pins is another; to put them into the paper;
and the important business of making a pin is, in this
manner, divided into about eighteen distinct operations.”
Source: Smith 1776
Picture:
http://www.library.hbs.edu/hc/
collections/kress/kress_img/ada
m_smith2.htm
SEITE 20

Frederick W. Taylor: Scientific Management
▪ Meticulously studying labor activities
▪ Work instructions for workers
▪ Managers oversee the productivity of groups of workers
▪ Units and their managers were structured hierarchically
▪ Functional organization remains dominant until the end of 1980s.
Source: Wikimedia Commons
SLIDE 21

Birth of Process Thinking:
Business Process Reengineering (BPR)
SLIDE 22

Purchasing process at Ford at the initial stage
SLIDE 23

Purchasing process at Ford after redesign
SLIDE 24

Exercise 1.2: Purchasing process at Ford
Consider the purchasing process at Ford.
1. Who are the actors in this process?
2. Which actors can be considered as customers in this process?
3. What value does the process deliver to its customers?
4. What are the possible outcomes of this process?
SLIDE 25

The Rise and Fall of BPR
1. Concept misuse:
▪ Projects were labeled BPR, even when business processes were not the core.
▪ Many corporations initiated reductions of workforce, often packaged as process
redesign projects, which triggered resentment.
2. Over-radicalism:
▪ Hammer’s early papers states: “Don’t Automate, Obliterate”.
▪ Many situations require a much more gradual (incremental) approach.
3. Support immaturity:
▪ Necessary tools and technologies were not yet available or insufficient.
▪ Much process logic had to be hard-coded in IT applications of the time.
▪ People grew frustrated when they noted that their efforts on redesigning a
process were thwarted by a rigid infrastructure.
SLIDE 26

Reshaping Process Thinking
Process Orientation is productive ERP Systems penetrate the market
SLIDE 27

Job Functions of Process Owner
SLIDE 28

Chapter 1: Introduction to BPM
Contents
1. Processes Everywhere
2. Ingredients of a Business Process
3. Origins and History of BPM
1. The Functional Organization
2. The Birth of Process Thinking
3. The Rise and Fall of BPR
4. The BPM Lifecycle
5. Recap
SEITE 29

Establishing Process Thinking in Organizations
▪ Establish BPM Team
▪ Describe Process Architecture
▪ Define Process Performance Measures
▪ Discover and Model Processes
▪ Analyze, Redesign, Implement and Monitor Processes
▪ Make Use of Process-Aware Information Systems
SLIDE 30

Example: Process model for the initial
fragment of the equipment rental process
SLIDE 31

Exercises 1.3-5: University Admission Process
WU Vienna‘s New Campus opened in 2013. Source: Wikimedia Commons

Exercises 1.3-5: University Admission Process
Consider the student admission process described in Exercise 1.1 (page 5).
▪ Exercise 1.3: Taking the perspective of the customer, identify at least two
performance measures that can be attached to this process.
▪ Exercise 1.4: Taking the perspective of the customer, think of at least two issues
that this process might have.
▪ Exercise 1.5: What possible changes do you think could be made to this process in
order to address these issues?
SLIDE 33

The BPM Lifecycle
|     |     |     |     |     | P r o c e s s   |     | Management Processes                      |             |
| --- | --- | --- | --- | --- | --------------- | --- | ----------------------------------------- | ----------- |
|     |     |     |     |     |                 |     | Define Vision Develop Strategy Implement  | Manage Risk |
Strategy
|     |     |     |     |     | id e n t if ic a t io n |     |     |     |
| --- | --- | --- | --- | --- | ----------------------- | --- | --- | --- |
Examples for BPM lifecycle and process mining Core Processes
|          |                |        |                      |                 |                  |                             | Pr o cu r e P r o c u r e M a r ke t         | D e liv e r   M a n a g e                     |
| -------- | -------------- | ------ | -------------------- | --------------- | ---------------- | --------------------------- | -------------------------------------------- | --------------------------------------------- |
|          |                |        |                      |                 |                  |                             | M a te ri a ls P r o d u c t s P ro d u ct s | P ro d u c ts C S u e s t r o v i m c e e r   |
|          | 35h B 30h      |        |                      |                 |                  |                             | Support Processes                            |                                               |
|          |                |        |                      |                 | P r o c e        | s s  a r c h it e c t u r e |                                              |                                               |
|          | 15h            |        |                      |                 |                  |                             | Manage Personnel Information  Manage         | Manage Assets                                 |
| A        |                | D      | E                    |                 |                  |                             |                                              |                                               |
| 5m 3m 5m | 10m            | 30m 2h | 10m                  |                 |                  |                             |                                              |                                               |
|          | C              |        | C o n fo r m a       | n c e  a n  d   | P r o c e s s    |                             |                                              |                                               |
|          |                |        |                      |                 |                  | A s -ism                    |  po rd o c e s s                             |                                               |
|          | 15m 1.5h 10min |        | p e r fo r m         | a n c e         |                  |                             |                                              |                                               |
|          |                |        |                      |                 | d is c o v e r y |                             | e l                                          |                                               |
|          |                |        | in s ig h            | t s             |                  |                             |                                              |                                               |
|          | A B            | C      | D E                  |                 |                  |                             |                                              |                                               |
|          |                |        | P r o c e s          | s               |                  |                             | Pa rn o c e s s                              |                                               |
|          |                |        | m o n it o r         | in g            |                  |                             | a ly s is                                    |                                               |
|          |                |        |                      |                 |                  |                             | In s ig h t s  o n                           |                                               |
|          |                |        | E x e c u t a b le   |                 |                  |                             |                                              |                                               |
|          |                |        |                      |                 |                  |                             | w e a k n e s s e s  a nt d                  |                                               |
|          |                |        | p r o c e s s        |                 |                  |                             |                                              |                                               |
|          |                |        |                      |                 |                  |                             | t h e ir  im p a c                           |                                               |
m o d e l
|     |     |     |     | P rm o ce en st sa |     | P r o c e s s  |     |     |
| --- | --- | --- | --- | ------------------ | --- | -------------- | --- | --- |
|     |     |     | im  | p le t io n        |     | r e d e s ig n |     |     |
T o -b e  p r o c e s s
m o d e l
SEITE 34

Stakeholders in the BPM Lifecycle
▪ Management Team: ▪ Process Owners:
▪ Chief Executive Officer (CEO) responsible for ▪ Process owner is responsible for efficient and
overall business success. effective operation of a given process, including
▪ Chief Operations Officer (COO) responsible for ▪ Planning and organizing, i.e. defining performance
defining the way operations are set up, sometimes measures and objectives as well as initiating and
Chief Process Officer (CPO) or Chief Process and leading improvement projects.
Innovation Officer (CPIO).
▪ Monitoring, i.e. ensuring that performance
▪ Chief Information Officer (CIO) responsible for objectives are met, and taking corrective actions.
operation of information system infrastructure.
▪ Process owner is involved in process modeling,
▪ Chief Financial Officer (CFO) responsible for analysis, redesign, implementation, and
overall financial performance of the company. monitoring.
▪ Human Resources (HR) director plays key role in
processes that involve many process participants.
SLIDE 35

Stakeholders in the BPM Lifecycle
▪ Process Participants: ▪ Process Methodologist:
▪ Perform activities of business process on day-to- ▪ Provides advice on methods, techniques and
day basis. software tools.
▪ Conduct routine work according to the standards ▪ Coordinates technical training.
and guidelines of the company.
▪ System Engineers:
▪ Coordinated by process owner, who is responsible
▪ Translate requirements into system design
for non-routine aspects of process.
▪ Responsible for implementation, testing and
▪ Involved as domain experts during process
deployment.
discovery and process analysis.
▪ BPM Group (also BPM Center of Excellence):
▪ Support redesign activities and implementation.
▪ Responsible for preserving project knowledge and
▪ Process Analysts:
documentation.
▪ Conduct process identification, discovery, analysis,
▪ Maintain process architecture.
and redesign.
▪ Prioritize process redesign projects.
▪ Coordinate implementation and monitoring.
▪ Align the BPM efforts with strategic goals.
▪ Report to management and process owners
▪ Most common in large organizations with several
▪ Have business or IT background.
years of BPM experience.
SLIDE 36

Chapter 1: Introduction to BPM
Contents
1. Processes Everywhere
2. Ingredients of a Business Process
3. Origins and History of BPM
1. The Functional Organization
2. The Birth of Process Thinking
3. The Rise and Fall of BPR
4. The BPM Lifecycle
4. Recap
SEITE 37

Recap
▪ A process is a collection of events, activities, and decisions that collectively lead to
an outcome that brings value to an organization’s customers.
▪ Every organization has processes.
▪ Managing processes ensures that they produce value.
▪ BPM is a body of principles, methods, and tools to design, analyze, execute, and
monitor business processes.
▪ Process models and performance measures are pillars for managing processes.
▪ Various related disciplines complement BPM, such as Lean, Six Sigma, and Total
Quality Management.
SLIDE 38