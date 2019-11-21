Experiment #1:
(updated 11/21/2019)

Objective:
Determine what percentage of organizations respond to Privacy Requests and Concerns,
and explore how can this information be used to benchmark and improve privacy practices.


Questions: 
1. Are organizations more likely to respond to privacy questions or privacy concerns?
2. How long does it take for organizations to respond to privacy requests?
3. Who responds to these requests?
4. How relevant are the responses to the requests?
5. How useful is the response to a request?
6. What is the cost in time and other resources for issuing requests, and issuing responses?


Metrics:
Q1. Are organizations more likely to respond to privacy questions or privacy concerns?
a. Remove AutoReplies [AckReceipt, Ticket, FAQs], and [Undeliverable] from total sample
b. Count Questions and Concerns
c. Subtract DNRs from Questions and from Concerns to obtain percentages of each
->  11 DNRs out of 33 total Questions is 33.3% no, 66.6% yes
->   7 DNRs	out of 31 total Concerns  is 22.5% no, 77.5% yes
A1. Organizations are more likely to respond to concerns than questions.

Q2. How long does it take for organizations to respond to privacy requests?
a. Remove NoResponses [Undeliverable and DNR] from total sample
b. Remove AutoReplies [Respondent's Initial Response Date]  received within 5 minutes after [Researcher's Initial Request Date].
c. For each remaining record, subtract [Researcher's Initial Request Date] from [Respondent's Initial Response Date] to obtain difference measured in minutes. 
d. Average all differences.
e. Also document count([Relevance Category] = 'DNR' && [Followup Request Date] IS NULL) as 'No Prompt'.
A2. 5953.7 minutes or 4.3 days average.

Q3. Who responds to these requests?
a. For each response, classify each responder according to these categories: 
      Legal, Privacy, Security, Support, Management, Unknown
   based on individual job title/credentials or email alias or service desk ticket.
b. Count only the responders providing the final coded response.
A3. Unknown = 28%, Support = 26%, Privacy = 23%,  Legal = 13%, Management = 7%, Security = 3%.

Q4. Which class of responder has the highest coded response scores?
a. Remove Final Responder = 'none' (Undeliverable and DNR) from total sample
b. Sort by:
  Final Responder (A-Z),
  Relevance (Descending),
    Usefulness (Descending),
      Effort (Descending).
c. Subtotal numeric scores for each Responder Class, and divide subtotal sum by Responder Class count to derive answer. Highest score wins.
A4.  Security = 6.5, Legal = 6.4, Privacy = 6.05, Unknown = 5.47, Support = 4.68, Management = 4.2

Q5. Did any respondents suffer a data breach Within 10 months after this experiment was initially conducted?
If so, how many? What actions did the respondents take, and did these actions comply with the final coded responses?
A1. [not conducted]

-------------------

Sample:
  100 organizations in 2 categories: 
    Tier 1 represents privacy subject matter experts and leaders. These organizations were selected from vendor listings on the iapp.org website.
    Tier 2 is comprised of San Francisco Bay Area businesses in 9 industry verticals. These businesses were selected from Crunchbase searches, and are categorized in this way:
    a) Marketing Analytics
    b) Finance
    c) Healthcare
    d) Security
    e) Human Resources
    f) Consumer Services
    g) Education
    h) Enterprise Software
    i) Engineering
    
    To qualify for this study, organizations must have an email address in the privacy policy where requests are intended to be received.


Methodology:
  Employ the "mystery shopper" technique used in market research by posing as a data subject exercising their privacy rights according to current applicable laws and organizations' stated privacy policies. When a data subject contacts an organization to request information or take actions regarding their personal data, the request is often referred to as a "Data Subject Access Request", or DSAR, according to privacy professional jargon.

  Half of the organizations receive a Privacy Request:
  "How and when will I be notified if there is a data breach?"

  The other half receive a Privacy Concern:
  "I'm concerned about how and when I'll be notified of a data breach"

  This is designed to discover which kind of inquiries organizations are more likely to respond to.
  Both questions are very specific requests.
  


Premise: 
  Current laws require that data subjects to be notified within a specified time period if their personal information    was breached. It's reasonable to assume this requirement can't be met if a data subject hasn't provided appropriate    contact information.


-------------------

Tools:
  1. curl scripts for getting privacy policies from list of urls
  2. local script for finding company name and mailto contact
    -> example using text search for "contact":
  3. Results
      a. Excel Spreadsheet
      b. Raw Data (csv)
      c. R scripts
      d. Linked Charts

P O P U L A T I O N - ID:   Anonymized Token Identifier
                      URL:  Numeric Identifier of URL targeted in curl script	
                      Tier: 1 for Privacy Subject Matter Experts; 2 for all others
                      Org:  Linked by ID and URL. 
                            (Intentionally not published to protect respondents' privacy.)


FIRST PASS
==========
R E S E A R C H E R - Initial Request Date:   Date/Time of email sent
                      Request Type:           Question or Concern
			
R E S P O N D E N T - Initial Response Type:  (See R E S P O N S E    C O D I N G)
                      Initial Response Date:  Date/Time of email received
                      Initial Responder:      Legal | Privacy | Support | Management | Security | Unknown
                      Initial Response:       Body of email received (redacted)
  
R E S E A R C H E R	- Initial Reply Date:     Date/Time of email sent
                      Initial Reply:          Thanks (if no further action)
                                              or Answers (if Questions were asked by Respondent)


SECOND PASS
==========
R E S E A R C H E R - Followup Request Date:  Date/Time of email sent

R E S P O N D E N T - Second Response Type:   (See R E S P O N S E    C O D I N G)
                      Second Response Date:   Date/Time of email received
                      Second Responder:       Legal | Privacy | Support | Management | Security | Unknown
                      Second Response:        Body of email received (redacted)

R E S E A R C H E R - Second Reply Date:      Date/Time of email sent
                      Initial Reply:          Thanks (if no further action)
                                              or Answers (if Questions were asked by Respondent)
                                              or Resent (in one case only)


THIRD PASS
==========
R E S P O N D E N T - Third Response Type:    (See R E S P O N S E    C O D I N G)
                      Third Response Date:    Date/Time of email received
                      Third Responder:        Legal | Privacy | Support | Management | Security | Unknown
                      Third Response:         Body of email received (redacted)
                      
R E S E A R C H E R - Third Reply Date:       Date/Time of email sent
                      Final Reply:            Thanks 

Privacy Requests are considered to be resolved when the communication exchange ends.
This is represented as the "Final Response", to which the Requestor replies: "Thanks for your response."
This reply is intended to represent that the request has been resolved and no further communication is required.
                      


RESPONSE CODING
===============
R E S P O N S E    C O D I N G -  
  Response Category: Appropriate | DNR | AckReceipt | Questions |                                                                           Undeliverable | Ticket | FAQs | Inappropriate
  Each response is categorized and scored. The default score value is 0, representing non-scorable responses such as "Undeliverable" and "Did Not Respond".
  
  Relevance:    Relevance Score values are on a scale of 1-3 where 1 is least relevant and 3 is most relevant.

                To score a 3, the response must include a mention of 4 values: 
                how AND when "the data subject will be notified of a data breach".
                
                To score a 2, the response must mention at least 2 of 4 values: 
                how OR when "the data subject will be notified of a data breach"
                PLUS 
                the stemmed term or synonym for "breach", OR "notification".

                To score a 1, the stemmed term or synonym for "breach", AND/OR "notification" must be included,
                AND
                omits how OR when "the data subject will be notified of a data breach"
                OR
                only how OR when "the data subject will be notified of a data breach" is included.
                  
                The score of 0 is assigned to responses lacking any of the above values.
                
  Usefulness:   Usefulness Score values are on a scale of 1-3 where 1 is least useful and 3 is most useful.
                This metric represents how well the information provided by the respondent can be used to find out if a data breach occurred.

                To score a 3 for usefulness, the relevance score must be a 2 or 3, at minimum.
                AND
                the response specifies both "How" and "When", such as: "You will be notified as soon as possible by email"
                OR provides specific instructions for the data subject, such as: "You can subscribe to notifications by..."

                To score a 2 for usefulness, the relevance score must be coded as a 1 or 2,
                AND
                the response references an action taken by the respondent, such as:
                "We notify people if this event occurs",
                OR "We post a notice on our site"
                OR "we have a process for responding to such incidents".

                To score a 1 for usefulness, the relevance score must not be 0,
                AND
                the response is so general that it cannot be tested, such as:
                "We take your privacy and security seriously" or "we follow all applicable laws".
                
                The score of 0 is assigned to responses lacking any of the above values.

  Effort:       Effort Score values are on a scale of 1-3 where 1 is most effort and 3 is least effort.
                This metric is designed to measure:
                a) how many additional questions the Requestor must submit to get a final response, or 
                b) how many additional steps the Requestor must take to get a satisfactory response, or 
                c) the level of effort made by the Respondant to locate PI or consult with others.

                To score a 3 for effort, the following conditions apply:
                [Followup Request Date] is NULL
                AND
                [Initial Response Type], [Second Response Type], [Third Response Type] must not be
                "Question", "Ticket, or "FAQs"
                AND
                [Final Coded Response] must not contain:
                references to policies, legislation, or other resources, such as webforms and login pages
                OR
                any indication that Respondant performed lookup queries, consulted with other team members, or attempted to authenticate                 the Researcher.
                
                
                To score a 2 for effort, the following conditions apply:
                [Second Response Type] OR [Third Response Type] must not be "Question" OR "Ticket"
                AND
                [Final Coded Response] must not contain:
                references to webforms and login pages
                OR
                any indication that Respondant consulted with other team members.


                To score a 1 for effort, the following conditions apply:
                [Followup Request Date] is NOT NULL
                AND / OR
                [Initial Response Type], AND [Second Response Type], OR [Third Response Type] is coded as
                "AckReceipt", Question", "Ticket, or "FAQs"
                AND / OR
                [Final Coded Response] contains:
                references to policies, legislation, or other resources, such as webforms and login pages
                AND / OR
                any indication that Respondant performed lookup queries, consulted with other team members, or attempted to authenticate                 the Researcher
                AND / OR 
                [Final Coded Response] IS NULL.
                
                
                The score of 0 for effort is not assigned.
                

R E D A C T E D    R E S P O N S E S - 	Final Coded Response: Redacted names, locations, URIs, and any other identifying information. This information, in addition to profiling the Sample Population by industry vertical and source, was not originally provided when this research experiment was published January, 2019.



TESTING METHODOLOGY
===================
QA1. Ensure that every email sent or received is accounted for, matching date/time.

QA2. Ensure that each respondent type is properly coded.

QA3. Ensure that each response is assigned to the correct respondent, and is properly coded for relevancy, usefulness, and effort. 

  
-------------------
Follow-up experiments:

A. Many organizations do not publish email addresses as contact points for receiving privacy requests.
Another variation of this experiment would be testing responses to requests submitted online through web forms.
Interesting metrics would include the amount of effort required for the requestor, and how efficient it is for the organization to acheive a final resolution of the request.

B. Some respondants have suffered from data breaches since the time this experiment was conducted. It would be interesting to conduct a different experiment to measure how well organizations comply with mandated data breach notifications. Including this metric as part of this experiment could possibly lead to identification of respondants. As of 11/21/2019, no data breach notifications have been received.
