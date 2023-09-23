### Troubleshooting URL Shortener for Site Reliability
###### 
###### 
###### --------------------------------------------------------------------------------------------------
The Story
------------------------------------------------------------------------------------------------------------
We’re a tech start-up company with a URL shortener tool. We have a SLA(service level agreement or warranty) with Nike to provide them access to our URL shortener and it outlines that we are only allowed 20 minutes of downtime a year. The SLA guarentees Nike that we will provide reliable site uptime so the their web application is operational and available to users for the remaining time of the year. If anything happens to the URL shortener, we must communicate any incidents to Nike as this could negatively affect Nike's performance, reliablity, user experience and especially earnings because this could cost Nike millions of dollars.

 ####### ------------------------------------------------------------------------------------------------------
Scenario
--------------------------------------------------------------------------------------------------------------
A new hire was tasked with updating the URL shortener in Amazon Elastic Beanstalk. The new hire committed version 2 of the application with git code to the main branch, which automatically triggered a build, test, and deploy to the production server, replacing version 1 of the application running on the server. This caused an error in the web application creating a period of downtime putting the company at risk of breaking the SLA devised with Nike. Remember you're only allotted 20 minutes of downtime. 

###### ---------------------------------------------------------------------------------------------------
###### Purpose & Description
###### ---------------------------------------------------------------------------------------------------

To provide a solution for this scenairo, I used the same EC2 instance installed with Jenkins, Python, and AWS Elastic Beanstalk CLI that was previously used in my previous deployment. You can review that [here]()
Given the scenario, 

Next Steps 
-----------------------------------------
Create a post-incident report. The report must include:
- What was the reason for the incident?
- How long was the site down or malfunctioning?
- What steps were taken to resolve the incident?
- Was the incident fully resolved?
- What steps would you take to prevent this from happening again?

  
