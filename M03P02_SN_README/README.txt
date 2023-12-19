---------------------------------------------- README - M03P02 ------------------------------

This document provides overall instructions for setting up and executing project M03P02. Please note that there are few areas which are not automated as they were not mentioned as a requirement and are called out explicitly.

----------------------------------------------------------------------------------------------
A. Areas not automated and are manual:
----------------------------------------------------------------------------------------------

1. CREATION OF KEYPAIR
	a) Create keypair via AWS Console UI "M03P02keypair.ppk" and also download/save to local system.

2. CREATION OF IAM ROLES
	There are three roles used in this entire project and all three roles have been added manually via AWS Console UI.
	a) EC2Role
	b) LambdaRole
	c) CodeDeployRole

3. UPLOAD OF FILES TO S3 BUCKET 
	a) appspec.yml
	b) shell scripts (pre/post/start/stop)
	c) raw_data.py
	d) requirements.txt

4. UPDATE ROLES (FROM #1) IN CLOUDFORMATION TEMPLATE 
	a) "EC2Role" in Cloudformation Template
	b) "LambdaRole" ARN in Cloudformation Template

5. UPDATE LAMBDA FUNCTION
	a) Update SNS Topic ARN in Lambda Function code (via AWS Console UI after Cloudformation stack is successful)

6. CREATION OF CODEDEPLOY
	a) Install CodeDeploy Agent on EC2Instance
	b) Create CodeDeploy Application 
	c) Create Deployment Group
	d) Deploy Application

7. RUN PYTHON APPLICATION
	a) python3 raw_data.py



----------------------------------------------------------------------------------------------
B. TASK 1
----------------------------------------------------------------------------------------------
PREREQUISITES:
A.1
A.2.a
A.4.a


STEPS:
1. Create Stack using ...\CloudProject2_M03P02_SN\M03P02_SN_CFTemplates\CF_Template_Task1.json
2. Confirm Subscription received in email
3. Create Lambda Function using ...\\CloudProject2_M03P02_SN\anomaly_detection.py and update the SNS Topic ARN from the Outputs tab of CloudFormation stack (same as Step 2 of TASK 1 above). Also, add Trigger as Kinesis stream that was newly created via Cloudformation.
4. SSH into newly created EC2 Instance and upload the raw_data.py file
5. Execute raw_data.py


VERIFICATION:
1. Check data in newly created Dynamo DB table
2. Check email for notifications


----------------------------------------------------------------------------------------------
C. TASK 2
----------------------------------------------------------------------------------------------

PREREQUISITES:
A.1
A.2
A.4.a


STEPS:
1. Create Stack using ...\CloudProject2_M03P02_SN\M03P02_SN_CFTemplates\CF_Template_Task2.json
2. Confirm Subscription received in email
3. Create folder in newly created S3 bucket and Upload files (folders) from ...\CloudProject2_M03P02_SN\M03P02_SN_CodeDeployFiles\m03p02sn_AutoExecuteOnCodeDeploy 
4. SSH into newly created EC2 Instance and install CodeDeploy agent using Steps mentioned in ...\CloudProject2_M03P02_SN\M03P02_SN_README\README_InstallAgentonEC2InstanceViaPutty.txt
5. Create Lambda Function using ...\\CloudProject2_M03P02_SN\anomaly_detection.py and update the SNS Topic ARN from the Outputs tab of CloudFormation stack (same as Step 2 of TASK 1 above). Also, add Trigger as Kinesis stream that was newly created via Cloudformation.
6. Go to CodeDeploy and create Application
7. Create Deployment Group
8. Deploy Application (run raw_data.py manually or via the shell script that runs automatically on deploy)


VERIFICATION:
1. Check data in newly created Dynamo DB table
2. Check email for notifications


----------------------------------------------------------------------------------------------
D. TASK 3
----------------------------------------------------------------------------------------------

PREREQUISITES:
A.1
A.2
A.4


STEPS:
1. Create Stack using ...\CloudProject2_M03P02_SN\M03P02_SN_CFTemplates\CF_Template_Task3.json
2. Confirm Subscription received in email
3. Create folder in newly created S3 bucket and Upload files (folders) from ...\CloudProject2_M03P02_SN\M03P02_SN_CodeDeployFiles\m03p02sn_AutoExecuteOnCodeDeploy 
4. SSH into newly created EC2 Instance and install CodeDeploy agent using Steps mentioned in ...\CloudProject2_M03P02_SN\M03P02_SN_README\README_InstallAgentonEC2InstanceViaPutty.txt
5. Update SNS Topic ARN in Lambda Function code (via AWS Console UI after Cloudformation stack is successful) - see A.5 
6. Go to CodeDeploy and create Application
7. Create Deployment Group
8. Deploy Application (run raw_data.py manually or via the shell script that runs automatically on deploy)


VERIFICATION:
1. Check data in newly created Dynamo DB table
2. Check email for notifications



----------------------------------------------------------------------------------------------
E. Screenshots 
----------------------------------------------------------------------------------------------
1. Screenshots Submission file as ...\CloudProject2_M03P02_SN\ACSC_OCT21_SEEMA_NAIR_CloudProject2_M03P02.docx
2. Also in folder structure at ...\CloudProject2_M03P02_SN\M03P02_SN_Screenshots



----------------------------------------------------------------------------------------------
F. Files 
----------------------------------------------------------------------------------------------
1. JSON Files -  
	...\CloudProject2_M03P02_SN\M03P02_SN_CFTemplates\CF_Template_Task1.json
	...\CloudProject2_M03P02_SN\M03P02_SN_CFTemplates\CF_Template_Task2.json
	...\CloudProject2_M03P02_SN\M03P02_SN_CFTemplates\CF_Template_Task3.json
2. Shell Scripts - 
	...\CloudProject2_M03P02_SN\M03P02_SN_CodeDeployFiles\m03p02sn_AutoExecuteOnCodeDeploy\scripts\m03p02sn-start.sh
	...\CloudProject2_M03P02_SN\M03P02_SN_CodeDeployFiles\m03p02sn_AutoExecuteOnCodeDeploy\scripts\m03p02sn-stop.sh
	...\CloudProject2_M03P02_SN\M03P02_SN_CodeDeployFiles\m03p02sn_AutoExecuteOnCodeDeploy\scripts\post-install.sh
	...\CloudProject2_M03P02_SN\M03P02_SN_CodeDeployFiles\m03p02sn_AutoExecuteOnCodeDeploy\scripts\pre-install.sh
3. Appspec - ...\CloudProject2_M03P02_SN\M03P02_SN_CodeDeployFiles\m03p02sn_AutoExecuteOnCodeDeploy\appspec.yml
4. Lambda Function Code - ...\CloudProject2_M03P02_SN\anomaly_detection.py
5. Application - ...\CloudProject2_M03P02_SN\M03P02_SN_CodeDeployFiles\m03p02sn_AutoExecuteOnCodeDeploy\service\raw_data.py
6. Dependencies - ...\CloudProject2_M03P02_SN\M03P02_SN_CodeDeployFiles\m03p02sn_AutoExecuteOnCodeDeploy\service\requirements.txt



------------------------------ THANK YOU ----------------------------------------------------------