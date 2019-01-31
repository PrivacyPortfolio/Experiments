Experiment #1:

Objective:
Determine what percentage of organizations respond to Privacy Requests and Concerns,
and explore how can this information be used to improve privacy practices.


Goals:

Questions: 
1. Are organizations more likely to respond to privacy questions or privacy concerns?
2. How long does it take for organizations to respond to privacy requests?
3. Who responds to these requests?
4. How relevant are the responses to the requests?
5. How useful is the response to a request?
6. What is the cost in time and other resources for issuing requests, and issuing responses?



Metrics:


-------------------

Sample:
  100 organizations in 2 categories: 
    Tier 1 is comprised of privacy organizations, tool vendors, and certified companies who represent the subject matter experts and leaders in privacy, compliance, and infoSec.
    Tier 2 is comprised of everyone else who isn't in Tier 1, but a majority of these are listed as vendors on the iapp.org website and a majority of these have at least a significant workforce here in the Bay Area.
    Organizations must have an email address in the privacy policy where requests are intended to be received.


Methodology:
Half of the organizations receive a Privacy Request:
  Privacy Request: 
  "How and when will I be notified if there is a data breach?"

The other half receive a Privacy Concern:
  Privacy Concern: 
  "I'm concerned about how and when I'll be notified of a data breach"

This is designed to discover which kind of inquiries organizations are more likely to respond to. Both questions are very specific requests.

Premise: Current laws require that data subjects to be notified within a specified time period if their personal information was breached. It's reasonable to assume this requirement can't be met if a data subject hasn't provided appropriate contact information.


-------------------

Tools:
1. curl scripts for getting privacy policies from list of urls
2. local script for finding company name and mailto contact
-> example using text search for "contact":


Coding Responses:
We record the Initial Response Date/Time, Initial Response Type, Initial Responder, and Initial Response.
"Initial Response Type" is enumerated as: 
  1 - Additional Questions
  2 - Automatic Reply
  3 - Request Received
  4 - Appropriate Response
  5 - FAQs
  6 - Delivery Notification

"Initial Responder" is enumerated as:
  1 - Real Person with Job Title
  2 - Real Person No Job Title
  3 - Team or Group Name (sub-classified as Legal, Privacy, Support, Other)

Privacy Requests are considered to be resolved when the communication exchange ends.
This is represented as the "Final Response", to which the Requestor replies: "Thanks for your response."
This reply is intended to represent that the request has been resolved and no further communication is required.

"Final Responses" are further classified as:
  Relevance Category
  Relevance Score
  Usefulness Score
  Effort Score
  
  Relevance Categories are: "Answer", "FAQs", "Who are you", "What do you want", and "Ticket"
  Relevance Score values are on a scale of 1-3 where 1 is least relevant and 3 is most relevant.
  To score a 3, the response must include a mention of "how the data subject will be notified of a data breach" AND "when the data subject will be notified of a data breach".
  To score a 2, the response must mention either "how" or "when" the data subject will be notified, or mention the term or synonym for "data breach", or "notification".
  To score a 1, none of the above values are included in the response.
  
  Usefulness Score values are on a scale of 1-3 where 1 is least useful and 3 is most useful.
  These scores represent a slightly different aspect of relevancy scores, in that not every relevant response is actually of use to the Requestor.
  For instance:
  
  A response coded as a 3 for relevance, is coded as a 3 for usefulness if:
    "You will be notified as soon as possible by email"
    
  A response coded as a 3 for relevance, is coded as a 2 for usefulness if:
    "We notify people if this event occurs", or "We post a notice on our site", or "we follow all applicable laws"
    
  A response coded as a 2 for relevance, is coded as a 3 for usefulness if:
    "You can subscribe to notifications by..."
    
  A response coded as a 2 for relevance, is coded as a 2 for usefulness if:
    The information can be used to find out if a data breach occurred.
    
  A response coded as a 2 for relevance, is coded as a 1 for usefulness if:
    There is no practical guidance on how to find out if a data breach occurred.

An Effort Score is designed to measure:
how many additional questions the Requestor must submit to get a final response
how many additional steps the Requestor must submit to get a final response
any effort made by the Respondant to locate PI before issuing a final response


  
-------------------
Follow-up experiments:

Many organizations do not publish email addresses as contact points for receiving privacy requests.
Another variation of this experiment would be testing responses to requests submitted online through web forms.
Interesting metrics would include the amount of effort required for the requestor, and how efficient it is for the organization to acheive a final resolution of the request.
