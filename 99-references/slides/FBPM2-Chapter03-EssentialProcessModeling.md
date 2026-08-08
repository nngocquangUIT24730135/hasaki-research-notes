Chapter 3: Essential Process Modeling
Contents
1. First Steps with BPMN
2. Branching and Merging
3. Business Objects
4. Resources
5. Process Decomposition
6. Process Model Reuse
7. Recap

Process Modeling in the BPM Lifecycle
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

Chapter 3: Essential Process Modeling
Contents
1. First Steps with BPMN
2. Branching and Merging
3. Business Objects
4. Resources
5. Process Decomposition
6. Process Model Reuse
7. Recap

Business Process Model and Notation (BPMN)
▪ OMG standard (BPMN 2.1)
▪ Supported by numerous tools: bpmn.org lists over 70 tools
▪ Both for conceptual and executable models

BPMN from 10,000 miles…
Based on popular graphical flowcharts:
- Core set of notation elements
- Each core element has various subtypes
A BPMN process model is a graph consisting of four types of core elements:
start end
activity event gateway sequence
flow

Let’s start modeling
Order-to-cash
A typical order-to-cash process is triggered by the receipt of a purchase order from a
customer. The purchase order has to be checked against the stock regarding the
availability of the item(s) requested. Depending on stock availability the purchase order
may be confirmed or rejected.
If the purchase order is confirmed, an invoice is emitted and the goods requested are
shipped. The process completes by archiving the order or if the order is rejected.

Solution in BPMN: Order-to-cash
end
|     |     |     | Reject order | event |     |
| --- | --- | --- | ------------ | ----- | --- |
activity
Items not in
Oe rd e r
stock
r je c te d
|     | Check stock  C hv ea c k   sb | to c k   | split gateway |     |     |
| --- | ----------------------------- | -------- | ------------- | --- | --- |
end
|     | a ila | ilit y |     |     |     |
| --- | ----- | ------ | --- | --- | --- |
event
P u r c h a s e
| o rd e r       |     | Items in |          |     |         |
| -------------- | --- | -------- | -------- | --- | ------- |
| r e c e iv e d |     | stock    | Confirm  |     | Archive |
E mo it
start Ship goods
|     |     |     | order |   in v ic e | order |
| --- | --- | --- | ----- | ----------- | ----- |
Order
event
fulfilled
Naming conventions
• Event: noun + past-participle verb (e.g. insurance claim lodged)
• Activity: imperative verb + noun (e.g. assess credit risk)

8
BPMN core elements
Activities capture work performed in a process
▪ Different types of activities
activity
Events represent the process’ triggers (start event)
and outcomes (end event).
▪ Different types of events
start end
event event

9
BPMN core elements
Gateways capture forking and joining paths in the control flow.
▪ Different types of gateways
gateway
Sequence flows represent the order in which activities and events
will be performed.
They can be assigned a condition to distinguish between alternative
branches.
sequence
▪ Different types of flows
flow

P
r
u r c h a s e
o rd e r
e c e iv e d
C
a
hv ea c k
ila
sb to c
ilit y
k
Ite m s n o t in
s to c k
Ite m s in
s to c k
R e
C
je
oo
c t o r
n fir m
r d e r
d e r
r
Oe rd
je c
e r
te d
E
in v
mo it
ic e
S h ip g o o d s
A ro cr hd iv
e r
e
Ofu rd e
lfille
rd
10
Process model vs process instances: The tokens game
Order #1
Order #2
Order #3

11
A little bit more on events…
A start event triggers a new process instance start
by generating a token that traverses the
event
sequence flow (“tokens source”)
An end event signals that a process instance has
end
completed with a given outcome by consuming
event
a token (“tokens sink”)

12
Let’s reconsider our order-to-cash example
| […] If  | the purchase |       | order         |           | is confirmed, |     | an invoice |     | is  |
| ------- | ------------ | ----- | ------------- | --------- | ------------- | --- | ---------- | --- | --- |
| emitted | and the      | goods |               | requested |               | are | shipped.   |     | The |
| process | completes    | by    | archiving     |           | the order.    | […] |            |     |     |
|         |              |       | R e je c t  o | r d e r   |               |     |            |     |     |
Ite m s  n o t in
|     |     |     |     |     | Oe rd e r |     |     |     |     |
| --- | --- | --- | --- | --- | --------- | --- | --- | --- | --- |
s to c k
|     |     |     |     |     | r je c te d |     |     |     |     |
| --- | --- | --- | --- | --- | ----------- | --- | --- | --- | --- |
C hv ea c k   sb to c k
a ila ilit y
P u r c h a s e
| o rd e r       | Ite | m s  in |            |     |             |     |                |            |      |
| -------------- | --- | ------- | ---------- | --- | ----------- | --- | -------------- | ---------- | ---- |
| r e c e iv e d | s   | to c k  |            |     |             |     |                |            |      |
|                |     |         | C oo n fir | m   | E mo it     |     |                | A ro cr hd | iv e |
|                |     |         |            |     |             | S h | ip   g o o d s |            |      |
|                |     |         | r d e      | r   |   in v ic e |     |                |            | e r  |
Ofu rd e rd
lfille

13
Solution: Order-to-cash
RReejjeecctt  oorrddeerr
IItteemmss  nnoott  iinn
OOrrddeerr
ssttoocckk
rreejjeecctteedd
CChheecckk  ssttoocckk
| split |     | Emit invoice |     |     |
| ----- | --- | ------------ | --- | --- |
aavvaaiillaabbiilliittyy
PPuurrcchhaassee
oorrddeerr IItteemmss  iinn
rreecceeiivveedd ssttoocckk
| CCoonnffiirrmm   |     | Emit | AArrcchhiivvee |     |
| ---------------- | --- | ---- | -------------- | --- |
Ship goods
| oorrddeerr |     |  invoice | oorrddeerr |     |
| ---------- | --- | -------- | ---------- | --- |
OOrrddeerr
|     | split |     | join | ffuullffiilllleedd |
| --- | ----- | --- | ---- | ------------------ |
Ship goods

Mapping, Abstraction, and Purpose of a Model
Models are abstractions from real world phenomena,
developed for the purpose of reducing overall complexity.
Models aggregate information and document only relevant
aspects of the real world
Models are being developed:
1. in a specific modelling subject
2. for a specific target audience
3. with a specific modelling purpose in mind

15
What’s the relevant model?
?

Chapter 3: Essential Process Modeling
Contents
1. First Steps with BPMN
2. Branching and Merging
3. Business Objects
4. Resources
5. Process Decomposition
6. Process Model Reuse
7. Recap

17
A little more on gateways: XOR Gateway
An XOR Gateway captures decision points (XOR-
split) and points where alternative flows are merged
(XOR-join)
c o n d itio n
| XOR-split | ➔ takes one | outgoing branch |     |
| --------- | ----------- | --------------- | --- |
¬  c o n d itio n
| XOR-join | ➔ proceeds when one |     | incoming branch  |
| -------- | ------------------- | --- | ---------------- |
has completed

Example: XOR Gateway
Invoice checking process
5

Exercise 3.1
Model the following fragment of a business process for assessing
loan applications (loan origination process).
Once a loan application has been approved by the loan provider, an
acceptance pack is prepared and sent to the customer. The acceptance
pack includes a repayment schedule which the customer needs to agree
upon by sending the signed documents back to the loan provider. The latter
then verifies the repayment agreement: if the applicant disagreed with the
repayment schedule, the loan provider cancels the application; if the
applicant agreed, the loan provider approves the application. In either case,
the process completes with the loan provider notifying the applicant of the
application status.

A little more on gateways: AND Gateway
An AND Gateway provides a mechanism to
create and synchronize “parallel” flows.
AND-split ➔ takes all outgoing branches
AND-join ➔ proceeds when all incoming
branches have completed

Example: AND Gateway
Airport security check

P u rc h a s e
o rd e r
re c e iv e d
C h e
a v a
c kila sb to c
ility
k
Ite m s n o t in
s to c k
Ite m s in
s to c k
C
R
o
e
n
je c t o r
fir m o
d
r
e
d
r
e r
O
re
rd
je c
e r
te d
S e
S
n
h
d
ip
in
g
v
o
o
o
ic
d s
e
A ro cr hd iv e
e r
Ofu rd e
lfille
rd
Revised solution
Order-to-cash
XOR-split
AND-split AND-join

Exercise 3.2
Model the following fragment of a business process for assessing
loan applications.
A loan application is approved if it passes two checks: i) the applicant’s loan
risk assessment, done automatically by a system, and ii) the appraisal of the
property for which the loan has been asked, carried out by a property
appraiser. The risk assessment requires a credit history check on the
applicant, which is performed by a financial officer. Once both the loan risk
assessment and the property appraisal have been performed, a loan officer
can assess the applicant’s eligibility. If the applicant is not eligible, the
application is rejected, otherwise the acceptance pack is prepared and sent
to the applicant.

24
Business Process Modeling Tools
Pen & Paper
Haptic
Standalone
▪ E.g. Visio, Camunda Modeler
Repository-based
▪ E.g. ARIS, Signavio, Apromore

XOR / AND are not always what we need...
Order distribution process
A company has two warehouses, one in Amsterdam, the other in
Hamburg, that store different products. When an order is received, it is
distributed across these warehouses: if some of the relevant products
are maintained in Amsterdam, a sub-order is sent there; likewise, if some
relevant products are maintained in Hamburg, a sub-order is sent there.
Afterwards, the order is registered and the process completes.

Solution 1
Order distribution process
XOR-split XOR-join
AND-split AND-join

Solution 2
Order distribution process
AND-split AND-join
XOR-split XOR-join

OR Gateway
An OR Gateway provides a mechanism to
create and synchronize n out of m parallel
flows.
cond
1
OR-split ➔ takes one or more branches
depending on conditions
cond
n
OR-join ➔ proceeds when all active
incoming branches have completed

29
Solution using OR Gateway
Order distribution process

30
What join type do we need here?

When should we use an OR-join?

Exercise 3.3
Model the following fragment of a business process for assessing
loan applications.
A loan application may be coupled with a home insurance which is offered at
discounted prices. The applicants may express their interest in a home
insurance plan at the time of submitting their loan application to the loan
provider. Based on this information, if the loan application is approved, the
loan provider may either only send an acceptance pack to the applicant, or
also send a home insurance quote. The process then continues with the
verification of the repayment agreement.

Rework and repetition
Address ministerial correspondence
In the treasury minister’s office, once a ministerial inquiry has been received, it is
registered into the system. Then the inquiry is investigated so that a ministerial response
can be prepared.
The finalization of a response includes the preparation of the response itself by the
cabinet officer and the review of the response by the principal registrar. If the registrar
does not approve the response, the latter needs to be prepared again by the cabinet
officer for review. The process finishes only once the response has been approved.
XOR-join: entry XOR-split: exit
point point

Why do we need to merge the loopback branch
of a repetition block with an XOR-join?

Exercise 3.4
Model the following fragment of a business process for assessing
loan applications.
Once a loan application is received by the loan provider, and before
proceeding with its assessment, the application itself needs to be checked
for completeness. If the application is incomplete, it is returned to the
applicant, so that they can fill out the missing information and send it back to
the loan provider. This process is repeated until the application is found
complete.

36
Components of a modeling language
Modelling Language
Vocabulary
| Syntax | Semantics | Notation |
| ------ | --------- | -------- |

37
Components of a modeling language: Vocabulary
Vocabulary: set of modeling elements of
Modelling Language
the language (BPMN: activities, gateways,
Vocabulary events…)
Syntax Semantics Notation

38
Components of a modeling language: Syntax
Syntax: set of rules to govern how these
Modelling Language
elements can be combined (BPMN: start
Vocabulary events only have outgoing sequence flows
whereas end events only have incoming
sequence flows).
Syntax Semantics Notation

39
Components of a modeling language
Semantics: bind these elements, including
Modelling Language
their textual descriptions, to a precise
Vocabulary meaning (in BPMN: activities model
something actively performed during the
business process, while XOR gateways
Syntax Semantics Notation
model exclusive decisions and simple
merging points).

40
Components of a modeling language: Notation
Notation: set of graphical symbols for the
Modelling Language
visualization of the elements (in BPMN:
Vocabulary
labeled rounded boxes to depict activities
and the circles with a thin border to depict
start events).
Syntax Semantics Notation

Chapter 3: Essential Process Modeling
Contents
1. First Steps with BPMN
2. Branching and Merging
3. Business Objects
4. Resources
5. Process Decomposition
6. Process Model Reuse
7. Recap

Business Objects (aka artifacts)
Can be:
▪ Physical or digital information artifacts (e.g. an order on paper, an invoice on PDF)
▪ Physical material (e.g. a box containing the ordered goods)
42

Our Order-to-cash process, again
43
P u rc h a s e
o rd e r
re c e iv e d
C h e
a v a
c kila sb to c
ility
k
Ites
Ite ms
m s
to c
s n
to c
in
k
o t in
k
R e je c t o r d
C oo
e r
nr
d
fir m
e r
O
re
rd
je c
e r
te d
S
S e n d
in v o ic e
h ip g o o d s
A ro cr hd iv e
e r
Ofu rd e
lfille
rd
The purchase order document serves as an input to the stock
availability check against the Warehouse DB. Based on the
outcome of this check, the status of the document is updated,
either to “approved” or “rejected”. If the order is approved, an
invoice and a shipment notice are produced. The order is then
archived on the Orders DB.

Business Objects in BPMN
A Data Object captures an artifact required
(input) or produced (output) by an activity.
▪ Can be physical or electronic
44
P u rc h a s
o rd e r
e
in
Ev mo it
ic e
In v o ic e
A Data Store is a place containing data
objects that must be persisted beyond the
duration of a process instance.
Oracle CRM Client info
It is used by an activity to store (as output)
Retrieve client
information
or retrieve (as input) data objects.

Solution
Invoice
P u r c h aev sre e
P u r c h aev sre e
Op rdr
Op r dr
[a p o d ]
[a p o d ]
| Purchase | Purchase |     | Send    |     |
| -------- | -------- | --- | ------- | --- |
| Order    | Order    |     | invoice |     |
[checked]
|     |          | Confirm  |     | Archive |
| --- | -------- | -------- | --- | ------- |
|     | Items in | order    |     | order   |
stock Order
fulfilled
Check stock
Ship goods
availability
Purchase
| order    | Items not in  |     |     |     |
| -------- | ------------- | --- | --- | --- |
| received | stock         |     |     |     |
Reject order
|     |     | Order |     | Orders DB |
| --- | --- | ----- | --- | --------- |
Shipment
rejected
notice
Warehouse DB
P uOe r c h a s e
rd e r
[r je c te d ]
The purchase order document serves as an input to the stock availability check against the Warehouse
DB. Based on the outcome of this check, the status of the document is updated, either to “approved” or
“rejected”. If the order is approved, an invoice and a shipment notice are produced. The order is then
archived on the Orders DB.
45

Do data objects affect the token flow?

Exercise 3.5
Is there any missing data
object or data store in the
example below?

Do we always need to model data objects?

BPMN Text Annotations
A Text Annotation is a mechanism to provide additional text information to the model
reader
▪ Doesn’t affect the flow of tokens through the process
For blocked invoices
Clear vendor
line items
49
S h i p g o o
I
d
n
s
c lu d e s p a c k a g in g

Exercise 3.6
Put together the four fragments of the loan assessment process that
you created in Exercises 3.1–3.4.
Hint. Look at the labels of the start and end events to understand the order
dependencies among the various fragments. Then extend the resulting
model by adding all the required business objects. Moreover, attach
annotations to specify the business rules behind i) checking an application
completeness, ii) assessing an application eligibility, and iii) verifying a
repayment agreement.

Chapter 3: Essential Process Modeling
Contents
1. First Steps with BPMN
2. Branching and Merging
3. Business Objects
4. Resources
5. Process Decomposition
6. Process Model Reuse
7. Recap

Resources
52

Resources
Active resources:
▪ Process participant
▪ Software system
▪ Equipment
Resource class:
A group of (active) resources that are interchangeable, e.g. a role, an
organizational unit or the whole organization.
53

Resources in the order-to-cash example
The order-to-cash process is carried out by a seller’s organization which
includes two departments: the Sales department and the Warehouse &
Distribution department.
The purchase order received by the Seller has to be checked against the
stock. This is done via an ERP module within the Warehouse &
Distribution department.
If the purchase order is confirmed, the Warehouse & Distribution
department ships the goods. Meantime, the Sales department emits the
invoice. The process concludes with the order being archived by the Sales
department.
54

BPMN Elements – Pools & Lanes
Pool
Captures a resource class. Generally used to model a business party (e.g. a
whole company)
55
looP
looP
Lane
Captures a resource sub-class within a resource class by partitioning a pool.
Generally used to model departments (e.g. shipping, finance), internal roles (e.g.
Manager, Associate), software systems (e.g. DBMS, CRM) or equipment (e.g.
Manufacturing plant)
Lane
Lane
Lane
Lane

Solution: Order-to-cash
14

Exercise 3.7
Extend the business process for assessing loan applications that you
created in Exercise 3.6 by considering the following resource
aspects.
The process for assessing loan applications is executed by four roles within
the loan provider: a financial officer takes care of checking the applicant’s
credit history; a property appraiser is responsible for appraising the property;
an insurance sales representative sends the home insurance quote to the
applicant if this is required. All other activities are performed by the loan
officer who is the main point of contact with the applicant.

Exchanging information between business parties
Order-to-cash
The purchase order sent by the Customer is received by the Seller and
checked against the stock. This is done via an ERP module within the
Warehouse & Distribution department. If the purchase order is not
confirmed, the Sales department sends an order rejection to the
Customer, otherwise it sends an order confirmation.
Next, the Warehouse & Distribution department ships the goods and sends
a shipment notification to the Customer. Meantime, the Sales department
emits the invoice and sends it to the Customer. The process concludes
with the order being archived by the Sales department.
58

BPMN Elements – Message Flow
A Message Flow represents a flow of information or materials between
two process parties (Pools)
M e s s a g e
A Message Flow can connect:
• directly to the boundary of a Pool ➔ captures a message to/from that party
• to a specific activity or event within that Pool ➔ captures a message that triggers a
specific activity/event within that party
Pool 2 2
lo Receive
o
P
1
lo
o
Send Receive 1
lo Send
P o
P
59

BPMN Elements – Start Message Event
The start message event triggers a process by the receipt of a message
when an incoming message flow is connected to the event
Message
Message
received
60

Solution: Order-to-cash
61

Pools, Lanes and Message Flows: syntax
1. The Sequence Flow cannot cross the boundaries of a Pool
2. Both Sequence Flow and Message Flow can cross the boundaries of Lanes
3. A Message Flow cannot connect two flow elements within the same pool
19

Black box or white box?

When are messages sent or received?
• A Send activity will send the outgoing message upon activity
completion
• A Receive activity won’t start until the incoming message has been
received
Note: the order of the message flows w.r.t. an activity is irrelevant, the
above rules always hold
64
P o o l 2 2
lo
o
P
1
lo
o lo
1
P o
P
S e n d
Receive
Send Receive

When are messages sent or received?
• Message B is first received
before Activity can start.
• Message A is sent after,
upon Activity’s completion
• First, message B is
received, before Activity can
start.
• Then, message A is sent,
upon Activity’s completion
65

Process (or Orchestration) Diagram
Models a single business party and can be:
Public view (black box)
ecivreS gninoitcuA
Private view (white box)
e
| c   | Conduct auction |     |     |
| --- | --------------- | --- | --- |
iv
re
| S   | Send auction  | Send auction  | Send auction  |
| --- | ------------- | ------------- | ------------- |
 g
| n   | creation  | creation  | completion  |
| --- | --------- | --------- | ----------- |
in
|     | confirmation | confirmation | notification |
| --- | ------------ | ------------ | ------------ |
o Auction
itc
u begins
A
66

Collaboration Diagram
Models a global business process between at least two business parties (each
modelled by a Pool)
Send delivery
notification
relle
S
|     | Send auction  |     | Send     | Send         |          |
| --- | ------------- | --- | -------- | ------------ | -------- |
|     | creation      |     | payment  |              |          |
|     | request       |     | details  | payment ack. | Private  |
process
| Auction  |         |     | Auction      |     |     |
| -------- | ------- | --- | ------------ | --- | --- |
| creation | Auction |     | completion   |     |     |
| request  |         |     | notification |     |     |
creation
confirmation Goods
Payment sent
details Payment notification
| e civre |     | Conduct a u c ti o n |     | acknowledgement |     |
| ------- | --- | -------------------- | --- | --------------- | --- |
D e l iv e r y
ackno w l e d g e ment
| S  g  | Send auction         | S e n d   auction    | Send auction         |     |     |
| ----- | -------------------- | -------------------- | -------------------- | --- | --- |
| nin   | c r e a ti o n       | c r e a ti o n       | c o m p l e t i o n  |     |     |
|       | co n f ir m a t io n | co n f ir m a t io n | n o tif ic a t i o n |     |     |
| oitcu | A u                  | c t i o n            |                      |     |     |
b e g i n s
A
|     |     | Bid Bid | Auction |     |     |
| --- | --- | ------- | ------- | --- | --- |
completion
|     |     | acknowledgement | notification |     |     |
| --- | --- | --------------- | ------------ | --- | --- |
re
d
diB
Public
process
67

Exercise 3.8
Extend the model of Exercise 3.7 by representing the interactions
between the loan provider and the applicant.

Chapter 3: Essential Process Modeling
Contents
1. First Steps with BPMN
2. Branching and Merging
3. Business Objects
4. Resources
5. Process Decomposition
6. Process Model Reuse
7. Recap

Process decomposition

Process decomposition
An activity in a process can be decomposed into a “sub-process”
Use this feature to:
1. Improve understanding by breaking down large models
2. Identify parts that should be:
▪ repeated
▪ executed multiple times in parallel
▪ interrupted, or
▪ compensated
TT aa ss kk
S
Cu ob lla
- p
pr
o
sc ee ds
s
E x p a n d e d S u b - p r o c e s s
71
Activities

72
Example: Sub-Process
Invoice Process Process
received Invoice Payment
Process Invoice
no
mismatches
Enter Invoice /
Check Invoice
Credit Note
Mismatches
Details
mismatch
Block Invoice
exists

73
Identify possible sub-processes
Acquire raw materials
Ship and invoice

74
Solution

75
The refactored model

Exercise 3.9
Identify suitable sub-processes in the process for assessing loan ap-
plications modeled in Exercise 3.6.
Hint. Use the building blocks that you created throughout Exercises
3.1–3.4.

77
Imposing order of messages via subprocess
The expanded subprocess for “Activity”

78
Example: Modelling process hierarchies
Process Receive and
Level 3 ...
Inquiry and Validate
Quote Order
...
Level 4 Enter Order Check Credit
Order
received
Clear Order
Credit
...
Level 5 Check Credit available
Record
Contact
customer
Credit not
account rep.
available
(Fragment of the SCOR reference model)

79
Value chain modelling
Chain of (high-level) processes an organization performs in order to achieve a business goal,
e.g. deliver a product or service to the market.
Business
process
“is predecessor
of”

80
Linking value chains with process models
Process
model for
this process
is available

When should we decompose a process model into
sub-processes?

82
Guidelines: modeling levels
Use sub-processes when the model becomes too large:
▪ Hard to understand
▪ Increased error probability
Level 1 – start with value chain
Level 2 – add main decisions and handoffs (lanes)
Level 3+ – add procedural aspects:
▪ Parallel gateways
▪ Data objects, data stores
▪ Exception handling
▪ And as much detail as is relevant
Decomposition drivers:
▪ Logical: group elements meaningfully (e.g. common business object)
▪ Structural: up to 30 nodes (activities, events, gateways)

Chapter 3: Essential Process Modeling
Contents
1. First Steps with BPMN
2. Branching and Merging
3. Business Objects
4. Resources
5. Process Decomposition
6. Process Model Reuse
7. Recap

Embedded or global sub-processes?

Process Reuse
By default, a sub-process is “embedded” into its parent process (i.e. it is stored
within the same file)
In order to maximize reuse, it is possible to “extract” the sub-process and store it as
a separate file in the process model repository
Such a sub-process is called “global” model, and is invoked via a “call” activity
(normal) Call
activity activity

86
Example: process reuse
Call activity is the
default choice to
maximize reusability

Exercise 3.9
Identify suitable sub-processes in the process for assessing loan ap-
plications modeled in Exercise 3.6.
Hint. Use the building blocks that you created throughout Exercises
3.1–3.4.

88
Sub-processes: syntax
Sequence flows cannot cross sub-process boundaries
▪ Use start/end events
Message flows can cross sub-process boundaries
▪ To indicate messages emanating from/incoming into the sub-process
Start with at least one start event
▪ If multiple, first occurring will trigger the sub-process
Finish with at least one end event
▪ The sub-process will complete once all tokens have reached an end event.
May need an (X)OR-split after sub-process to understand what end
event(s) have been reached

89
Example: sub-process with multiple end events
Quote-to-order

Exercise 3.10
Identify suitable sub-processes in the process of Exercise 1.7 (page
30). Among these sub-processes, identify those that are specific to
this process versus those that can potentially be shared with other
processes of the same company.

Chapter 3: Essential Process Modeling
Contents
1. First Steps with BPMN
2. Branching and Merging
3. Business Objects
4. Resources
5. Process Decomposition
6. Process Model Reuse
7. Recap

Recap
1. BPMN activities capture units of work in a process
2. Events define the start and end of a process, and signal something that happens
during the execution of it
3. Gateways model exclusive and inclusive decisions, merges, parallelism and
synchronization, and repetition
4. A process model depicts all the possible ways a given business process can be
executed, while a process instance captures one specific process execution out of all
possible ones
5. Data objects capture a physical or digital business object required to execute an
activity or trigger an event, or that results from the execution of an activity or an event
occurrence
6. Pools generally model resource classes while lanes are used to partition pools
7. Sub-processes represent activities that can be broken down in a number of internal
steps, as compared to tasks, which capture single units of work