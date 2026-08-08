Chapter 5: Process Discovery
Contents
1. The Setting of Process Discovery
2. Process Discovery Methods
3. Process Modeling Method
4. Process Model Quality Assurance
5. Recap

Process Modeling in the BPM Lifecycle
P r o c e s s   Management Processes
Define Vision Develop Strategy Implement  Manage Risk
Strategy
|     |     |     |     |     | id e n t if ic a t io n |     |
| --- | --- | --- | --- | --- | ----------------------- | --- |
Core Processes
Pr o cu r e P r o c u r e M a r ke t D e liv e r   M a n a g e
M a te ri a ls P r o d u c t s P ro d u ct s P ro d u c ts C S u e s t r o v i m c e e r
Support Processes
|     |     |     |     |     | P r o c e | s s  a r c h it e c t u r e |
| --- | --- | --- | --- | --- | --------- | --------------------------- |
E x a m p le s fo r B P M  life cy cle  a n d  p ro ce ss m in in g Manage Personnel Information  Manage Manage Assets
B 30h
35h
|          | 15h            | C o n        | fo r m a n c e  a n  d   |     | P r o c e s s    |                           |
| -------- | -------------- | ------------ | ------------------------ | --- | ---------------- | ------------------------- |
| A        |                | E            |                          |     |                  | A s -ism  po rd o c e s s |
| 5m 3m 5m | 10m D          | 30m 2h 10m p | e r fo r m a n c e       |     |                  |                           |
|          |                |              |                          |     | d is c o v e r y | e l                       |
|          | C              |              | in s ig h t s            |     |                  |                           |
|          | 15m 1.5h 10min |              |                          |     |                  |                           |
|          | A B C          | D E          |                          |     |                  |                           |
|          |                | P            | r o c e s s              |     |                  | Pa rn o c e s s           |
|          |                | m o          | n it o r in g            |     |                  | a ly s is                 |
In s ig h t s  o n
|     |     | E x e c u t | a b le   |     |     |     |
| --- | --- | ----------- | -------- | --- | --- | --- |
w e a k n e s s e s  a nt d
|     |     | p r o c e | s s |     |     |     |
| --- | --- | --------- | --- | --- | --- | --- |
t h e ir  im p a c
|     |     | m o d | e l       |          |                           |                |
| --- | --- | ----- | --------- | -------- | ------------------------- | -------------- |
|     |     |       | P rm o ce | en st sa |                           | P r o c e s s  |
|     |     |       | im p le   | t io n   |                           | r e d e s ig n |
|     |     |       |           |          | T o -b e  p r o c e s s   |                |
m o d e l

Chapter 5: Process Discovery
Contents
1. The Setting of Process Discovery
2. Process Discovery Methods
3. Process Modeling Method
4. Process Model Quality Assurance
5. Recap

4
Process discovery
Four main tasks:
▪ Define the setting: assemble a team that will be responsible for
managing the process
▪ Gather information: build an understanding of the process. Different
discovery methods available
r
e
▪ Conduct the modeling: do the actual modeling
h
t
e
g
o
t
▪ Assure model quality: guarantee that the resulting model meets
e
n
o different quality criteria
d

5
Who is involved?
Process analyst Domain expert

Example: modeling perspective
Consider the following two modelling tasks:
▪ Modeling the process for ordering books through an online bookstore, from the
perspective of the customer.
▪ Modeling the same process from the perspective of the bookstore.
Which of the two tasks above are you familiar with and why?

Exercise 5.1
You are the manager of a consulting company and you need to hire a
person for the newly signed BPM project with an online bookstore.
Consider the following two profiles; who would you hire as a process
analyst?
▪ Mike Miller has ten years of work experience with an online retailer. He has
worked in different teams involved with the order-to-cash process of the online
retailer.
▪ Sara Smith has five years of experience working as a process analyst in the
banking sector. She is familiar with two different process modeling languages
and with several modeling tools.

8
Challenge 1: Fragmented process knowledge
I make a photocopy
before handing over
the application
Why can‘t I directly
provide cash after
approval?
We bundle refinancing
to get better interest
rates.

9
Challenge 2: Domain experts think on instance level
“Every trip is different”
“You cannot really compare. Our
customers go to different places in
different seasons using different
modes of transportation”
“We can never do anything exactly
in the same way. There are so many
special conditions”

10
Challenge 3: Knowledge of process modeling is uncommon
“Does this diagram correctly show your process?”

11
What makes a good process analyst?
▪ Getting the right people on board
▪ Formulate and test hypotheses
▪ Identify patterns
▪ Pay attention to model quality

Exercise 5.2
Consider the order-to-cash process of your preferred online bookstore
and assume you have access to three internal resources: a customer
relationship manager (who handles sales and reclaims), a warehouse
worker (who looks after shipments), and a financial officer (who raises
invoices and collects payments). As a process analyst, what questions do
you need to ask these domain experts to be able to obtain a complete
and systematic view of this process?
Hint. Think of the different exposure to this process that the three
resources have and of the possible conditions, process outcomes, and
exceptions that they may have experienced while executing this process.

Profile of an Expert Process Analyst
1. Getting the right people on board
2. Having a set of working hypotheses of how the process is structured
at different levels of detail
3. Identifying patterns in the information provided by domain experts
4. Paying attention to model quality

Chapter 5: Process Discovery
Contents
1. The Setting of Process Discovery
2. Process Discovery Methods
3. Process Modeling Method
4. Process Model Quality Assurance
5. Recap

15
Process discovery methods
1. Evidence-based
▪ Document analysis
▪ Observation
▪ Automated process discovery
2. Interview-based
3. Workshop-based
Choose one or more on the basis of context and budget

16
Document Analysis
Documents point to existing roles, activities and business objects:
▪ Process descriptions (ideal scenario)
▪ Internal policies
▪ Organization charts
▪ Employment plans
▪ Quality certificate reports
▪ Glossaries and handbooks
▪ Forms
▪ Work instructions…
Could be used to gather information before approaching domain experts.
Potential issues:
▪ May not be process-oriented and trustworthy
▪ May require abstraction or refinement

17
Observation
▪ Follow directly the execution of individual process instances,
then abstract from instance to process level:
▪ Active role: play a specific role, e.g. customer
▪ Passive role: observe participants and their environment
▪ Trace business objects in the course of their lifecycle
Potential issues:
▪ Active role: no big picture
▪ Passive role: participants’ bias

18
Automated process discovery and Process mining
Discovery
discovered model
event stream
Enhancement
enhanced model
event log
existing model
DB
✓/
Conformance

Automated discovery: Minimum data requirements
▪ Activity name and timestamp
▪ Reference to case id
Additional information:
▪ Activity resource, cost
▪ Case attributes (e.g. customer reference, type of case…)

Exercise 5.3
As a process analyst working for the University of Newtown, you have
been engaged by Mark Johnson, the process owner of the student
admission process, in a project that aims at improving this process. In
order to model the as-is process, you start by collecting relevant
information about this process. The available documentation includes the
organization chart of the Office of the Deputy Vice-Chancellor (DVC) for
Student Affairs where Mark’s team sits, the UML class diagram of the
student admission system which supports this process, and a set of
relevant organizational policies that you extract from the university’s Web
pages.
Based on this documentation, formulate initial hypotheses on how the
student admission process works. Next, identify the relevant domain
experts to interview and their supervisors whom you should seek
approval from.

Exercise 5.3 (cont’ed)
Organizational chart of the Office of the DVC (Student Affairs)

Exercise 5.3 (cont’ed)
Extract of the UML class diagram of the student admission system

Exercise 5.3 (cont’ed)
Organizational policies for student admission

24
Interview-based Discovery
Approaches:
▪ forward vs backward
▪ structured vs unstructured
Assumption: analyst and domain expert share terminology
Pitfall: exceptional behavior tends to be neglected > use questions that
aim to identify such behavior

Exercise 5.4
After collecting relevant information on the student admission process,
you interviewed some representatives for the two roles involved in this
process: Mary Adams and Louise Smith as student admission officers,
and Peter Capello as a member of the academic committee (Mark
Johnson, the process owner, confirmed that the enrollment office is not
involved in this process). The relevant parts of the interview transcripts
are provided below.

Exercise 5.4 (cont’ed)
Student admission officer (Mary Adams):
“My process starts when I receive an application for admission. First, I check the
completeness of this document. If the application is incomplete, I need to send a
request for clarification back to the applicant. Otherwise, I forward it to the
academic committee. I then receive a response from the academic committee
which can be either of the below:
▪ A notification of acceptance from the academic committee. In this case, I
prepare a letter of offer and send it to the applicant via post to collect his or her
signature. Most of the times, I receive a signed offer back from the applicant,
but sometimes I don’t.
▪ A notification of rejection. In this case, I send a rejection letter to the applicant
via ordinary post.
The problem is that the academic committee is often too slow to reply. I wonder if
these academics are just too overloaded with work to care about student
admissions...”

Exercise 5.4 (cont’ed)
Student admission officer (Louise Smith):
“When I get a fresh application, it’s important that this contains all the required
information, including name, address, phone number and email address of the
applicant. Unfortunately, the Web portal has many bugs and sometimes lets
through incomplete applications, which are a nightmare to rectify! This means
going back and forth with the student at least a couple of times. Anyway, once the
application is complete, I pass it to a member of the academic committee using
our internal student admission system – the same that collects applications via
the Web portal. Most of the times, the member of the academic committee replies
with a notification of acceptance, in which case I need to prepare a letter of offer
and send it to the applicant via post. Our policies are such that applicants must
reply within four weeks. In fact, we are flooded by applications, so if they do not
hurry to reply, we will offer the place to someone else. Sometimes I receive a
notification of rejection. Well, in this case I formulate a rejection letter and send it
to the applicant via post.”

Exercise 5.4 (cont’ed)
Member of academic committee (Peter Capello):
“When I receive an application from the admission officer, I assess its quality. I
extract the grade of the applicant from his or her previous degree and convert it to
a standard score based on a conversion table. The score must be at least 70%;
otherwise the student is out. Next, I perform a plagiarism check of the essay
contained in the application using our pla- giarism detection software. Most of the
times, the essay is plagiarism-free. If so, I proceed to read it and assign it a score.
Finally, I read the two reference letters attached to the appli- cation. There’s a lot
you can learn from a reference letter. Often there are subtle messages that the
referee wants you to get, like “This is a great student, but I’ve had better ones”. In
any case, based on the score, quality of the essay and reference letters, if I deem
that the applicant is qualified, I send an acceptance notification to the admission
officer, otherwise I send a rejection notification. In either case, I archive the results
of my assessment in my database. Ah, I communicate with the student admission
office using our internal student admission system. A piece of junk, sometimes
messages get lost and I have to send them again, if I’m lucky to find it out!”

Exercise 5.4 (cont’ed)
Next, you took an active role in observing how this process works by
acting as the applicant. Using a fake identity (in agreement with the
process owner), you triggered this process several times by submitting
various applications via the Web portal. Af- ter this, you came up with the
following observations.

Exercise 5.4 (cont’ed)
Applicant:
To apply for admission, the applicant needs to prepare an admission application
and submit it to the university via a Web portal. The application must include
academic transcripts, an essay and two reference letters. The applicant will then
receive a response from an admission officer via ordinary mail, which can be:
▪ A letter of offer. In this case, the applicant needs to sign the letter of offer and
return it to the admission officer via post within four weeks.
▪ A rejection letter. In this case, the applicant does not do anything further and
the pro- cess is finished.
▪ A request for clarification from the admission officer. This is an email
notification. In this case, the applicant provides the required documentation to
the admission officer by submitting an updated application through the same
Web portal used for the initial submission, and then gets a response that is the
letter of offer, the rejection letter, or again a request for clarification.

Exercise 5.4 (cont’ed)
Using the information above, create a draft BPMN model of the as-is
student admission process. This draft will then be validated with the
people that have been interviewed, before sign-off by the process owner.
Make appropriate assumptions.

32
Workshop-based Discovery
▪ Gather all key stakeholders together
▪ Participants interact to create shared understanding
▪ Typically one process analyst (facilitator), multiple domain experts,
process owner may also attend
▪ May be software-supported – a model is directly created during
the workshop (typically a separate role – tool operator)
▪ Model is used as a reference point for discussions
▪ Alternative: brown-paper workshops
▪ Usually 3 to 5 half-day sessions

33
Example: Any difference in discovery?
Consider the following two companies:
• Company A is young, founded three
years ago, and has grown rapidly to a
current toll of one hundred
employees.
• Company B is owned by the
government and operates in a
domain with extensive health and
security regulations.
How might these different characteristics
influence a workshop-based discovery
approach?

34
Discovery and Culture
Before starting with process discovery, it is important to understand the culture
and the sentiment of an organization.
▪ There are companies that preach and practice an open culture in which all
employees are encouraged to utter their ideas and their criticism. Such
organizations can benefit a lot from workshops as participants are likely to
present their ideas freely.
▪ In strictly hierarchical organizations, it is necessary to take special care that
every participant gets an equal share of parole in a workshop and that ideas
and critique are not held back.
It might be the case that the young dynamic company has a more open culture
than the company with extensive health and security regulations. This has to be
taken into account when organizing a workshop.

Exercise 5.5
Consider the complaints that have emerged from the interviews reported
in Exercise 5.4. As a facilitator, what questions would you ask the various
participants to investigate these further in a workshop?

36
Discovery methods: strengths and weaknesses
| Aspect | Evidence- | Interviews | Workshops |
| ------ | --------- | ---------- | --------- |
based
| Objectivity | High       | Medium-high | Medium-high |
| ----------- | ---------- | ----------- | ----------- |
| Richness    | Medium     | High        | High        |
| Time        | Low-medium | Medium      | Medium      |
consumption
| Immediacy of  | Low | High | High |
| ------------- | --- | ---- | ---- |
feedback

37
Discovery methods: strengths and weaknesses
| Method | Strength | Weakness |     |     |
| ------ | -------- | -------- | --- | --- |
Document Analysis • Structuredinformation • Outdated material
|     | • Independent from  | •   | Wrong level of  |     |
| --- | ------------------- | --- | --------------- | --- |
|     | availability of     |     | abstraction     |     |
stakeholders
| Observation | • Context-rich insight  | •   | Potentially intrusive |            |
| ----------- | ----------------------- | --- | --------------------- | ---------- |
|             | into process            | •   | Stakeholders          | likely to  |
behave differently
• Only few cases
Automatic Discovery • Extensive set of  • Potential issue with
|           | cases                    |     | data quality and level  |     |
| --------- | ------------------------ | --- | ----------------------- | --- |
|           | • Objective data         |     | of abstraction          |     |
| Interview | • Detailed inquiry into  | •   | Requires sparse time    |     |
|           | process                  |     | of process              |     |
stakeholders
• Several iterations
|          |                     |       | required before          | sign-off |
| -------- | ------------------- | ----- | ------------------------ | -------- |
| Workshop | • Direct resolution | of  • | Requires availability    | of       |
|          | conflicting views   |       | several stakeholders at  |          |
the same time

In what situations is it simply not possible to use one or more
of the described discovery methods?

Exercise 5.6
The order-to-cash process of your favorite online bookstore has ten major
activities conducted by ten people with five different roles. How much time
do you approximately need for creating a process model that is validated
by the various stakeholders and approved by the process owner?
Consider two scenarios: one in which you run interviews, the other in
which you run workshops. You may also use other discovery methods in
these two scenarios, in addition to either inter- views or workshops. Can
you estimate the difference in time effort between the two scenarios?
Make appropriate assumptions.

Chapter 5: Process Discovery
Contents
1. The Setting of Process Discovery
2. Process Discovery Methods
3. Process Modeling Method
4. Process Model Quality Assurance
5. Recap

41
Stepwise method to conduct the modeling
1. Identify the process boundaries
2. Identify activities and events
3. Identify resources and their handovers
4. Identify the control flow
5. Identify additional elements (e.g. data objects, different types of events,
exception handling…)

1. Identify the process boundaries
What are the process triggers?
Purchase order received
What are the possible outcomes (positive/negative)?
Positive outcome: order fulfilled
Negative outcome: order rejected
Which perspective do we assume?
Seller
What artifacts are required as input and output to the process?
Input: Purchase order
Output: Invoice, Shipment notice

Exercise 5.7
Identify the process boundaries for the procure-to-pay process de-
scribed in Exercise 1.7 of Chapter 1 (page 30).

44
2. Identify activities and events

Exercise 5.8
Identify the main activities and events for the procure-to-pay process.

46
3. Identify resources and their handoffs

Exercise 5.9
Using the description of the procure-to-pay process, first identify the
involved resources; next, assign the activities and events you obtained in
Exercise 5.8 to these resources; and finally identify the handoffs.

48
4. Identify the control flow

Exercise 5.10
Using the description of the procure-to-pay process, refine the model you
obtained in Exercise 5.9 by defining the full control flow.

50
5. Identify additional elements

When should we stop modelling a process?

Exercise 5.11
Using the description of the procure-to-pay process, define the model you
obtained in Exercise 5.10 by adding business objects and exception
handlers.

Chapter 5: Process Discovery
Contents
1. The Setting of Process Discovery
2. Process Discovery Methods
3. Process Modeling Method
4. Process Model Quality Assurance
5. Recap

54
Process model quality assurance
• Validity • Understandibility
• Completeness • Mantainability
• Learning
• Structural correctness
• Behavioral correctness

Syntactic quality: Verification
Syntactic quality relates to the conformance of a process model to the syntactic
rules of the modeling language used.
Two types of syntactic rules: structural rules and behavioural rules.
A model is of high syntactic quality if it is syntactically correct:
▪ Structurally correct +
▪ Behaviorally correct

Structural correctness
A model is structurally correct if it satisfies the following syntactic rules:
1. Element-level rules:
▪ activities must have at least one incoming and one outgoing sequence flow
▪ start events must not have incoming arcs, end events must not have outgoing arcs
▪ gateways must have exactly one incoming and at least two outgoing arcs (splits) or at
least two incoming and exactly one outgoing arcs (joins)
▪ …
2. Model-level rule: all flow nodes must be on a path from a start to an end
event
▪ i.e. no dangling arcs or disconnected nodes
▪ implies that a model should have at least one start and one end event.

Example: structural correctness

Behavioral correctness (aka “soundness”)
A model is sound if it satisfies the following behavioral rules:
1. option to complete: any running process instance must eventually complete,
2. proper completion: at the moment of completion, each token of the process
instance should be in a different end event, and
3. no dead activities: any activity can be executed in at least one process
instance.

Exercise 5.12
Have a look at Figure 5.11. What is precisely going wrong in each block
structure?

60
Example: no option to complete
If c1 is true after executing A, or c2 is true after executing B, the instance cannot complete
(deadlock)
Note: this model also suffers from a dead activity (D)

61
Example: livelock (no option to complete)
If condition_1 is true, the instance cannot complete and activity B will be repeated
forever (livelock)
Note: this model is structurally incorrect, because B is not on a path to the end event

62
Example: no proper completion
At the moment of completion, there will be two tokens in the end event (lack of
synchronization)

63
Example: dead activity
Even if this model can always complete, Activity D will never be executed
Note: this model also suffers from a deadlock, as a token will be left behind (stuck before the
AND-join). However, there is always an option to complete

Exercise 5.13
Fulfilment of special orders
▪ Which behavioral rules are violated in the model below?
▪ How can this model be made sound?

65
Semantic quality: validation
Semantic quality relates to the adherence of a process model to its real-world
process.
Validation is the activity of checking the semantic quality of a model by
comparing it with its real-world business process.
A model is of high semantic quality if it is semantically correct:
• Valid (all model instances are correct and relevant) +
• Complete (all possible process instances are covered)
Domain Expert Process Analyst

66
Semantics
Meaning of the various elements
▪ Activities model something actively performed during the process
▪ Events model something happening instantaneously during the process
▪ AND gateways model parallelism
▪ XOR gateways model exclusive decisions and simple merging points
▪ OR gateways model inclusive decisions and synchronizing merging points
+
Meaning of the whole business process model
▪ “This model captures an order fulfilment process that takes place at a seller.
The model starts with the receipt of an order…”

Exercise 5.14
Consider the following process description.
A company has two warehouses that store different products:
Amsterdam and Hamburg. When an order is received, it is distributed
across these warehouses: if some of the relevant products are
maintained in Amsterdam, a sub-order is sent there; likewise, if some
relevant products are maintained in Hamburg, a sub-order is sent there.
Afterwards, the order is registered and the process completes.
7

Exercise 5.14 (cont’ed)
What can we say about the semantic quality of this model?
Invalid
It is not possible that products are neither in the Amsterdam nor in the Hamburg
warehouse.
7

Example: semantic correctness
And about this one? (with reference to the same description)
Incomplete
Orders may contain both products that are in Amsterdam and products that are
in Hamburg
7

Exercise 5.15
Consider the model in the next slide, with reference to the following
process description. Is this model valid and complete? If not, what
statements are invalid and what is missing?
When a special order is received, it is first registered and then its details are checked. Next,
the order is confirmed and meantime the custom product is manufactured. Once the product
has been made, the shipment can be planned. Afterwards, the customer type and shipment
status are checked. In fact, if a customer is casual an ad hoc invoice must be emitted, which
is not required for ordinary customers. In the latter case, the customer account is simply
charged with the costs related to the order fulfillment. Moreover, if the shipment has been
delayed, the customer must be updated on the expected delay. Concomitantly to these
activities, the custom product is shipped. After the latter activity and after the invoice has
been emitted, the process completes with the archival of the order. Any time during the
confirmation of the order and the manufacturing of the respective product, an order change
request may be received, in which case any activity must be interrupted to handle the
change re- quest. This includes the registration of the order variation and a notification to
the customer, after which the process resumes from the order checking.

Exercise 5.15 (cont’ed)

Pragmatic Quality: Certification
Pragmatic quality relates to the usability of a process model
Challenge = anticipate the particular usage of the model
Usability:
▪ Understandability: how easy it is to read and comprehend the model
▪ Maintainability: how easy it is to apply changes
▪ Learning: how good a model reveals how its corresponding process
works in reality
Model characteristics that influence usability include size, structural
complexity and layout
72

Example: block-structuring a model
73

74
Is this process model of good pragmatic quality?
Different labeling styles
Noun phrase
Verb phrase
(imperative)
Noun phrase
(using “of”)
Verb phrase
(gerund)

75
Example: A model from the SAP R/3 collection…

Exercise 5.16
Is the process model below of good pragmatic quality? If not, how can it
be improved?

77
Modeling Guidelines and Conventions
Used to improve pragmatic quality by restricting:
1. Vocabulary (e.g. banning the use of the OR gateway)
2. Structure (e.g. limiting the size of a model to max 30 nodes)
3. Semantics – rare (e.g. using data objects to only capture information flow)
4. Appearence (e.g. enforcing a particular labeling or layout style)

Example: modeling guidelines and conventions
Labeling
1. Activities as imperative verb + noun
2. Events as noun + past-participle verb
3. Conditions on outgoing arcs of (X)OR-splits with reference to object
Layout
1. From top-left to bottom-right
2. Use direct arcs with no crossing where possible

79
Example modelling guidelines: 7PMG
G1 Use as few elements in the model as possible
G2 Minimize the routing paths per element
G3 Use one start event (per trigger) and one end event (per outcome)
G4 Model as structured as possible
G5 Avoid OR gateways where possible
G6 Use verb-object activity labels
G7 Decompose a model with more than 30 elements

80
Exercise 5.17
Which 7PMG can be applied to this model? Consider the description below.
A complaint is triggered by a phone call by a complaining customer. It is decided whether the
complaint can be handled or whether it has to be referred to an internal or external party. An
external referral leads to a telephone confirmation to the external party. An internal referral is
added to the incident agenda. If no referral is needed, a complaint analysis is conducted and
the complainant is contacted. In either case, the complaint is archived and the case is closed.

Chapter 5: Process Discovery
Contents
1. The Setting of Process Discovery
2. Process Discovery Methods
3. Process Modeling Method
4. Process Model Quality Assurance
5. Recap

Recap
1. For Process Discovery, we have to define the setting, gather
information, conduct modeling and assure model quality
2. There are various discovery methods such as document
analysis, observation, automated process discovery,
interviews and workshops
3. A modeling method proceeds by identifying the process
boundaries, then activities and events, resources and their
handoffs, control flow and additional elements
4. Quality assurance relates to syntactic, semantic and pragmatic
quality