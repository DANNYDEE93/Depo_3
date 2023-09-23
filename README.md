### **Troubleshooting URL Shortener for Site Reliability**
#### ______________________________________________________________________________
###### Danielle Davis
###### September 23, 2023

#### ______________________________________________________________________________
##### **The Story**
#### ______________________________________________________________________________
We’re a tech start-up company with a URL shortener tool. We have a SLA(service level agreement or warranty) with Nike to provide them access to our URL shortener and it outlines that we are only allowed 20 minutes of downtime a year. The SLA guarentees Nike that we will provide reliable site uptime so the their web application is operational and available to users for the remaining time of the year. If anything happens to the URL shortener, we must communicate any incidents to Nike as this could negatively affect Nike's performance, reliablity, user experience and especially earnings because this could cost Nike millions of dollars.

#### ______________________________________________________________________________
##### **Scenario**
#### ______________________________________________________________________________
A new hire was tasked with updating the URL shortener in Amazon Elastic Beanstalk. The new hire committed version 2 of the application with git code to the main branch, which automatically triggered a build, test, and deploy to the production server, replacing version 1 of the application running on the server. This caused an error in the web application creating a period of downtime putting the company at risk of breaking the SLA devised with Nike. Remember you're only allotted 20 minutes of downtime. 

#### ______________________________________________________________________________
###### **Purpose & Description**
#### ______________________________________________________________________________
To provide a solution for this scenairo, I used an EC2 instance installed with Jenkins, Python, and AWS Elastic Beanstalk CLI along with a webhook made through GitHub to automatically trigger a test and build in Jenkins. I used this same EC2 instance to deploy a web application in an ElasticBeanstalk environment created through the command line interface with an URL shortener in my previous deployment. You can review my previous Deployment 3 [here](https://github.com/DANNYDEE93/Deployment3).
Given the scenario, I've provided a post-incident report to have a record for what happened, how long the application was down for, the steps I took to resolve the incident, and the steps I will take in the future to avoid another incident like this from happening again. 

#### ______________________________________________________________________________
##### **Post-incident report**
#### ______________________________________________________________________________
<ins>**Reason for the incident**</ins>

<ins>**Downtime**</ins>

- How long was the site down or malfunctioning?

 <ins>**Resolution**</ins>
- What steps were taken to resolve the incident?

 
         <ins> **Was the incident fully resolved?** </ins>

#### ____________________________________________________________________________
##### **Next Steps**
#### ______________________________________________________________________________


- What steps would you take to prevent this from happening again?

  
