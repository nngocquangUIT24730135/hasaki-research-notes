Chapter 4: Advanced Process Modeling
Contents
1. More on Rework and Repetition
2. Handling Events
3. Handling Exceptions
4. Processes and Business Rules
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

Chapter 4: Advanced Process Modeling
Contents
1. More on Rework and Repetition
2. Handling Events
3. Handling Exceptions
4. Processes and Business Rules
5. Recap

More on rework and repetition
XOR-join: entry XOR-split: exit point
point
Structured
cycle (SESE
fragment)
SESE = Single Entry Single Exit fragment, i.e. a fragment delimited by a single entry
node and a single exit node (there are no other incoming arcs into the fragment or
outgoing arcs from the fragment)

Block-structured repetition: Loop Activity
BPMN also provides the loop activity construct to allow the repetition of a task or
sub-process
Task Sub-process
Loop Loop

Example: block-structured repetition
Completion
condition
|             |           |                     |     |                 |            |          | U n til R e | s p o n s e  is  a p | p r o v e d |
| ----------- | --------- | ------------------- | --- | --------------- | ---------- | -------- | ----------- | -------------------- | ----------- |
|             |           |                     |     |                 |            | F in a   | lis e       |                      |             |
|             |           | A s s ig n          |     | I nM v e sisq t | ig a t e   |          |             |                      |             |
|             |           |                     |     |                 |            | MR in is | t e r ia l  |                      |             |
|             |           | M in is t e r ia l  |     | in t            | e r ia l   |          |             |                      |             |
|             |           |                     |     |                 |            | e s p    | o n s e     |                      |             |
|             |           | E n q u ir y        |     | E n u           | ir y       |          |             |                      |             |
| M in isqe t | e r ia l  |                     |     |                 |            |          |             | M in is t            | e r ia l    |
| E n uiv     | ire yd    |                     |     |                 |            |          |             | E n q u              | ir y        |
r e c
f in iliz e d
|     |     |                | P r e p at | rr e    | R e v ie    | wr      |             |     |     |
| --- | --- | -------------- | ---------- | ------- | ----------- | ------- | ----------- | --- | --- |
|     |     |                | MR in is   | e ia l  | MR in isp t | e ia l  |             |     |     |
|     |     |                | e s p o    | n s e   | e s o       | n s e   |             |     |     |
|     | Ev  | ns q u ir y    |            |         |             | R e     | s p o n s e |     |     |
|     | in  | e t ig a t e d |            |         |             | r e v   | ie w e d    |     |     |
Must have a
decision activity

Loop Activity or (Arbitrary) Cycle?

Arbitrary Cycles
Arbitrary = unstructured, i.e. it can have multiple entry and exit nodes (non-SESE).
8
A B
G
C
E
F
D
entry point entry point exit point
exit point
C
E
D

Exercise 4.1
▪ Identify the entry and exit points that delimit the unstructured cycles in the process
model shown below. What are the repetition blocks?

Exercise 4.1
▪ Identify the entry and exit points that delimit the unstructured cycles in the
process model shown below. What are the repetition blocks?
▪ Model the business process shown below using a loop activity.

11
Example: multi-instance activity
Procurement
In procurement, typically a quote is to be obtained from all preferred
suppliers (assumption: five preferred suppliers exist). After all quotes
are received, they are evaluated and the best quote is selected. A
corresponding purchase order is then placed.

12
Solution: without multi-instance activity
Procurement
Obtain Quote
from Supplier A
Obtain Quote
from Supplier B
Obtain Quote Select best
... Place PO ...
from Supplier C quote
Obtain Quote
from Supplier D
Obtain Quote
from Supplier E

Parallel repetition: multi-instance activity
Provides a mechanism to indicate that an activity is executed multiple
times concurrently
Useful when the same activity needs to be executed for multiple entities
or data items, such as:
▪ Request quotes from multiple suppliers
▪ Check the availability for each line item in an order separately
▪ Send and gather questionnaires from multiple witnesses in the context of an
insurance claim
M u lt i-T I na ss tk a n c e
13
Multi-Instance
Sub-process

Solution: with multi-instance activity
. . . O b t a in Q u o t e
F o r e a c
S
h s u
e leq
p
cu
p lie
t b
o t e
r
e s t
P la c e P O . . .
14
Procurement
cardinality

15
Further example: multi-instance activity
Motor insurance claim lodgement
After a car accident, a statement is sought from the witnesses that were
present, in order to lodge the insurance claim. As soon as the first two
statements are received, the claim can be lodged to the insurance
company without waiting for the other statements.

Solution: multi-instance activity
Motor insurance claim lodgement
Multi-instance pool
Data collection
denotes multiple
denotes a set of data
participants of the
objects of the same type
same type
(determines cardinality of
multi-instance activity)
Completion
condition indicates
minimum number of
instances required to
complete
(≤ cardinality)

17
Our order-to-cash example…
now with pools, messages and MI markers

Exercise 4.2
Model the following process fragment.
After a car accident, a statement is sought from two witnesses out of
the five that were present in order to lodge the insurance claim. As
soon as the first two statements are received, the claim can be
lodged with the insurance company without waiting for the other
statements

Uncontrolled Repetition: Ad-hoc sub-process
Contains activities to be executed in arbitrary order and number of times
May define order of sub-set of activities by sequence flow
Completion
Can be used in an early version of a process diagram
condition
when the order of execution is still unknown
Until all KPIs reviewed

Example: Ad-hoc sub-process
20

21
Exercise 4.3: Army recruitment
Model the following process snippet.
A typical army selection process starts by shortlisting all candidates’ applications.
Those shortlisted are then called to sit the following tests: drug and alcohol, eye,
color vision, hearing, blood, urine, weight, fingerprinting and doctor examination.
The color vision can only be done after the eye test, while the doctor examination
can only be done after color vision, hearing, blood, urine and weight have been
tested. Moreover, it may be required for some candidates to repeat some of
these tests multiple times in order to get a correct assessment, e.g. the blood
test may need be repeated if the candidate has taken too much sugar in the
previous 24 hours. The candidates that pass all tests are asked to sit a mental
exam and a physical exam, followed by an interview. Only those that also pass
these two exams and perform well in the interview can be recruited in the army.

Chapter 4: Advanced Process Modeling
Contents
1. More on Rework and Repetition
2. Handling Events
3. Handling Exceptions
4. Processes and Business Rules
5. Recap

23
How do we model this scenario?
PO handling
A Purchase Order (PO) handling process starts when a PO is received.
The PO is first registered. If the current date is not a working day, the
process waits until the following working day before proceeding.
Otherwise, an availability check is performed and a PO response is sent
back to the customer.

24
Events handling
In BPMN, events model something instantaneous happening during the execution
of a process
They affect the process flow:
▪ Start
▪ Intermediate
▪ End

25
BPMN event types
| S t a r t | I n t e r m e d i a t e | E n d |           |                   |                     |                     |                   |                   |       |
| --------- | ----------------------- | ----- | --------- | ----------------- | ------------------- | ------------------- | ----------------- | ----------------- | ----- |
|           |                         |       | Upw n t y | p e d   E v e     | n t   –   I n d i c | a t e s   t h a     | t   a n   i n s t | a n c e   o f   t | h e   |
|           |                         |       | r o c e   | s s   i s   c r e | a t e d   ( s t a   | r t )   o r   c o m | p l e t e d       | ( e n d ) ,       |       |
i t h o u t   s p e c i f y i n g   t h e   c a u s e   f o r   c r e a t i o n / c o m p l e t i o n C a t c h i n g
|     |     |     | Sor t a r t  |   M e s s a g         | e   E v e n t       | –   I n d i c a   | t e s   t h a t   a | n   i n s t a n     | c e        |
| --- | --- | --- | ------------ | --------------------- | ------------------- | ----------------- | ------------------- | ------------------- | ---------- |
|     |     |     | f   t h e    |   p r o c e s s       |   i s   c r e a t e | d   w h e n       |   a   m e s s a     | g e   i s           |            |
|     |     |     | e c e i      | v e d                 |                     |                   |                     |                     |            |
|     |     |     | Et n d       | M e s s a g e         |   E v e n t   –     |   I n d i c a t e | s   t h a t   a     | n   i n s t a n c   | en   o f   |
|     |     |     | h e   p      | r o c e s s   i s     |   c o m p l e t     | e d   w h e n     |   a   m e s s       | a g e   i s   s e   | t          |
|     |     |     | Iees n t e r | m e d i a t e         |   M e s s a g       | e   E v e n t     | –   I n d i c a     | t e s   t h a t   a | nho  e     |
|     |     |     | v e n        | t   i s   e x p e c   | t e d   t o   o c   | c u r   d u r i   | n g   t h e   p     | r o c e s s .   T   |            |
|     |     |     | v e n        | t   i s   t r i g g e | r e d   w h e n     |   a   m e s s     | a g e   i s   r     | e c e i v e d       | r          |
e n t

Example: message events
Court
Administra-
tion
P&E Court Listings
For all Judges
Check P&E Judge Availability
|     | Check Court  | Request  |     | Court Calendar | Change P&E  |     |
| --- | ------------ | -------- | --- | -------------- | ----------- | --- |
Change Request
|                | Calendar | Sittings List |               |     | Schedules |          |
| -------------- | -------- | ------------- | ------------- | --- | --------- | -------- |
| Court Calendar |          |               | Sittings List |     |           | Yearly   |
| Received       |          |               | Received      |     |           | Schedule |
Sent
Judiciary
| Start event |     | Intermediate  |     |     | End event |     |
| ----------- | --- | ------------- | --- | --- | --------- | --- |
Resolve P&E
Judge
| (receive) |     | catching event |     |     | (send) |     |
| --------- | --- | -------------- | --- | --- | ------ | --- |
Availability
(receive)

Comparison with sending/receiving tasks
R e
in
c e
v o
iv e
ic e
Send invoice
r
In v o ic e
e c e iv e d
In v o ic e
s e n t
S e n d in v o ic e
=
=
Invoice
sent
=
≠ Receive
invoice
Invoice
received

So, when to use what?
Use message events only when the corresponding activity would simply send or
receive a message and do nothing else

Typed or Untyped Event?

Exercise 4.4
Is there any other activity in the loan assessment model below that can be replaced
by a message event?

Start Timer Event – Indicates that an instance of the
process is created at certain date(s)/time(s), e.g. start
process at 6pm every Friday
Intermediate Timer Event – Triggered at certain date(s)/
time(s), or after a time interval has elapsed since the
moment the event is enabled (delay)
S t a r t I n t e r m e d i a t e E n d
Temporal events

Example: temporal events
In a small claims tribunal, callovers occur once a month to set down the
matter for the upcoming trials. The process for setting up a callover starts
three weeks prior to the callover day, with the preparation of the callover
list containing information such as contact details of the involved parties
and estimated hearing date. One week prior to the callover, the involved
parties are notified of the callover date. Finally, on the callover day, the
callover material is prepared and the callover is held.
Pcm r e p avr r e
|     | Pa r e p a r e   |     | Cp oa nr ta cs t  |     | Ha o ldv |     |
| --- | ---------------- | --- | ----------------- | --- | -------- | --- |
a llo e r
|     | c llo v e r  lis | t   | tie |     | c llo e r |     |
| --- | ---------------- | --- | --- | --- | --------- | --- |
a te ia l
3  wto e e k s  p rio r  1  w e e k  p rio r  c a llo v e r d a y c a llo vld e r
|  c ad llo v e r  |     | to  c a llo v e r  |     |                |     | h e |
| ---------------- | --- | ------------------ | --- | -------------- | --- | --- |
| a y              |     | d a y              |     |                |     |     |
| Start            |     | Intermediate       |     | Intermediate   |     |     |
| event            |     | catching event     |     | catching event |     |     |

Coming back to our scenario…
PO handling
A Purchase Order (PO) handling process starts when a PO is received.
The PO is first registered. If the current date is not a working day, the
process waits until the following working day before proceeding.
Otherwise, an availability check is performed and a PO response is sent
back to the customer.
Next working day
weekend/
holiday
weekday Check Send PO
Register PO
Availability Response
PO PO
Received fulfilled

Multiple start events
The first start event that occurs will trigger an instance of the process
PO Response
Received
Process PO
Response
Error Message
Received
Notify
Friday Purchasing
afternoon Officer

35
Exercise 4.4: Internet Service Provider
Model the billing process of an Internet Service Provider (ISP).
The ISP sends an invoice by email to the customer on the first working day of
each month (Day 1). On Day 7, the customer has the full outstanding amount
automatically debited from its bank account. If an automatic transaction fails for
any reason, the customer is notified on Day 8. On Day 9, the transaction that
failed on Day 7 is re-attempted. If it fails again, on Day 10 a late fee is charged to
the customer’s bank account. At this stage, the automatic payment is no longer
attempted. On Day 14, the Internet service is suspended until payment is
received. If the payment is still outstanding on Day 30, the account is closed and
a disconnection fee is applied. A debt-recovery procedure is then started.

36
Racing events: Event-based decision
With the XOR-split gateway, a branch is chosen based on conditions
that evaluate over available data
→ The choice can be made immediately after the token arrives from
the incoming flow
Sometimes, the choice must be delayed until an event happens
→ The choice is based on a race among events
Two types of XOR split:
data-driven event-driven
XOR-split XOR split

Example: Event-based decision
37

Exercise 4.6: Stock replenishment
Model the following process.
A restaurant chain submits a purchase order (PO) to replenish its warehouses
every Thursday. The restaurant chain’s procurement system expects to receive
either a “PO Response” or an error message. However, it may also happen that
no response is received at all due to system errors or due to delays in handling
the PO on the supplier’s side. If no response is received by Friday afternoon or if
an error message is received, a purchasing officer at the restaurant chain’s
headquarters should be notified. Otherwise, the PO Response is processed
normally.

Matching choices in different business parties
Lead-to-Quote
Matching a
data-driven
choice at Client

19
What’s wrong with this collaboration diagram?
Auction creation

Solution
Auction creation

Exercise 4.7
Fix the following
collaboration diagram.

Recap: message and timer events
Start Intermediate End
Catching Throwing
Untyped: indicate start point,
state changes or final states.
Message: Receiving and
sending messages.
Timer: Cyclic timer events,
points in time, time spans or
timeouts.

Chapter 4: Advanced Process Modeling
Contents
1. More on Rework and Repetition
2. Handling Events
3. Handling Exceptions
4. Processes and Business Rules
5. Recap

45
Process abortion
Exceptions are events that deviate a process from its normal course
The simplest form of exception is to notify that there is an exception
(negative outcome)
This can be done via the Terminate end event: it forces the whole
process to abort ( wipes off all tokens left behind, if any)

46
Example 1: terminate event
Signal the negative outcome…

47
Example 2: terminate event
Abort the process by removing all tokens…

Exercise 4.8
Revise the examples presented so far by using the terminate event
appropriately.

49
Exception handling
Handling exceptions often involves stopping a sub-process and performing a special activity
Types of exceptions for an activity (task/sub-process):
Internal: something goes wrong inside an activity, whose execution must
thus be interrupted. Handled with the Error event
External: something goes wrong outside the process, and the execution
of the current activity must be interrupted. Handled with the Message
event
Timeout: an activity takes too long and must be interrupted. Handled
with the Timer event
All these events are catching intermediate events. They stop the enclosing activity and
start an exception handling routine.

Eew r r o
r r o
h e
rn
r
e
E
a
v
ve
t t
en
a
nt
c h
tw
e
–hd I n
i l e
t o
d
t
iht c
h
ae
e
t e
c
b
sao at
c
u
nh
n
ei
n
d a
rgr r o
y
r
i n
o
: t h
t e r
f a
emn
e
a
edc n d
i at
i v
t
v
e
i t y
e
v
re s
r
i os ni
o
gn e
c
no en rs au t em se as n
i t
50
Internal exception: error event
Start Intermediate End
Must be attached to
the activity’s boundary

51
Example: internal exception
PO handling
Consider again our  PO Handling process  example with the following extension:
if an item is not available, any processing related to the PO must be stopped.
Thereafter, the client needs to be notified that the PO cannot be further
processed.
Handle PO
Next workingN deaxyt working day
weekend/ weekend/
|     | holiday holiday |                |                 |          |     |
| --- | --------------- | -------------- | --------------- | -------- | --- |
|     | weekday         | weekday Check  | Check  Send PO  | Send PO  |     |
RReeggiisstteerr  PPOO
|     |     | Availability | AvailabilityResponse | Response |     |
| --- | --- | ------------ | -------------------- | -------- | --- |
PO
| PPOO             |            |     |     | PO Response | PO        |
| ---------------- | ---------- | --- | --- | ----------- | --------- |
| RReecceeiivveedd | Registered |     |     |             | fulfilled |
fulfilled sent

52
Solution: internal exception
Throwing and catching
error events must have
the same label
PO handling
H a n d le  P O
Handle PO
|                        | N Next working day e x t w o rk | in g  d a y | Ite m s  n o t  |     |     |
| ---------------------- | ------------------------------- | ----------- | --------------- | --- | --- |
| w weekend/ e e k e n d | /                               |             | a v a ila b le  |     |     |
h holiday o lid a y
|     |     | Cv h Check  e cb k   | Send PO  | SR e n d  P O   |     |
| --- | --- | -------------------- | -------- | --------------- | --- |
w weekday e e k d a y
Register PO R e g is te r P O
|     |     | A a Availability ila ility | Ite Response m s | e s p o n s e |     |
| --- | --- | -------------------------- | ---------------- | ------------- | --- |
PO P O PO P O
| PO Pc Oe |     |     | a v a ila b le | Response R e s | p o n s e |
| -------- | --- | --- | -------------- | -------------- | --------- |
Registered R e g is te re d fulfilled fu lfille d
| Received R e iv e d |     |     |     | sent s | e n t |
| ------------------- | --- | --- | --- | ------ | ----- |
Ite m s  n o t
a v a ila b le
|     |     |     |     | N o tific a | tio n |
| --- | --- | --- | --- | ----------- | ----- |
s e n t
Must catch an error
event thrown from
|     |     |     | within | the same  |     |
| --- | --- | --- | ------ | --------- | --- |
activity

53
One more example: internal exception
Extend the claim handling process shown below as follows:
After checking the insurance policy, a possible outcome is that the
insurance is invalid. In this case, any processing is cancelled and a letter
is sent to the customer. In the case of a complex claim, this implies that
the damage checking is cancelled if it has not yet been completed.
simple or
Check Policy
complex
claim
Classify Claim
Claim Claim
received complex checked
Check Damage
claim

54
Solution: internal exception
rr
CCe
c e c
lalaee imim
iviv ee dd
CC lala ss ss ify ify C C lala imim
C
nc
h e c
C la
e e d
la s s
k in s u r a n
s im p le o r
c o m p le x
c la im
ims
b e c o m p le x
ifie dc la im
c e
c o
sm
c
im p Cp
le
o m C h
c la
le o r h e c k P
x c la im
p le x e c k D a
im
o
m
lic
a
y
g e C
C
h
h
e
e
c
c
k
k P
D a
o
m
lic
a
y
g e c
Ch la
e c
imk
e d
Inc sh ue r ac
k
ne cd e
c
Ch la
e c
imk
e d
Check insurance
Policy is
invalid invalid
policy
simple or Check Policy
complex claim
valid
policy
Classify Claim
Claim Claim Insurance Claim
received needs be checked checked complex Check Damage
classified claim
Policy is
invalid
Notify
Customer
Claim
rejected

55
Example: external exception
PO handling
A PO change request may be received anytime after the PO is registered.
This request includes a change in quantity or line items. When such a
request is received, any processing related to the PO must be stopped.
The PO change request is then registered. Thereafter, the process
proceeds as it would do after a normal PO is registered. Further, if the
customer sends a PO cancelation request after the PO registration, the
PO processing must be stopped and the cancelation request must be
handled.
Next working day
weekend/
holiday
weekday Check Send PO
Register PO
Availability Response
PO PO
Received fulfilled

Solution: external exception
PO handling
H a n d le  P O
|     |                              |                 | N e x t w     | o rk in g N  d e a xy | t w o rk in g  d  | a y             |                 |                 |     |     |
| --- | ---------------------------- | --------------- | ------------- | --------------------- | ----------------- | --------------- | --------------- | --------------- | --- | --- |
|     |                              | w e e k e n d / | w e e k e     | n d /                 |                   |                 |                 |                 |     |     |
|     |                              | h o lid a y     | h o lid a     | y                     |                   |                 |                 |                 |     |     |
|     |                              |                 |               |                       | C h e c k         |   Cv h e cb k   | S e n d  P O    | SR e n d  P O   |     |     |
|     | RR ee gg iiss ttee rr  PP OO |                 | w e e k d a y | w e e k d a           | y                 |                 |                 |                 |     |     |
|     |                              |                 |               |                       | A v a ila b ility | A a ila ility   | R e s p o n s e | e s p o n s e   |     |     |
P O
| PPcc OOee        |     |             |      |              |            |         |                  | P O         | R e ss pe on nt s e | P O         |
| ---------------- | --- | ----------- | ---- | ------------ | ---------- | ------- | ---------------- | ----------- | ------------------- | ----------- |
| RR ee iivv ee dd |     | R e g is te | re d |              |            |         |                  | fu lfille d |                     | fu lfille d |
|                  |     |             | P O  |  C h a n g e | P O  C a   | n c e l |                  |             |                     |             |
|                  |     |             | r e  | c e iv e d   | r e c e iv | e d     |                  |             |                     |             |
|                  |     |             |      |              |            |         | HC a n d le  P O |             |                     |             |
a n c e la tio n
|     |     | R   | e g is te r  P O |     |     |     |     |     |     |     |
| --- | --- | --- | ---------------- | --- | --- | --- | --- | --- | --- | --- |
P O
|     |     |     | C h a n g e |     |     |     |     |     |     |     |
| --- | --- | --- | ----------- | --- | --- | --- | --- | --- | --- | --- |
c a n c e le d
8

Exercise 4.9
Model the following routine for accessing an Internet bank service.
The routine for logging into an Internet bank account starts once the credentials entered from
the user have been retrieved. First, the username is validated. If the username is not valid, the
routine is interrupted and the invalid username is logged. If the username is valid, the number
of password trials is set to zero. Then, the password is validated. If this is not valid, the
counter for the number of trials is incremented and if lower than three, the user is asked to
enter the password again, this time together with a CAPTCHA test to increase the security
level. If the number of failed attempts reaches three times, the routine is interrupted and the
account is frozen. Moreover, the username and password validation may be interrupted
should the validation server not be available. Similarly, the server to test the CAPTCHA may
not be available at the time of log in. In these cases, the procedure is interrupted after
notifying the user to try again later. At any time during the log in routine, the customer may
close the web page, resulting in the interruption of the routine.

Exercise 4.10: activity timeout
Order-to-transportation quote
Once a wholesale order has been confirmed, the supplier transmits this order to
the carrier for the preparation of the transportation quote. In order to prepare the
quote, the carrier needs to compute the route plan (including all track points that
need to be traversed during the travel) and estimate the trailer usage.
By contract, wholesale orders have to be dispatched within four days from the
receipt of the order. This implies that transportation quotes have to be prepared
within 48 hours from the receipt of the order to remain within the terms of the
contract.

Solution: activity timeout
Order-to-transportation quote

60
Example: Non-interrupting boundary events
PO handling
H a n d le  P O
|     |     | N e x t w o rk | in g  d a y | Ite m s  n o t  |     |
| --- | --- | -------------- | ----------- | --------------- | --- |
a v a ila b le
|     | w e e k e | n d / |     |     |     |
| --- | --------- | ----- | --- | --- | --- |
h o lid a y
|     |     | w e e k d a y | C h e c k   |     | S e n d  P Os  e |
| --- | --- | ------------- | ----------- | --- | ---------------- |
R e g is te r P O
|     |     |     | A v a ila b ility |     | R e s p o n |
| --- | --- | --- | ----------------- | --- | ----------- |
Ite m s
P O P O
| Pc Oe |     |     |     | a v a ila b le | R e ss pe on nt s e |
| ----- | --- | --- | --- | -------------- | ------------------- |
R e g is te re d
R e iv e d fu lfille d
|     | P Ore  C h a n | g e P Ore  Cc a n c e l |     | Ite m s  n o t  |     |
| --- | -------------- | ----------------------- | --- | --------------- | --- |
|     | c e iv e       | d e iv e d              |     | a v a ila b le  |     |
HC aa n d le  P O
n c e la tio n
R e g is te r  P O
P O
N o tific a tio n
C h a n g e
|     |     |     | c a n | c e le d | s e n t |
| --- | --- | --- | ----- | -------- | ------- |
The customer may send a request for address change after the PO registration. When such
a request is received, it is just registered, without further action.

61
Non-interrupting boundary events
Sometimes we may need to trigger an activity in parallel to the normal
flow, i.e. without interrupting the normal flow.
This can be achieved by using non-interrupting boundary events
Must be attached to
the activity’s boundary

62
Solution: non-interrupting boundary events
PO handling
H a n d le  P O
|     |           | N e x t w o rk | in g  d a y | Ite m s  n o t  |     |     |
| --- | --------- | -------------- | ----------- | --------------- | --- | --- |
|     | w e e k e | n d /          |             | a v a ila b le  |     |     |
h o lid a y
|     |     | w e e k d a y | Cv h e cb k   |     | SR ee n d  P Os |  e  |
| --- | --- | ------------- | ------------- | --- | --------------- | --- |
R e g is te r P O
|     |     |     | A a ila ility |     | s p o n |     |
| --- | --- | --- | ------------- | --- | ------- | --- |
Ite m s
P O P O
| Pc Oe |     |     |     | a v a ila b le |     | R e ss pe on nt s e |
| ----- | --- | --- | --- | -------------- | --- | ------------------- |
R e g is te re d fu lfille d
R e iv e d
|     |           |                      |     | Items not  |     | Address |
| --- | --------- | -------------------- | --- | ---------- | --- | ------- |
|     | PO Change | P Ore  Cc a n c ed l |     |            |     |         |
change
|     | received | e iv e |                   | available |     |          |
| --- | -------- | ------ | ----------------- | --------- | --- | -------- |
|     |          |        | HC aa n d le  P O |           |     | received |
n c e la tio n
|     | Register PO  |     |     |     |     | Update  |
| --- | ------------ | --- | --- | --- | --- | ------- |
P O
|     | Change |     |     |     | Notification | customer  |
| --- | ------ | --- | --- | --- | ------------ | --------- |
c a n c e le d
sent
address
Customer
address
updated

Exercise 4.11
Consider the process for assessing loan applications below.

Exercise 4.11
Extend this process as follows.
An applicant who has decided not to combine the loan with a home insurance
plan may change its mind any time before the eligibility assessment has been
completed. If a request for adding an insurance plan is received during this
period, the loan provider will simply update the loan application with this request.

65
Complex Exceptions
PO handling
[[……]] FFuurrtthheerr,, iiff tthhee ccuussttoommeerr sseennddss aa PPOO ccaanncceellaattiioonn rreeqquueesstt aafftteerr tthhee
PO registration, the PO processing must be stopped and the change
PO registration, the request is first assessed. Based on the progress of
request needs to be handled.
the order handling (e.g. if items have already been fetched from
external warehouses) a penalty is determined and communicated to
the customer. The customer has 48 hours to accept the penalty and go
on with the cancelation or to stop the cancelation and continue with the
order handling.

Complex Exceptions: Signal event
• To send or receive a signal for synchronization purposes
• A signal is broadcasted without any specific target. Thus it can be
caught multiple times
• Signals are different than messages which are routed to a specific
target
| S t a r t | I n t e r m e    | d i a t e E n d |
| --------- | ---------------- | --------------- |
|           | C a t c h in g T | h r o w in g    |
Can be attached to the
activity’s boundary

Solution: non-interrupting event + signal event
PO handling
H a n d le  P O
|                   |     | N e x t w       | o rk in g  d a y |           | Ite m s  n  | o t       |          |     |
| ----------------- | --- | --------------- | ---------------- | --------- | ----------- | --------- | -------- | --- |
|                   |     | w e e k e n d / |                  |           | a v a ila b | le        |          |     |
|                   |     | h o lid a y     |                  |           |             |           |          |     |
|                   |     |                 | C h              | e cb k    |             | SR ee n d |  P Os  e |     |
|                   |     | w e e k d a y   |                  |           |             |           |          |     |
| R e g is te r P O |     |                 | A v a            | ila ility |             | s p o     | n        |     |
Ite m s
|       | P O              |     |     |     | a v a ila b | le  |                     | P O         |
| ----- | ---------------- | --- | --- | --- | ----------- | --- | ------------------- | ----------- |
| Pc Oe |                  |     |     |     |             |     | R e ss pe on nt s e |             |
|       | R e g is te re d |     |     |     |             |     |                     | fu lfille d |
R e iv e d
P O
|     |     | P Or  Cc a n c e l  | to  b e          |     | Items not  | Broadcasts a signal to all  | Address  |     |
| --- | --- | ------------------- | ---------------- | --- | ---------- | --------------------------- | -------- | --- |
|     |     | P Ore  Cc a n c e l |                  |     |            |                             |          |     |
|     |     | e e iv e d          |                  |     | available  |                             | change   |     |
|     |     | e iv e d            | c a n c e le     | d   |            | catching signal events      |          |     |
|     |     |                     | H a n d le  P O  |     |            |                             | received |     |
|     |     |                     | C a n c e la tio | n   |            |                             |          |     |
bearing same label
|     |     |     | Cp he an r g e   | Hc a n d lela  P | O   |              | Update    |     |
| --- | --- | --- | ---------------- | ---------------- | --- | ------------ | --------- | --- |
|     |     |     |                  | P O              |     | Notification |           |     |
|     |     |     | a lty            | a n c e tio      | n   |              | customer  |     |
c a n c e le d
|     |     |     |     |     | P O | sent | address |     |
| --- | --- | --- | --- | --- | --- | ---- | ------- | --- |
c a n c e le d
|     |     |              |           |              | R     | e q u e s t | Customer  |     |
| --- | --- | ------------ | --------- | ------------ | ----- | ----------- | --------- | --- |
|     |     |              |           |              |       |             | P O       |     |
|     |     |              |           |              | to    |  s to p     | address   |     |
|     |     |              |           |              |       |             | to  b ele |     |
|     |     |              |           |              | r e   | c e iv e d  | updated   |     |
|     |     |              |           |              |       | c           | a n c e d |     |
|     |     | D e te r m   | in e Np   | o tify       |       |             |           |     |
|     |     | c a n c e la | tio n     | e n a lty    |       |             |           |     |
|     |     | p e n a      | lty to  c | u s to m e r |       |             |           |     |
|     |     |              |           |              | R     | e q u e s t | Pnc Ooa   |     |
|     |     |              |           |              | to  c | o n tin u e | tn        |     |
|     |     |              |           |              | r e   | c e iv e d  | c e le d  |     |
|     |     |              |           |              | 4 8   |  h o u r s  |           |     |

To handle events that may not refer to a particular task/ sub-process within a
process
▪ Placed into a process or subprocess
▪ Is activated when its start event is triggered
▪ It may or may not interrupt the parent process or sub-process, depending on
the type of its start event:
▪ Non-Interrupting:
▪ Interrupting:
S u b
E- vP er
+
no tc
e s s
E v e n t S u b -P ro c e s s
Event sub-process

Example: event sub-process
PO handling
Handle PO H a n d le  P O
|     |                        | Next working day N e x t w o rk | in g  d a y   |        | Items not  Ite m s  n o t  |                          |     |     |
| --- | ---------------------- | ------------------------------- | ------------- | ------ | -------------------------- | ------------------------ | --- | --- |
|     | weekend/ w e e k e n d | /                               |               |        | available a v a ila b le   |                          |     |     |
|     | holiday h o lid a y    |                                 |               |        |                            |                          |     |     |
|     |                        |                                 | Cv Check  h e | cb k   |                            | SR Send PO  ee n d  P Os |  e  |     |
weekday w e e k d a y
| Register PO R e g is te r P O |                             |     | Availability |       |                | Response |                              |                       |
| ----------------------------- | --------------------------- | --- | ------------ | ----- | -------------- | -------- | ---------------------------- | --------------------- |
|                               |                             |     | A a ila      | ility | Items Ite m s  | s p o n  |                              |                       |
|                               | PO P O                      |     |              |       | available      |          |                              | PO P O                |
| Pc PO Oe                      |                             |     |              |       | a v a ila b le |          | Response R e ss pe on nt s e |                       |
|                               | Registered R e g is te re d |     |              |       |                |          |                              | fulfilled fu lfille d |
| Received R e iv e d           |                             |     |              |       |                |          | sent                         |                       |
Handle PO
Cancelation
|     | PO Cancel |     | PO  | Items | Notification |     |     |     |
| --- | --------- | --- | --- | ----- | ------------ | --- | --- | --- |
Only receptive of events
|     | received |     | canceled | not available | sent |     |     |     |
| --- | -------- | --- | -------- | ------------- | ---- | --- | --- | --- |
occurring during the
execution of the enclosing
Update
sub-process
customer
address
Address
Customer
|     | change received |     | address updated |     |     |     |     |     |
| --- | --------------- | --- | --------------- | --- | --- | --- | --- | --- |
Handle
PO Change
PO
received
inquiry
PO Inquiry
PO
handled
|     | Register PO  |     |     | Inquiry  |     |     |     |     |
| --- | ------------ | --- | --- | -------- | --- | --- | --- | --- |
|     | Change       |     |     | received |     |     |     |     |

Event sub-processes or boundary events?

Exercise 4.12
Model the following business process for reimbursing expenses.
After an expense report is received from an employee, the employee is notified of
the receipt of the report. Next, a new account must be created if the employee
does not already have one. The report is then reviewed for automatic approval.
Amounts under EUR 1,000 are automatically approved while amounts equal to or
over EUR 1,000 require manual approval. In case of rejection, the employee must
receive a rejection notice by email. In case of approval, the reimbursement is
deposited directly to the employee's bank account and an approval notice is sent
to the employee via email, with the details of the money transfer. At any time
during the review, the employee can send a request for amount rectification. In
that case the rectification is registered and the report needs to be reviewed again.
Moreover, if the report is not handled within 30 days, the process is stopped and
the employee receives a cancelation notice email so that he can resubmit the
expense report from scratch.

72
Example: activity compensation
PO handling
After a PO has been registered, checked, and a response has been sent
back, a payment sub-process and a fulfilment sub-process are started.
During these two sub-processes, a PO cancellation may be received
from the customer. In this case, both sub-processes are stopped, and
their effects are reverted (e.g. reimbursement and/or goods return may
need to occur).

73
Activity compensation
▪ Rollback of completed process activities
▪ May be used as part of an exception handling procedure
▪ Triggered by throwing Compensate event
▪ Compensation Handler (a catching Compensate event + a Compensate activity)
performs the rollback
Compensation
handler

74
Solution: activity compensation
The compensate
activity can be a
PO handling
sub-process
Fulfil and Pay PO
Payment
Cancel PO
Re-
imbursement
Handle PO
+
PO Received PO
Fulfillment fulfilled
and paid
Only one compensate
activity must be linked Cancel PO
Goods return
from a catching
compensate event
PO Cancel received
Cancel PO

75
Compensate event
• Indicates that the enclosing activity must be compensated
• The  throwing intermediate  and the  end  version generate the
compensation event
• The  intermediate catching  version triggers the compensation when
attached to the boundary of an activity
Start Intermediate End
C a t c h in g T h r o w in g
| Ccgv o m  | p e n sa  athn t ed u |   E v e n t               |               |                     |
| --------- | --------------------- | ------------------------- | ------------- | ------------------- |
| oee mnr p | e n s ees             |                           |               |                     |
| e         | ro a t e t            | c o me p ei n s a t i o n |   e v e n t   | w h i l e   t h e   |
| s i       | n   c o               | m s   t                   |               |                     |
Must be attached to the
activity’s boundary

Exercise 4.13
Modify the model created in Exercise 4.13 as follows.
If the report is not handled within 30 days, the process is stopped, the
employee receives a cancelation notice email and must resubmit the
expense report. However, if the reimbursement for the employee’s expenses
had already been made, a money recall needs to be made, to get the money
back from the employee, before sending the cancelation notice email.

77
Recap: Events
| Start | Intermediate | End |
| ----- | ------------ | --- |
-
g ng
|     |  y n o n g  |     |
| --- | ----------- | --- |
| g   | r it N it n |     |
| n   | a  y iw     |     |
ih d p p
nr u r u
| c   | ur ar o       |     |
| --- | ------------- | --- |
| t a | e dr e r      |     |
| C   | o n h         |     |
|     | B t n u t n T |     |
o
I BI
Untyped: indicate start point,
state changes or final states.
Message: Receiving and
sending messages.
Timer: Cyclic timer events,
points in time, time spans or
timeouts.
Signal: Signalling across
different processes. A signal
can be caught multiple times.
Error: Catching or throwing
named errors.
Compensate: Handling or
triggering compensation.
Terminate: Triggering the
immediate termination of a
process.

Chapter 4: Advanced Process Modeling
Contents
1. More on Rework and Repetition
2. Handling Events
3. Handling Exceptions
4. Processes and Business Rules
5. Recap

79
Processes and Business Rules
• Business rules implement organizational policies or practices
• Example: in an online shop platinum customers have a 20% discount
for purchases over EUR 250.
• In BPMN, business rules can be captured via:
• Decision activities
• Conditions on outgoing arcs of (X)OR-split
• Conditional events

Example: conditional event
Replenishment order
80

Exercise 4.14
Model the following business process snippet.
In a stock exchange, stock price variations are continuously monitored
during the day. A day starts when the opening bell rings and concludes when
the closing bell rings. Between the two bells, every time the stock price
changes by more than 10%, the entity of the change is first determined.
Next, if the change is high, a “high stock price” alert is sent, otherwise a “low
stock price” alert is sent.

Chapter 4: Advanced Process Modeling
Contents
1. More on Rework and Repetition
2. Handling Events
3. Handling Exceptions
4. Processes and Business Rules
5. Recap

Recap
1. Structured loops can be modelled with loop activities, but
arbitrary cycles cannot
2. Multi-instance activities model activities that need to be
executed multiple times without a-priori knowledge of their
number
3. Multi-instantiation extends to business objects and resources
4. Intermediate events can either be catching or throwing
5. Message events capture message exchange at the start,
during and at the end of a process
6. Timer events capture temporal events (absolute or periodic)

Recap (cont‘ed)
7. Exceptions can be technology or business based, and either internal,
external or activity timeouts
8. The simplest way to handle exceptions is via process abortion using
terminate events
9. Boundary error events capture internal extensions
10. Boundary message events capture external extensions
11. Boundary timer events capture activity timeouts
12. Signal events broadcast multiple messages and can be used to
capture complex exceptions
13. Compensation events are required to revert the effects of completed
activities
14. Conditional events are one way of capturing business rules