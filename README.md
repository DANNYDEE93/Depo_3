### **Troubleshooting URL Shortener for Site Reliability**
______________________________________________________________________________
###### Danielle Davis
###### September 23, 2023


______________________________________________________________________________
#### <ins> **The Story** </ins>
______________________________________________________________________________
We’re a tech start-up company with a URL shortener tool. We have a SLA(service level agreement or warranty) with Nike to provide them access to our URL shortener and it outlines that we are only allowed 20 minutes of downtime a year. The SLA guarentees Nike that we will provide reliable site uptime so the their web application is operational and available to users for the remaining time of the year. If anything happens to the URL shortener, we must communicate any incidents to Nike as this could negatively affect Nike's performance, reliablity, user experience and especially earnings because this could cost Nike millions of dollars.
___________________________________________________________________________________


______________________________________________________________________________
#### <ins>**Scenario**</ins>
______________________________________________________________________________
A new hire was tasked with updating the URL shortener in Amazon Elastic Beanstalk. The new hire committed version 2 of the application with git code to the main branch, which automatically triggered a build, test, and deploy to the production server, replacing version 1 of the application running on the server. This caused an error in the web application creating a period of downtime putting the company at risk of breaking the SLA devised with Nike. Remember you're only allotted 20 minutes of downtime. 
______________________________________________________________________________


_______________________________________________________________________________
####  <ins>**Purpose & Description**</ins> 
______________________________________________________________________________
To provide a solution for this scenairo, I used an EC2 instance installed with Jenkins, Python, and AWS Elastic Beanstalk CLI along with a webhook made through GitHub to automatically trigger a test and build in Jenkins. I used this same EC2 instance to deploy a web application in an ElasticBeanstalk environment created through the command line interface with an URL shortener in my previous deployment. You can review my previous Deployment 3 [here](https://github.com/DANNYDEE93/Deployment3).
Given the scenario, I've provided a post-incident report to have a record for what happened, how long the application was down for, the steps I took to resolve the incident, and the steps I will take in the future to avoid another incident like this from happening again. 
________________________________________________________________


______________________________________________________________________________
### <ins>**Post-Incident Report**</ins>
____________________________________________________________________________

Between the hour of 12:45pm and 12:55pm on Septermber 22, 2023, all users of the Nike web application encountered an internal server error. As we were working on a second version of the web application, this version was hastily deployed to production at 12:45pm. Version 2 of the web application a code error within the 'application.py' and 'test_app.py' that caused issues with our internal server that disrupted the connectivity to Nike's web application.  This critical-level incident affected 100% of internal and external users. The incident was detected by DataDog from monitor alerts and triggered a successful build in Jenkins and the senior development team was alerted right away. A bug error ticket was created and the incident was escalated to our engineering team.


____________________________________________________________________________
#### <ins>**Resolution**</ins>
___________________________________________________________________________

 <ins>**A. Rollback Deployment**</ins>
 
In order to make sure that the web application wasn't down for longer than 20 minutes, my first step was to rollback to the previous version of the application that was working using git code in remote repo in the visual studio code terminal to commit changes and push the switch back to version 1 in the local repo on GitHub. Rollback to version 1 in visual studio code using the following steps:

1. Run **git log --oneline** to see th hash number associated with the git commit for Version 1(V1)

 [here](https://github.com/DANNYDEE93/Deployment3) hash
 
2. Run **git checkout <V1hash#>** which is the same as "git switch" to switch back the V1.

[here](https://github.com/DANNYDEE93/Deployment3) checkout

____________________________________________________________________________________
3. Run **git switch -c second** to save changes to a new branch 
4. Run **git checkout -b second origin main** to 
5. Run **git branch --set-upstream-to=origin main** to connect the branches from the remote repo to the local repo.
7. Run **git add** to add changes to the staging environment
8. Run **git commit -m "Rolled back to Version 1"** commits changes to the local repo
_____________________________________________________________________________________

9. Run **git status** to see which branch you are currently in an whether it is up to date. Make sure there aren't any other conflicts that need resolving. 
10. Run **git pull** the changes in the remote repo and sign into Github to connect repositories
11. Run **git push**  to push changes made in the main branch on the remote repo that has already been connected to the local repo. 

[here](https://github.com/DANNYDEE93/Deployment3) pulloush

[here](https://github.com/DANNYDEE93/Deployment3) version1

 <ins>**B. Troubleshooting**</ins>
 
Now that the deployment was rolled back to the previous version 1 of the application, we have resolved the issue of downtime for internal and external users. We can afford to troubleshoot and find the issue within version 2 of the application. 

1. Checked error logs in ElasticBeanstalk that pointed to a JSON error in the application.py file in the local repo.

[here](https://github.com/DANNYDEE93/Deployment3) error log


3. Checked error in commits shown in the local repo

   [here](https://github.com/DANNYDEE93/Deployment3) v2
5. Corrected errors in version 2 of the application for the future and allows the development team to continue making necessary updates to improve user experience.

6. [here](https://github.com/DANNYDEE93/Deployment3) jenkins 

   
____________________________________________________________________________
#### <ins>**Next Steps**</ins>
______________________________________________________________________________

Here are some ways we can improve the deployment process and prevent similar incidents from happening in the future:

1. Add necessary permission to groups so that certain groups do not have the ability to commit to the main branch before approval from higher level personnel.
2. If finanaces will allow, additonal environements could be created so that we can automatically switch to a new working one with blue/green deployment
3. Use monitoring tools such as DataDog to immediately alert the necessary personnel of any issues in the deployment of the web applicaiton.


____________________________________________________________________________________
#### <ins>**Conclusion**</ins>
____________________________________________________________________________________

With the 10 minutes of downtime that was used to roll back to the previous version of the web application, the company has used 50% of the allowable downtime as outlined in our SLA with Nike. For the rest of the year, we now only have 10 minutes to resolve any other service issues with our provided URL shortener. This is why it is very important to follow through with the 'Next Steps' that are described above. If we use the proper tools to continuously monitor and integrate within the deployment process, we can avoid future complications and the risk of breaking our SLA.

