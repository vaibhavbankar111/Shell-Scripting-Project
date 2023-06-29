The Amazon S3 notification feature enables you to receive notifications when a certain event occurs inside your S3 Storage bucket.
To get notifications, first, add a notification configuration that reads the event you want Amazon S3 Bucket to publish and
the destination where Amazon S3 will send the notifications. This configuration is stored in the notification sub-resource 
that is associated with a bucket.

1. Each time a new video/series/documentary is uploaded in S3 Storage Bucket, you receive a notification.
Most organizations use S3 since it is cost-efficient.

2. Under the hood, the S3 bucket triggers Lambda Function.
Since Lambda is a server less compute, it allows you to run code that can be written in any programming language.
Also, it follows Pay As You Go pricing where you are charged based on the usage.

3. This information is sent to SNS (Simple Notification Service), which is a fully managed messaging service provided by
Amazon Web Services (AWS). SNS provides reliable message delivery, scalability, and fault tolerance, making it suitable
for building robust and scalable messaging systems in the cloud.

4. From SNS, it depends from platform to platform.
If it is a simple blog posting website, the content can be stored in a S3 bucket and email notifications can be sent to
all the subscribers. Whereas in case of Netflix, there would be some additional queuing, transcoding the video to 
different formats, extracting metadata, or performing other media processing tasks.

5. IAM — IAM stands for Identity and Access Management. IAM allows you to create and manage roles, which are sets of 
permissions that can be used to access AWS resources, such as EC2 instances, Lambda functions, or other services. 
In this specific scenario, the Lambda function needs to have permission to be invoked by S3 Bucket and invoke SNS.
Hence we will need to grant IAM permission to Lambda Function.

Here are the steps we will need to follow:-

Step 1 — Launch an AWS EC2 Instance. Enable HTTP and HTTPS traffic. You can create a new key pair or use an existing one.
Once the instance is in a running state, you can connect it via console or using the SSH Key Pair.

Step 2— Configure AWS CLI.
Once you have connected to your EC2 Instance, you need to install and configure AWS CLI using the below command
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" 
sudo apt install unzip
unzip awscliv2.zip 
sudo ./aws/install
aws configure
On the top right corner of your AWS Console, click on Security Credentials
Goto Access Keys, Generate new access key. Remember to download the key as a CSV, and enter these details.
Run the “aws configure” command: Type “aws configure” in the command prompt or terminal window and press Enter.
This will start the configuration process.

Provide AWS access key ID:
Provide AWS secret access key:
Provide default region name:
Provide default output format:

Step 3— You can fork my repository and then using the clone command, you can get the repository from Github to your EC2 Instance.

git clone https://github.com/pawankahurke/Shell-Scripting-Projects.git
cd Shell-Scripting-Projects/
cd aws-event-triggering/
Once you have cloned, you should be able to see the code on your EC2 Instance.

Step 4 — Some important command that you should enter before you execute the shell script
sudo apt-get install jq
sudo apt-get install zip unzip
sudo apt-get update

Step 5— Using Shell Script, we will create S3 Bucket, Lambda Function, and Assign IAM Role(To be invoked by S3 Bucket and invoke SNS).
execute this shell script,
chmod 777 s3-notification-triggers.sh
./s3-notification-triggers.sh

So, what we have done via Shell Script is that we have

. Created IAM Role

. Created S3 Bucket

. Created Lambda Function

. Created SNS Topic and added personal email as a subscription to this SNS Topic.

Once your script is executed, you will receive an email asking about your confirmation of the subscription.
If you go ahead and confirm, you will receive a notification email if anything new is added to the S3 Bucket.
Now, when you will go to your AWS Console, you will see the following resources created.
Each time a new video/series/documentary is uploaded in S3 Storage Bucket, you receive a notification on your email id.
thank you 








