## Exercise 3: Protect Data 


### Task 1: Transparent Data Encryption 

Transparent data encryption (TDE) helps protect Azure SQL Database against the threat of malicious offline activity by encrypting data at rest. It performs real-time encryption and decryption of the database, associated backups, and transaction log files at rest without requiring changes to the application

1. In the Azure Portal, go to Resource Group with suffix **-SQL**, select the SQL Database **Clinic**.
1. Select **Transparent data encryption** under the Security blade.
1. Here you can review; transparent data encryption is already enabled. 

![](images/transdataenc.png)

### Task 2: Auditing 

1. In SQL Database, under Settings select **Auditing** where you can review that Auditing is enabled and data is being stored in your storage account.
1. Click on **View Audit Logs**, this will show all the database activities happened recently.
![](images/auditing.png)


### Task 3: Threat Protection 
1. Open Resource Group with suffix **-SQL**, navigate to the SQL Server. Select **Advanced Data Security** under Security.
1. Use the following configurations:
Advanced Data Security: **On**
Subscription: **Choose your subscription**
Storage Account: **Choose your storage account**
Periodic recurring scans: **On**
Send scan reports to: **username**
Send Alerts to: **username**
1. Select **Save**.

![](images/advancedsecurity.png)


### Task 4: Configure SQL Data Discovery and Classification

In this task, you will look at the SQL Data Discovery and Classification feature that introduces a new tool for discovering, classifying, labeling & reporting the sensitive data in your databases. It introduces a set of advanced services, forming a new SQL Information Protection paradigm aimed at protecting the data in your database.

1. Go to SQL Database, On the **Advanced Data Security** blade, select the **Data Discovery & Classification** tile.

![](images/dataclassification.png)


1. In the Data Discovery & Classification blade, select the info link with the message **We have found 16 columns with classification recommendations**.
1. Look over the list of recommendations to get a better understanding of the types of data and classifications that can be assigned, based on the built-in classification settings.
1. Check the Select all check box at the top of the list to select all the remaining recommended classifications, and then select **Accept selected recommendations**.
1. When the save completes, select the **Overview** tab on the Data Discovery & Classification blade to view a report with a full summary of the database classification state.

**image to be taken**

**Verify by running SQL Query**


### Task 6: Simulate Attack 

1.	In the Azure Portal, open Resource Group with suffix **-SQL**, navigate to the app service **contosoapp-suffix**.
1.	Select browse, you will be directed to **Contoso Clinic** webpage.	
1.	Go to **Patients**, select **SQLi Hints**.
1.	You will see SQL ingestions that will result into an attack.
1.	Pick one of them and paste in the search box and select Search.
1.	Go to SQL Database **Clinic**, select **Advanced Data Security** under Security blade.
1.	Select **Advanced Threat Protection**, where you can review the alert , also this will be shown as a threat. It will take few minutes to get fetched.


### Task 7: Vulnerability Scan

The SQL Vulnerability Assessment service is a service that provides visibility into your security state, and includes actionable steps to resolve security issues, and enhance your database security.

1.	Return to the **Advanced Data Security** blade and then select the **Vulnerability Assessment** tile.
1.	On the Vulnerability Assessment blade, select **Scan** on the toolbar.
1.	When the scan completes, you will see a dashboard, displaying the number of failing checks, passing checks, and a breakdown of the risk summary by severity level.
1.	__________

1.	Run a SQL Injection Alert 
1.	You'll receive an email with security alert (lab user has mailbox) 
1.	Review the security alerts in ATP 
1.	Review Audit Logs
1.	Run a Vulnerability Scan and review results. 


### Task 8: Application Access: 
1.	Add a Mask for Credit Card, Email and other personal information in Customer table. 
In this exercise, you will enable Dynamic Data Masking (DDM). DDM limits sensitive data exposure by masking it to non-privileged users. This feature helps prevent unauthorized access to sensitive data by enabling customers to designate how much of the sensitive data to reveal with minimal impact on the application layer. It’s a policy-based security feature that hides the sensitive data in the result set of a query over designated database fields, while the data in the database is not changed.

i.	Go to SQL Database, On the Advanced Data Security blade, select the Dynamic Data Masking. 
ii.	Select +Add Mask.
iii.	Use following configurations and select Add:
Schema: dbo
Table: select Patients from dropdown
Column: SSN (char) from dropdown
iv.	Add a mask again by selecting +Add Mask.
v.	Use following configurations and select Add:
Schema: dbo
Table: select Visits from dropdown
Column: PatientID (int) from dropdown
Masking field format: Number (random number range) [From: 0 – To: 100]
