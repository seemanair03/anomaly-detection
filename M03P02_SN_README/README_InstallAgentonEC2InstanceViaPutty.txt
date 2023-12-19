Create Key Pair and save the downloaded .ppk file
Create Cloudformation stack 
After CloudFormation is Successful, go to newly created instance
Copy the public DNS
Open Putty - add DNS details and browse for the .ppk file and Open.

Login as: ec2-user


sudo yum update
sudo yum install ruby
sudo yum install wget
cd /home/ec2-user

wget https://aws-codedeploy-us-east-1.s3.us-east-1.amazonaws.com/latest/install
chmod +x ./install
sudo ./install auto

sudo service codedeploy-agent status

sudo service codedeploy-agent start
sudo service codedeploy-agent status


Create CodeDeploy
For Manual Run - After Successful deployment come to CLI and cd to the folder where the raw_data.py file is
Execute--> python3 raw_data.py