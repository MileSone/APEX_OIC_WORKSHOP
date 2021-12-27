# Business Scenario

With the power of Oracle Integration Cloud process and workflow, we create Oracle Integration Cloud proccess application as backend engine. And for people already take adventages in Oracle APEX User Interface and oracle Database, you can easily build integrations with OIC and still use SSO as authorization scheme.

Here is a example of how to take advantage of this solution:

![Snipaste_2021-12-16_15-29-55](images/Snipaste_2021-12-16_15-29-55.png)

busniess workflow : 

APEX user submit form to active the proccess from APEX -> Sales Department first Comfirmation ->  Sales Department Second Approval  -> check for customer type if it is VIP customer -> Credit Department Third Comfirmation -> Credit Department Fourth Approval -> (Do anything you want) - > END proccess

Workflow is not fixed, your busniess changes and upgrade everyday. The old way people need change their program, doing development to fulfill the busniess need. Which will take days/months and the test and debug is nightmare. This solution avoid all of it. People can change existing workflow or link to new workflow as you need.  we can edit and manage workflow direcly in OIC application without change anything in APEX side.

And with this IDCS integration, inovate more. since OIC is integration cloud, your APEX now can easily connect to Saas applications,third-party SaaS and on-premises apps.

# Tutoiral Steps

1. [Create OIC instance](#memu_step1)

2. [Create APEX instance](#memu_step2)

3. [Add group and user](#memu_step3)

4. [Assign OIC Role](#memu_step4)

5. [OIC import workshop project](#memu_step5)

6. [APEX import workshop Project](#memu_step6)

7. [Config IDCS application](#memu_step7)

8. [Config APEX application](#memu_step8)

9. [Test and Run Application](#memu_step9)

10. [End User experience](#memu_step10)

    



<a name="memu_step1"></a>

# Create OIC instance

##### Step 1: Login to OCI console with your username / password and the homepage looks as below: 

[cloud.oracle.com](cloud.oracle.com) 

![Snipaste_2021-12-20_11-30-28](images/Snipaste_2021-12-20_11-30-28.png)

##### Step 2: Click on the Hamburger icon on top left, navigate to developer services and then select integration as shown in the below  

![Snipaste_2021-12-20_11-28-25](images/Snipaste_2021-12-20_11-28-25.png)

##### Step 3: Select the respective compartment and click on create button to create Integration instance as shown below.  

 ![Snipaste_2021-12-20_11-28-49](images/Snipaste_2021-12-20_11-28-49.png)

##### Step 4: Provide the respective details and click on create button to create the integration as shown below.  

![Snipaste_2021-12-20_11-29-34](images/Snipaste_2021-12-20_11-29-34.png)

##### Step 5:  click on "Service Console" to save your **OIC instance URL**

  ![Screenshot 2021-12-16 at 1.26.28 PM](images/Screenshot_2021-12-16_at_1.26.28.png)



<a name="memu_step2"></a>

# Create APEX instance

##### Step 1: Click on the Hamburger icon on top left, navigate to Oracle Database and then select Autonomous Database as shown in the below   

![Snipaste_2021-12-20_11-34-00](images/Snipaste_2021-12-20_11-34-00.png)

##### Step 2: Select the respective compartment and click on create button to create autonomous database as shown below.  

![Snipaste_2021-12-20_11-34-19](images/Snipaste_2021-12-20_11-34-19.png)

##### Step 3: Enter encessary information enter admin passoword then select “Create Autonomous Database” button.

![Snipaste_2021-12-20_11-35-26](images/Snipaste_2021-12-20_11-35-26.png)

![Snipaste_2021-12-20_11-35-42](images/Snipaste_2021-12-20_11-35-42.png)

##### Step 4: Once its built, click on Launch APEX button

![Snipaste_2021-12-16_13-47-35](images/Snipaste_2021-12-16_13-47-35.png)



![Snipaste_2021-12-16_13-47-51](images/Snipaste_2021-12-16_13-47-51.png)

##### Step 5: Enter user name password for admin login page to enter admin workspace console. Create a workspace to build application in workspace.

![Snipaste_2021-12-16_13-49-01](images/Snipaste_2021-12-16_13-49-01.png)

##### Step 6: Create workspace

![Snipaste_2021-12-16_13-49-37](images/Snipaste_2021-12-16_13-49-37.png)

##### Step 7: Login to this workspace (use the switch button below the Sign in button to swith between admin services and workspace login.)

![Snipaste_2021-12-16_13-50-21](images/Snipaste_2021-12-16_13-50-21.png)



<a name="memu_step3"></a>

# Add group and user

Since APEX integration application as UI, people need login as IDCS user. And user need some role settings in OIC as well.

##### Step 1:  in Cloud console click on Identity & Security and delete Federation.

![Snipaste_2021-12-16_13-41-31](images/Snipaste_2021-12-16_13-41-31.png)

<a name="IDCS_CONSOLE"></a>

##### Step 2:  click on the link in the middle to enter IDCS page 

![Snipaste_2021-12-16_13-41-54](images/Snipaste_2021-12-16_13-41-54.png)

##### Step 3:  navigate to Users 

![Snipaste_2021-12-16_13-44-29](images/Snipaste_2021-12-16_13-44-29.png)

##### Step 4:  input First Name Last Name and Email - click finish button (An active email will be send to this user)

![Snipaste_2021-12-16_13-44-39](images/Snipaste_2021-12-16_13-44-39.png)

##### Step 5:  navigate to Group add a group like below

![Snipaste_2021-12-16_13-43-59](images/Snipaste_2021-12-16_13-43-59.png)

##### Step 6:  inside this Group click on Assign button to add user in this group

![Snipaste_2021-12-16_13-44-11](images/Snipaste_2021-12-16_13-44-11.png)

<a name="memu_step4"></a>

# Assign OIC role 

##### Step 1:  Still in IDCS console click left top menu select Oracle Cloud Services

![Snipaste_2021-12-16_13-42-13](images/Snipaste_2021-12-16_13-42-13.png)

##### Step 2:  search for the OIC name your just create in this case I searched "oic" , navigate to Application role in the top tab button area, In "serviceAdministrator" at the very end click that menu button. 

![Snipaste_2021-12-16_13-42-56](images/Snipaste_2021-12-16_13-42-56.png)



##### Step 3:  select Assign Group search for the Group name you just created. and select it. hit "OK"

![Snipaste_2021-12-16_13-43-23](images/Snipaste_2021-12-16_13-43-23.png)



Therefor we have bind this group to have OIC service admin role for my OIC instance. Every user in this group will have the access. you can assign different role like "Service Developer" to different group as well.



<a name="memu_step5"></a>

# OIC import workshop project

For this workshop we will be use a demo project for importing and we can use it straight ahead. For detail how to create the OIC process application please navigate to [OIC part](https://github.com/MileSone/APEX_OIC_WORKSHOP/tree/main/OIC)

##### Step 1: in the projects folder, download two projects

![Screenshot 2021-12-20 at 12.17.35 PM](images/Screenshot_2021-12-20_at_12.17.35.png)

##### Step 2:  open OIC instance URL , in console click processes in the left top menu

![Screenshot 2021-12-16 at 1.26.59 PM](images/Screenshot_2021-12-16_at_1.26.59.png)

##### Step 3:  on the top right click “Create” button

![Screenshot 2021-12-16 at 1.30.29 PM](images/Screenshot_2021-12-16_at_1.30.29.png)

##### Step 4: select import project  

![Snipaste_2021-12-16_13-30-43](images/Snipaste_2021-12-16_13-30-43.png)

##### Step 5:  choose the file "OIC_project.exp" enter a name for it and click import button.

![Snipaste_2021-12-16_13-31-09](images/Snipaste_2021-12-16_13-31-09.png)

##### Step 6:  then the Application is created, now we publish and start using it.

![Snipaste_2021-12-16_13-31-29](images/Snipaste_2021-12-16_13-31-29.png)

##### Step 7:  click into it. on the top right click" Publish" button 

![Snipaste_2021-12-16_13-34-41](images/Snipaste_2021-12-16_13-34-41.png)				

##### Step 8:  on the pop up window enter some comments then hit publish

![Snipaste_2021-12-16_13-34-58](images/Snipaste_2021-12-16_13-34-58.png)

##### Step 9:  on the top right click "Activate" button.

![Snipaste_2021-12-16_13-35-17](images/Snipaste_2021-12-16_13-35-17.png)

##### Step 10:  click "Activate new version"

![Snipaste_2021-12-16_13-35-31](images/Snipaste_2021-12-16_13-35-31.png)

##### Step 11: follew the steps click on >validate

![Snipaste_2021-12-16_13-35-43](images/Snipaste_2021-12-16_13-35-43.png)

##### Step 12: enter a version "1.0" click on >validate

![Snipaste_2021-12-16_13-36-00](images/Snipaste_2021-12-16_13-36-00.png)

##### Step 13: click finish

![Snipaste_2021-12-16_13-36-34](images/Snipaste_2021-12-16_13-36-34.png)

##### Step 14: on the top left navigate back to home

![Snipaste_2021-12-16_13-36-48](images/Snipaste_2021-12-16_13-36-48.png)

##### Step 15:  click on "Process" - "Process Application" in the menu, click "Activate" button on the top right (this is where all activate application is listed)

![Snipaste_2021-12-16_13-37-08](images/Snipaste_2021-12-16_13-37-08.png)



##### Step 16: select the right menu icon for the app you activated.

![Snipaste_2021-12-16_13-37-25](images/Snipaste_2021-12-16_13-37-25.png)

##### Step 17: click on web services

![Snipaste_2021-12-16_13-37-36](images/Snipaste_2021-12-16_13-37-36.png)

##### Step 18: open this URL

![Snipaste_2021-12-16_13-37-59](images/Snipaste_2021-12-16_13-37-59.png)

##### Step 19: sreach for the "1.0" and you will find a OICAPPID!VERSION*soaXXXXXXXXXX string save it:

OIC application Define ID:`CustomerCreationApp!1.0*soa_2a2f1c2d-7186-4733-91ed-91c76868112c`

![Snipaste_2021-12-16_13-38-27](images/Snipaste_2021-12-16_13-38-27.png)



###### now the OIC application has successfully deployed and activated , now we will need add some user to application roles, inorder to let them do approval/ reject action, create request or review the process.

##### Step 20:  In the OIC select "My Tasks"

![Snipaste_2021-12-16_13-39-34](images/Snipaste_2021-12-16_13-39-34.png)

##### Step 21:  select Administration

![Snipaste_2021-12-16_13-40-02](images/Snipaste_2021-12-16_13-40-02.png)



##### Step 22:  In the process Roles, select the role name that you want to add people with. at right hand click on "Add member" and search by email name to add member. In this case you can add your email to "New Creation Request"  "Credit Department" "Sales Department".

![Snipaste_2021-12-16_13-40-17](images/Snipaste_2021-12-16_13-40-17.png)

![Snipaste_2021-12-16_13-40-35](images/Snipaste_2021-12-16_13-40-35.png)



<a name="memu_step6"></a>

# APEX import Project

In this workshop we will import a demo APEX project. In APEX we will import application and database tables.

##### Step 1:  Login APEX click on App Builder

![Snipaste_2021-12-16_13-52-09](images/Snipaste_2021-12-16_13-52-09.png)

##### Step 2:  Click on Import button

![Snipaste_2021-12-16_13-52-21](images/Snipaste_2021-12-16_13-52-21.png)

##### Step 3:  drag the apex_project.sql into it. click Next

![Snipaste_2021-12-16_13-52-40](images/Snipaste_2021-12-16_13-52-40.png)

##### Step 4:  click next

![Snipaste_2021-12-16_13-52-55](images/Snipaste_2021-12-16_13-52-55.png)

##### Step 5:  click Next

![Snipaste_2021-12-16_13-53-34](images/Snipaste_2021-12-16_13-53-34.png)

##### Step 6:  Click on Edit Application

![Snipaste_2021-12-16_13-53-48](images/Snipaste_2021-12-16_13-53-48.png)

##### Step 7:  Save your URL and App ID

APEX baseURL:https://g30345bc1601f57-XXXX.adb.ap-tokyo-1.oraclecloudapps.com

APEX Application ID on top left: 104

##### then Click on SQL workshop, choose  SQL commands

![Snipaste_2021-12-16_13-54-04](images/Snipaste_2021-12-16_13-54-04.png)

##### Step 8:  Create Datatables for this project:

###### run each row to create table first

```
CREATE TABLE  "CRK_DICT" 
   (    "ID" NUMBER GENERATED BY DEFAULT AS IDENTITY MINVALUE 1 MAXVALUE 9999999999999999999999999999 INCREMENT BY 1 START WITH 1 CACHE 20 NOORDER  NOCYCLE  NOKEEP  NOSCALE  NOT NULL ENABLE, 
    "TNAME" VARCHAR2(4000) COLLATE "USING_NLS_COMP", 
    "TTYPE" VARCHAR2(200) COLLATE "USING_NLS_COMP"
   )  DEFAULT COLLATION "USING_NLS_COMP"
/
CREATE TABLE  "LOG_INFO" 
   (    "LOGGING" VARCHAR2(4000) COLLATE "USING_NLS_COMP", 
    "UPDATEDAT" TIMESTAMP (6) DEFAULT CURRENT_TIMESTAMP, 
    "ID" NUMBER GENERATED BY DEFAULT AS IDENTITY MINVALUE 1 MAXVALUE 9999999999999999999999999999 INCREMENT BY 1 START WITH 1 CACHE 20 NOORDER  NOCYCLE  NOKEEP  NOSCALE  NOT NULL ENABLE
   )  DEFAULT COLLATION "USING_NLS_COMP"
/
```

###### replace the value of OIC define ID and BaseURL for OIC instance URL

```
INSERT INTO CRK_DICT(TTYPE ,TNAME) VALUES('OICAppId','CustomerCreationApp!1.0*soa_2a2f1c2d-7186-4733-91ed-91c768681XXX')
INSERT INTO CRK_DICT(TTYPE ,TNAME) VALUES('BaseURL','https://oic-mile-workshop-XXXXXX-nt.integration.ocp.oraclecloud.com')
```

###### Select the SQL then hit run 

![Snipaste_2021-12-20_13-41-14](images/Snipaste_2021-12-20_13-41-14.png)

Note: With these set up, we have added the application and database tables, however this application is using SSO, unless we change it to others or create IDCS application for this APEX app we won't able to run the app.

save your APEX base URL for example: 



<a name="memu_step7"></a>

# Config IDCS application

Lets now create IDCS application, this IDCS is controlling the users who can login and logout from APEX UI. And this application is conrolling who can invoke OIC API in the scope.

##### Step 1:  Create IDCS app

navigate to [IDCS Console](#IDCS_CONSOLE)

Select Application on the menu

Click on Add button to add a application 

![Snipaste_2021-12-16_13-55-11](images/Snipaste_2021-12-16_13-55-11.png)

##### Step 2:  Create IDCS app details

choose Confidential Application

![Snipaste_2021-12-16_13-55-24](images/Snipaste_2021-12-16_13-55-24.png)

Enter a name;

![Snipaste_2021-12-16_13-56-55](images/Snipaste_2021-12-16_13-56-55.png)

For Configuration tab enter same value as below image

save your current Page Base URL (**IDCS URL**) like:  https://g30345bc1601f57-db202106151059.adb.ap-tokyo-1.oraclecloudapps.com

Redirect URL : <APEXURL>/ords/apex_authentication.callback

POST logout Redirect URL : <APEXURL>/ords/f?p=<your APEX App ID>

![Snipaste_2021-12-16_13-59-15](images/Snipaste_2021-12-16_13-59-15.png)

click Add scope search for the OIC name your created, and system will give you a scope like:

![Snipaste_2021-12-16_14-00-00](images/Snipaste_2021-12-16_14-00-00.png)

![Snipaste_2021-12-16_13-59-47](images/Snipaste_2021-12-16_13-59-47.png)

add some Roles select them as below.

![Snipaste_2021-12-16_14-00-56](images/Snipaste_2021-12-16_14-00-56.png)



Edit resources like below put Primary Audience as OIC Base URL like:

https://oic-mile-workshop-sehubjapacprod-nt.integration.ocp.oraclecloud.com

![Snipaste_2021-12-16_14-01-33](images/Snipaste_2021-12-16_14-01-33.png)

##### Step 3:  Activate the IDCS App

![Snipaste_2021-12-16_14-01-47](images/Snipaste_2021-12-16_14-01-47.png)

make sure save Client ID and Secret for later use

![Snipaste_2021-12-20_15-10-21](images/Snipaste_2021-12-20_15-10-21.png)



<a name="memu_step8"></a>

# Config APEX application

We have successful activate our IDCS application. Now we will link APEX application to this IDCS app.

##### Step 1:  Configure Web credentials

- In APEX application 104 -> share components -> Web Credentials 
- Edit a web credential called "IDCS_Application_Credentials"
- Put OAuth2 as Authentication Type
- OAuth Scope we put IDCS app scope system generated like https://BF1CB539D29C437F8B4F9EE42398255F.integration.ocp.oraclecloud.com:443urn:opc:resource:consumer::all
- put Client ID
- put Client Secret
- Apply Changes

![Snipaste_2021-12-16_14-37-29](images/Snipaste_2021-12-16_14-37-29.png)

##### Step 2:  Configure Authentication Schemes

- Choose OIC_IDCS_AUTH
- Scheme Type : Social Sign-In
- Discovery URL: <IDCS BASE URL>/.well-known/openid-configuration
- Scope: we put IDCS app scope system generated
- Change Post-Logout URL: <APEX BASEURL>/ords/f?p=<ApplicationID>
- Then hit Apply changes

![Snipaste_2021-12-16_14-39-32](images/Snipaste_2021-12-16_14-39-32.png)

![Snipaste_2021-12-20_16-10-38](images/Snipaste_2021-12-20_16-10-38.png)



and now we can run this application with IDCS username password, and you will see the Application



<a name="memu_step9"></a>

# Test Application

now lets login and test

![Snipaste_2021-12-20_16-09-07](images/Snipaste_2021-12-20_16-09-07.png)





![Snipaste_2021-12-20_16-12-50](images/Snipaste_2021-12-20_16-12-50.png)



Now you can create a customer creation request. (with OIC "New Creation Request"  role)



![Snipaste_2021-12-20_16-13-13](images/Snipaste_2021-12-20_16-13-13.png)

And logged in user can see their tasks.

![Snipaste_2021-12-20_16-13-00](images/Snipaste_2021-12-20_16-13-00.png)

Click into a single one user can enter commands, see where the task at, and approve or reject the task.

![Snipaste_2021-12-20_16-14-55](images/Snipaste_2021-12-20_16-14-55.png)



![Snipaste_2021-12-20_16-15-04](images/Snipaste_2021-12-20_16-15-04.png)

With OIC Email notification enable user will receive email notifications as well

![Snipaste_2021-12-20_17-42-39](images/Snipaste_2021-12-20_17-42-39.png)

In OIC Console click My Tasks in the menu - select Processes.

![Snipaste_2021-12-20_17-29-49](images/Snipaste_2021-12-20_17-29-49.png)



![Snipaste_2021-12-20_17-30-30](images/Snipaste_2021-12-20_17-30-30.png)

***You can see in graphical view to check where the task at.  Which department is blocking the workflow !***



<a name="memu_step10"></a>

# End User experience

In the video we will show how to use this OIC+APEX demo.

*Alex acts as request creator.*

*Oscar is an approver in the Sales Department.*

**People have different roles assigned in OIC, they will have different access in this APEX application!**

https://user-images.githubusercontent.com/6970416/146891233-17615c1e-5394-485d-be76-43539e8b9bd3.mp4

https://user-images.githubusercontent.com/6970416/146891271-b714fcad-ea47-4705-81ba-5cda372a2c62.mp4

https://user-images.githubusercontent.com/6970416/146891443-7698adb0-8d1e-497b-9a8c-fd1f80e7b301.mp4
