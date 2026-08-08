Chapter 2: Process Identification
Contents
1. The Context of Process Identification
2. Definition of the Process Architecture
1. Process Categories
2. Relationships Between Processes
3. Reuse of Reference Models
4. Process Landscape Model
5. The Example of SAP’s Process Architecture
3. Process Selection
1. Selection Criteria
2. Process Performance Measures
3. Process Portfolio
4. Recap
SEITE 1

Process Identification in the BPM Lifecycle
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

Chapter Overview
▪ Process identification refers to systematically defining business processes of
organization and establishing criteria to select processes for improvement.
▪ Output is process architecture, which represents processes and interrelations.
▪ Process architecture serves as framework for defining priorities and scope of projects.
▪ First, we discuss the context of process identification.
▪ We present a method based on process architecture definition and process selection.
▪ Definition is concerned with listing initial set of processes and their architecture.
▪ Selection considers criteria for defining priorities of processes using a portfolio.
SLIDE 3

Chapter 2: Process Identification
Contents
1. The Context of Process Identification
2. Definition of the Process Architecture
1. Process Categories
2. Relationships Between Processes
3. Reuse of Reference Models
4. Process Landscape Model
5. The Example of SAP’s Process Architecture
3. Process Selection
1. Selection Criteria
2. Process Performance Measures
3. Process Portfolio
4. Recap
SEITE 4

Definition of Business Strategy
Business strategy is an organizational perspective on
setting and meeting business goals. (Mintzberg)
SLIDE 5

Balanced Scorecard (Kaplan & Norton)
Learning and
| Financial | Customer | Internal  |
| --------- | -------- | --------- |
Growth
| Perspective | Perspective | Perspective |
| ----------- | ----------- | ----------- |
Perspective
|     | Product/Service | Operations Management  |
| --- | --------------- | ---------------------- |
|     | Attributes      | Processes              |
Improve Cost
Culture
| Structure | Price |     |
| --------- | ----- | --- |
Supply Distribution
Production Risk Mgmt.
Quality
| Increase Asset  | Availability | Customer Management  |
| --------------- | ------------ | -------------------- |
| Utilization     |              | Processes            |
Selection
Leadership
Selection Retention
|     | Functionality | Acquisition Growth |
| --- | ------------- | ------------------ |
Long-Term
Shareholder
Value
Innovation
|     | Relationship | Processes |
| --- | ------------ | --------- |
Alignment
Service
Opportunity Design
Expand Revenue
Research Launch
| Opportunities | Partnership |     |
| ------------- | ----------- | --- |
Regulatory and Social
Processes
| Enhance  | Image |     |
| -------- | ----- | --- |
Teamwork
| Customer Value |     | Environment Employment |
| -------------- | --- | ---------------------- |
Brand
Safety/HealthCommunity
SLIDE 6

Enterprise Architecture according to TOGAF
▪ Organizational perspective:
actors, roles, and organizational structure.
▪ Product perspective:
products and services along with their relationships.
▪ Business process perspective:
process architecture.
▪ Data perspective:
informational entities and their relationships.
▪ Application perspective:
different pieces of software with their dependencies.
▪ Technical infrastructure:
computer hardware and communication networks.
SLIDE 7

Exercise 2.1: Construction Company BuildIT
Construction Sight of WU Vienna‘s New Campus opened in 2013.
Source: Wikimedia Commons

Exercise 2.1-2: Construction Company BuildIT
Consider the construction company BuildIT and its procure-to-pay process that is
described on page 2.
▪ To which category in the internal perspective of Figure 2.1 does this process belong?
▪ How does it influence different aspects of the customer perspective?
▪ How is it shaped by aspects of the learning and growth perspective?
▪ Which aspects in the organizational, product, data, application, and technical
infrastructure perspectives have to be described to understand this process?

Changes of Strategic Relevance: Mannesmann
19th century 20th century 1990
Sources: stahlseite.de, Copyright Uwe Niggemeier,
deutsches-telefon-museum.eu, ebay-
SLIDE 10
kleinanzeigen.de, wanne-eickel-historie.de

The Process Checklist
It may not be easy to decide on what to consider as a business process. A chunk of work
that is frequently repeated might not be a business process on its own. To prevent poor
scoping decisions, it is useful to consider the following process checklist:
▪ Is it a process at all? ▪ Is the process important enough to manage?
▪ It must be possible to identify main action, which is ▪ There is customer who is willing to pay for outcomes,
applied to a category of cases.
▪ Organization that carries out the process would be
▪ Name is of form verb + noun. willing to pay another party for taking over, or
▪ Can the process be controlled? ▪ Legal, mandatory framework compels an
organization to execute it.
▪ Repetitive series of events and activities to
execute individually observable cases. ▪ Is the scope of the process not too big?
▪ Without a clear case notion, process management ▪ 1:1 relation between initial event and activities.
is not feasible.
▪ Is the scope of the process not too small?
▪ Also, without any sense of repetition, a group of
▪ Rule of thumb: there should be at least three
business activities may better qualify as a project
different actors – excluding the customer – involved.
than as a business process.
▪ If there are no handoffs between multiple actors or
systems, there is little that can be improved using
BPM methods.
SLIDE 11

Chapter 2: Process Identification
Contents
1. The Context of Process Identification
2. Definition of the Process Architecture
1. Process Categories
2. Relationships Between Processes
3. Reuse of Reference Models
4. Process Landscape Model
5. The Example of SAP’s Process Architecture
3. Process Selection
1. Selection Criteria
2. Process Performance Measures
3. Process Portfolio
4. Recap
SEITE 12

Process Categories
Management Processes
| Define Vision | Develop Strategy |     | Implement  | Manage Risk |
| ------------- | ---------------- | --- | ---------- | ----------- |
Strategy
Core Processes
Manage
| Procure | Procure | Market | Deliver  |     |
| ------- | ------- | ------ | -------- | --- |
Customer
| Materials | Products | Products | Products |     |
| --------- | -------- | -------- | -------- | --- |
Service
Support Processes
Manage
| Manage Personnel |     | Information  |     | Manage Assets |
| ---------------- | --- | ------------ | --- | ------------- |
SLIDE 13

Exercise 2.3: University
WU Vienna‘s New Campus opened in 2013. Source: Wikimedia Commons

Exercise 2.3: University
▪ What are core, support, and management processes of a university?

Relationships between Processes
S e q u e n c e
M a n a g e  r
| P r | o c u r e | P r o c u rc ets | MP a r k e t | D e liv e r   |
| --- | --------- | ---------------- | ------------ | ------------- |
C u s t o m e
| M a | t e ria ls | P r o d u | r o d u c ts | P r o d u c ts |
| --- | ---------- | --------- | ------------ | -------------- |
S e r v ic e
| D e c o m p o | s itio n |              | S p e c ia liz a t | io n               |
| ------------- | -------- | ------------ | ------------------ | ------------------ |
|               | P        | r o c u r e  |                    | H a n d le  Jo b   |
|               | P        | r o d u c ts |                    | A p p lic a tio n  |
HA a n d le  Jo b   H a n d le  Jo b
|     | P r o c e s s | A s sP ea m b le   |     |     |
| --- | ------------- | ------------------ | --- | --- |
p p lic a tio n   A p p lic a tio n
|     | P a r ts | r ts |     |     |
| --- | -------- | ---- | --- | --- |
(A u s tr ia ) (G e r m a n y )
SLIDE 16

Exercise 2.4: Relationships
▪ Can you think of other types of relations that are useful to distinguish between
processes?
▪ Hint. Think about the purpose of identifying the relations between business
processes

Process Architecture
Generic Process Architecture British Telecom
|     |     | Meta |     | Model structure, methodology and  |     |     |
| --- | --- | ---- | --- | --------------------------------- | --- | --- |
modelling standards
| Level 1 |     | Level |     |     |                             |     |
| ------- | --- | ----- | --- | --- | --------------------------- | --- |
|         |     | s     |     |     | Defines business activities |     |
Process L e v e l  A le D is ti n g u is h e s   o p e r a tio na l  c u s t om er
|                      |                          | v         |     | orie n te                          | d  p r o c e s s e     | s  f r o m  m a n a g e m en t  |
| -------------------- | ------------------------ | --------- | --- | ---------------------------------- | ---------------------- | ------------------------------- |
|                      | Bu s in es s  Activities | e L       |     |                                    | and strategic process  |                                 |
| Landscape            |                          | s s       |     |                                    |                        |                                 |
|                      |                          | e         |     | Shows groups of related business   |                        |                                 |
|                      | Level B                  | n Logical |     |                                    |                        |                                 |
| (incl. Value Chains) |                          | is        |     | functions and standard end-to-end  |                        |                                 |
|                      | Process Groupings        | u Levels  |     | processes (e.g. Service Streams)   |                        |                                 |
B
|     | L e v e l  C | s   |     |     |     |     |
| --- | ------------ | --- | --- | --- | --- | --- |
Level 2 le C o re   p ro c e s s e s   t h a t  c o m b in e   t o g e t h e r   to
|     |                     | v   |     | d e li v e r  S | e r v ic e   S t r e | a m s   a n d   o t h e r   e n d - |
| --- | ------------------- | --- | --- | --------------- | -------------------- | ----------------------------------- |
|     | Co re  P r o cesses | e   |     |                 |                      | to - e n d   p r o c e s s e s      |
L
| Business Processes |         | s   |     |                                       |     |     |
| ------------------ | ------- | --- | --- | ------------------------------------- | --- | --- |
|                    | Level D | s   |     | Decomposition of core processes into  |     |     |
e c
| (e.g. BPMN) |                                | o    |             | detailed ‘success mo |                        | d e l ’  b u s i n e s s                |
| ----------- | ------------------------------ | ---- | ----------- | -------------------- | ---------------------- | --------------------------------------- |
|             | Business Process Flows         | rP   |             |                      |                        | p r o c e s s   f lo w s                |
|             | L e v e l  E                   | s le |             | D e                  | t a i l e d  o p e r a | t i o n a l  p r o c e s s  f l o w s   |
|             |                                | v P  | h y s i cal | with   e             | r ro r   c o n d i ti  | o n s   a n d   p r o d u c t   a n d   |
| Level 3+    |                                | e    |             |                      |                        |                                         |
|             | Op e ra ti o nal Process Flows | L Le | v e l s     |                      | g e o g r a p h        | i c a l  v a r i a n t s  ( w h e r e   |
|             |                                |  s   |             |                      |                        | r e q u i r e d ) .                     |
n
| Sub-processes and Tasks |         | o   |     |                                    |     |     |
| ----------------------- | ------- | --- | --- | ---------------------------------- | --- | --- |
|                         | Level F | ita |     |                                    |     |     |
|                         |         | re  |     | Further decomposition of detailed  |     |     |
(e.g. BPMN) Detailed Process Flows operational where required
p O
© British Telecommunications (2005)
SLIDE 18

APQC Process Classification Framework
SLIDE 19

Process Landscape Model:
Example of Wienerlinien (Vienna Public Transport)
Management Processes
Manage  Communicate  Manage  Manage  Manage Risks and  Manage
Enterprise in and out Processes Quality Opportunities Innovation
Core Processes
Manage
|     | Contact  | Manage  |     |     | Foster  |
| --- | -------- | ------- | --- | --- | ------- |
Customer
|     | Customer | Sales |     |     | Relationship |
| --- | -------- | ----- | --- | --- | ------------ |
Relationship
| Operate    | Plan and Buy  | Maintain |          |           | Check     |
| ---------- | ------------- | -------- | -------- | --------- | --------- |
| Vehicles   | Vehicles      | Vehicles |          |           | Vehicles  |
| Transport  | Plan Customer |          |          | Transport | Evaluate  |
| Customer   | Transport     |          |          | Customer  | Transport |
| Provide    | Plan          | Build    | Maintain |           | Evaluate  |
Infrastructure Infrastructure Infrastructure Infrastructure Infrastructure
Support Processes
| Manage  | Manage  | Manage  | Manage  | Manage  | Provide Winter  |
| ------- | ------- | ------- | ------- | ------- | --------------- |
Personnel Financials Information Materials Disruptions Service
SLIDE 20

How to define Process Landscape Model
1. Clarify terminology:
▪ Define key terms.
▪ Use organizational glossary.
▪ Use reference models.
▪ Ensure that stakeholders have a consistent understanding of process landscape model.
2. Identify end-to-end processes:
▪ Those processes interface with customers and suppliers.
▪ Goods and services that organization provides are good starting point.
▪ Properties help to distinguish processes, including: Product type, Service type, Channel, Customer type.
3. For each end-to-end process, identify its sequential processes:
▪ Identify the internal, intermediate outcomes of end-to-end process.
▪ Perspectives help set boundaries: Product lifecycle, Customer relationship, Supply chain, Transaction
stages, Change of business objects, Separation.
4. For each business process, identify its major management and support processes:
▪ What is required to execute the previously identified processes.
▪ Typical support processes are management of personnel, financials, information, and materials.
▪ However, these can be core processes if they are integral part of business model.
▪ Management processes are usually generic.
SLIDE 21

How to define Process Landscape Model
5. Decompose and specialize business processes:
▪ Processes of process landscape should be further subdivided into abstract process on Level 2.
▪ Further subdivision until processes can be managed autonomously by single process owner.
▪ Considerations when this subdivision should stop: Manageability and Impact.
6. Compile process profile:
▪ Each of the identified processes should be described using process profile.
▪ Process profile supports definition of boundaries, vision performance indicators, resources, etc.
7. Check completeness and consistency:
▪ Reference models can be used to check whether all major processes are included.
▪ Reference models can help to check consistency of terminology.
▪ Check whether all processes can be associated with functional units of organization chart and vice versa.
SLIDE 22

Exercise 2.5: Construction Company BuildIT
Construction Sight of WU Vienna‘s New Campus opened in 2013.
Source: Wikimedia Commons

Exercise 2.5: Construction Company BuildIT
▪ Which APQC categories on Level 1 are relevant for a construction company like
BuildIT?
SLIDE 24

Example 2.2: Construction Company BuildIT
The following passage describes the company BuildIT from a more general perspective.
With this information, we will construct its process landscape model.
The overall end-to-end process of BuildIT starts with a customer demand and ends with
the expiry of the warranty of construction works. The business development department is
responsible for identifying customer demands and public tenders. Together with the
presales engineering department, they select projects for which BuildIT prepares bids.
Bids that are approved lead to contract negotiations. Once contracts are signed, the
contract is transferred to execution. Contract execution starts with the project initiation,
which includes engineering, design, and planning. What follows then are the actual
construction works. The procure-to-pay process that we already know from Example 1.1
also belongs to these initiation procedures. Once the construction works are finished, the
construction sight is commissioned to the customer. What can still follow are corrective
works to meet warranty obligations.

Process profile of BuildIT‘s
procure-to-pay process
Name of Process: Procure-to-Pay
Vision: The objective of the procurement process is to secure that the
entire range of external products and services becomes available on time
and is at the required level of quality.
Process Owner: Chief Financial Officer (CFO)
Customer of process: Expectation of customer:
• Requesting unit • Timely, economic and complete
provision
Outcome: Delivered products or provided services for the requested unit
Trigger: Need is identified
First activity: Submit Request
..
Last activity: Create Purchase Order
Interfaces inbound: Plan-to-Procure
Interfaces outbound: Construct-to-Complete
Required resources:
• Human resources:
Site Engineer, Clerk, Works Engineer
• Information, documents, know-how:
procurement guidelines, supplier rating, framework contract
• Work environment, materials, infrastructure:
Procurement information system
Process Performance Measures:
• Cycle Time
• Operational Costs
• Error Rate
SLIDE 26

Management Processes
| Develop Vision  | Develop and     | Manage Business  | Market and Sell  |
| --------------- | --------------- | ---------------- | ---------------- |
| and Strategy    | Manage Services | Capabilities     | Services         |
Core Processes
Contract
| Demand-to-Selection |     | Selection-to-Bid | Approval-to-Contract |
| ------------------- | --- | ---------------- | -------------------- |
Acquisition
Contract
| Contract-to-Plan |     | Plan-to-Completion | Completion-to-Expiry |
| ---------------- | --- | ------------------ | -------------------- |
Execution
Support Processes
Manage Human  Manage Financial  Manage Risk and  Manage External
Capital Manage IT Resources Manage Assets Compliance Relationships
SLIDE 27

Exercise 2.6: University
WU Vienna‘s New Campus opened in 2013. Source: Wikimedia Commons

Exercise 2.6: University
▪ Create a process landscape model for a university by applying the seven steps
described in this section. Use the APQC Process Classification Framework as an
aid.

Exercise 2.7: Manageabilty and Impact
▪ Explain how the trade-off between impact and manageability works out for broad
and narrow processes, respectively.

Example of SAP Process Map
MMaannaaggeemmeenntt  PPrroocceesssseess
ManagDee fine, Operationalize, and Track Strategy Sales, Franchise, and Partner ManagemenMtanage
Enterprise Innovation
Core Processes
|     | Innovate |     | Sell |     | Deliver |
| --- | -------- | --- | ---- | --- | ------- |
Support Processes
|     |     | Workplace and  |     | Corporate Finance  | Shareholder and  |
| --- | --- | -------------- | --- | ------------------ | ---------------- |
Procure to Pay
Attract, Develop, and  Infrastructure  and Operational  Stakeholder
| Retain Workforce |     | Provision |     | Compliance | Management |
| ---------------- | --- | --------- | --- | ---------- | ---------- |
SLIDE 31

Chapter 2: Process Identification
Contents
1. The Context of Process Identification
2. Definition of the Process Architecture
1. Process Categories
2. Relationships Between Processes
3. Reuse of Reference Models
4. Process Landscape Model
5. The Example of SAP’s Process Architecture
3. Process Selection
1. Selection Criteria
2. Process Performance Measures
3. Process Portfolio
4. Recap
SEITE 32

Selection Criteria
▪ Strategic Importance:
▪ Find out which processes have the greatest impact on the strategic goals.
▪ Consider profitability, uniqueness, or contribution to competitive advantages.
▪ Select those processes for process management that relate to strategy.
▪ Health:
▪ Determine which processes are in deepest trouble.
▪ These processes may profit the most from BPM initiatives.
▪ Feasibility:
▪ Determine how susceptible process is to BPM initiatives, incidentally or continuously.
▪ Culture and politics may be obstacles.
▪ BPM should focus on those processes where it is reasonable to achieve benefits.
SLIDE 33

Exercise 2.8: Selection Criteria
▪ Exercise 2.8. Consider again the procure-to-pay process of BuildIT (page 2) and
the admission process of a university (page 5) as described in Chapter 1.
▪ Discuss their strategic importance, their health, and the feasibility of a potential
improvement to these processes.
Further Questions:
▪ Given all the discussed criteria, does an assessment of the importance, health, and
feasibility always point us to the same processes to actively manage?
▪ Should all processes that are unhealthy, of strategic importance, and feasible to
manage be subjected to BPM?
SLIDE 34

Process Performance Measures
Performance Measures Performance Objectives
▪ Formulate performance objectives of the
▪ Time
process at a high level, in the form of a
▪ Cost desirable state that the process should
ideally reach, e.g., customers should be
▪ Quality
served in less than 30 minutes.
▪ Flexibility
▪ For each performance objective, identify
the relevant performance dimension(s) and
aggregation function(s), and from there,
define one or more performance measures
for the objective in question, e.g., the
percentage of customers served in less
than 30 minutes. Let us call this measure
ST(30).
▪ Define a more refined objective based on
this performance measure, such as
ST(30) >99%.
SLIDE 35

Example 2.3: Restaurant
▪ A restaurant has recently lost many customers ▪ In this scenario, most relevant performance
due to poor customer service. The dimension is serving time.
management team has decided to address this
▪ One objective is to completely avoid waiting
issue first of all by focusing on the delivery of
times above 30 min.
meals.
▪ Percentage of customers served in less than
▪ The team gathered data by asking customers
30 min should be close to 100%.
about how quickly they liked to receive their
▪ Thus, the percentage of customers served in
meals and what they considered as an
less than 30 minutes is relevant performance
acceptable wait.
measure.
▪ The data suggested that half of the customers
▪ Threshold mentioned in scenario is 15 min.
would prefer their meals to be served in 15 min
or less. All customers agreed that a waiting ▪ Choice between two performance measures:
time of 30 min or more is unacceptable average meal delivery time or percentage of
customers served in 15 min.
SLIDE 36

Exercise 2.9: Travel Agency
▪ Consider the following summary of issues reported in a travel agency.
▪ A travel agency has recently lost several medium-sized and large corporate
customers due to complaints about poor customer service. The management team
of the travel agency decided to appoint a team of analysts to address this problem.
The team gathered data by conducting interviews and surveys with current and
past corporate customers and also by gathering customer feedback data that the
travel agency has recorded over time.
▪ About 2% of customers complained about errors that had been made in their
bookings. In one occasion, a customer had requested a change to a flight booking.
The travel agent wrote an email to the customer suggesting that the change had
been made and attached a modified travel itinerary. However, it later turned out
that the modified booking had not been confirmed in the flight reservation system.
As a result, the customer was not allowed to board the flight and this led to a series
of severe inconveniences for the customer.
SLIDE 37

Exercise 2.9: Travel Agency
▪ Similar problems had occurred when booking a flight initially: the customer had
asked for certain dates, but the flight tickets had been issued for different dates.
Additionally, customers complained of the long times it took to get responses to
their requests for quotes and itineraries. In most cases, employees of the travel
agency replied to requests for quotes within 2-4 working hours, but in the case of
some complicated itinerary requests (about 10% of the requests), it took them up
to 2 days.
▪ Finally, about 5% of customers also complained that the travel agents did not find
the best flight connections and prices for them. These customers essentially stated
that they had found better itineraries and prices on the Web by searching by
themselves.
1. Which business processes should the travel agency select for improvement?
2. For each of the business processes you identified above, indicate which
performance measure the travel agency should improve.
SLIDE 38

Balanced scorecards with cascading
process performance measures
SLIDE 39

Process Portfolio
|        | Soo e l e c t i o n  F o c u s |     |            |                   |
| ------ | ------------------------------ | --- | ---------- | ----------------- |
| H ig h |                                |     | R a t in g | F e a s ib ilit y |
LC a n
C o n t r a c t  io
|     | n t r o llin g | P r e p a t a t n |     | L o w |
| --- | -------------- | ----------------- | --- | ----- |
L o a n
D e c is io n
LE ov aa n  M a r k e t
M e d iu m
| e c |     | lu a t io n |     |     |
| --- | --- | ----------- | --- | --- |
n
a
t
| r   | H a n d lin g   |     |     |     |
| --- | --------------- | --- | --- | --- |
o
| p   |                 |     |     | H ig h |
| --- | --------------- | --- | --- | ------ |
| m   | P a y m e n t s |     |     |        |
I
LP o a n
|     |     | LA op a n   | la n n in g |     |
| --- | --- | ----------- | ----------- | --- |
p lic a t io n
L o w
| P o o r |     | H e a lt h | G o o d |     |
| ------- | --- | ---------- | ------- | --- |
SLIDE 40

Exercise 2.10: University
WU Vienna‘s New Campus opened in 2013. Source: Wikimedia Commons

Exercise 2.10: University
A university defined four core processes in relation to teaching. An evaluation of strategic
importance, health, and feasibility using a survey among the department chairs has
resulted in the following assessment:
▪ Develop and Manage Study Programs: Importance 90%, Health 90%, Feasibility 40%.
▪ Market Study Programs: Importance 75%, Health 80%, Feasibility 60%.
▪ Schedule Courses: Importance 95%, Health 30%, Feasibility 50%.
▪ Deliver Courses: Importance 95%, Health 70%, Feasibility 30%.
▪ Manage Student Services: Importance 85%, Health 50%, Feasibility 40%.
▪ Manage Facilities: Importance 40%, Health 35%, Feasibility 70%.
Draw a process portfolio and suggest one process to be selected for process improvement.
Justify your choice.

Exercise 2.10: University
High Schedule Develop and Manage Feasibility
Manage
Courses Study Programs
Student
Low
Services
Market
Study
Programs Medium
e
c
n a Deliver Courses
t
r
o
p High
m
I
Manage
Facilities
Low
Poor Health Good

Chapter 2: Process Identification
Contents
1. The Context of Process Identification
2. Definition of the Process Architecture
1. Process Categories
2. Relationships Between Processes
3. Reuse of Reference Models
4. Process Landscape Model
5. The Example of SAP’s Process Architecture
3. Process Selection
1. Selection Criteria
2. Process Performance Measures
3. Process Portfolio
4. Recap
SEITE 44

Recap
▪ In this chapter, we discussed process identification.
▪ Process architecture definition aims at enumerating major processes of organization.
▪ Process architecture defines relationship between processes.
▪ Seven-step method for definition of process architecture including process landscape model.
▪ Process selection is concerned with prioritizing processes.
▪ Priorities upon importance of processes, health, and feasibility of improvements.
▪ Assessed by process owners or grounded on process performance measures and objectives.
▪ Most common performance dimensions are time, cost, quality, and flexibility.
▪ Process portfolios help in selection of processes for improvement.
▪ Selected processes become subject of remaining phases of BPM lifecycle.
SLIDE 45