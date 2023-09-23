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



___________________________________________________________
Message sent to Nike to inform them of the incident. The web application  is currently experiencing issues. We know this is frustrating and we’re working to resolve this as soon as possible. We have escalated this to our engineering team, and will provide an update as soon as more information becomes available.
________________________________________________________________

#### ______________________________________________________________________________
##### **Post-incident report**
#### ____________________________________________________________________________

Between the hour of 12:45pm and 1:05pm on Septermber 22, 2023, all users of the Nike web application encountered an internal server error. As we were working on a second version of the web application, this version was hastily deployed to production at 12:45pm. Version 2 of the web application a code error within the 'application.py' and 'test_app.py' that caused issues with our internal server that disrupted the connectivity to Nike's web application.  This critical-level incident affected 100% of users.  The incident was found and notified by the

 <ins>**Resolution**</ins>
 
</ins> **What steps were taken to resolve the incident?** </ins>

In order to make sure that the web application wasn't down for longer than 20 minutes, my first step was to rollback to the previous version of the application that was working using git code in remote repo in the visual studio code terminal to commit changes and push the switch back to version 1 in the local repo on GitHub. Rollback to version 1 in visual studio code using the following steps:

1. Run **git log --oneline** to see th hash number associated with the git commit for Version 1(V1)
2. Run **git checkout <V1hash#>** which is the same as "git switch" to switch back the V1.
      2a. After git checkout, V1 was placed in a branch in a detached state so it was not going to be able to add and commit the revert to V1.
     2b. git pull -u 

<ins> **Was the incident fully resolved?** </ins>

#### ____________________________________________________________________________
##### **Next Steps**
#### ______________________________________________________________________________


- What steps would you take to prevent this from happening again?

  
