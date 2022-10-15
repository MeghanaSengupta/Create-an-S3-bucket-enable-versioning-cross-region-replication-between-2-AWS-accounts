# Create-an-S3-bucket-enable-versioning-cross-region-replication-between-2-AWS-accounts-suding-CLI

aws s3 mb s3://session10bucket --region eu-west-2

aws s3api put-bucket-versioning --bucket session10bucket --versioning-configuration Status=Enabled

To test the bucket versioning state run get-bucket-versioning command (OSX/Linux/UNIX) using the name of the bucket as command parameter:

aws s3api get-bucket-versioning --bucket  session10bucket

* create Source bucket
aws s3 mb s3://session10bucket --region eu-west-2

**Enable Versioning
aws s3api put-bucket-versioning --bucket session10bucket --versioning-configuration Status=Enabled

To test the bucket versioning state run get-bucket-versioning command (OSX/Linux/UNIX) using the name of the bucket as command parameter:

aws s3api get-bucket-versioning --bucket session10bucket

* Create destination bucket
aws s3api create-bucket --bucket destination-bucket-session10cross-region --region ap-south-1 --create-bucket-configuration LocationConstraint=ap-south-1

****Enable versioning
aws s3api put-bucket-versioning --bucket destination-bucket-session10cross-region --versioning-configuration Status=Enabled 

***Create a Role
aws iam create-role --role-name S3replicationRole --assume-role-policy-document file://s3-trust-policy.json

* Create IAM Role Policy and attach to role
aws iam put-role-policy --role-name S3replicationRole --policy-document file://s3-role-perms.json --policy-name S3replicationRolePolicy

***Add replication configuration to the source bucket.
          

***Add replication configuration with below command
aws s3api put-bucket-replication --replication-configuration file://replicationrule.json --bucket session10bucket 


**Enable Replication
aws s3api put-bucket-replication --replication-configuration file://replicationrule.json --bucket destination-bucket-session10cross-region

**Retrive Replication Data
aws s3api get-bucket-replication --bucket session10bucket

![image](https://user-images.githubusercontent.com/109040029/195968059-b2f70d56-db7a-4b51-a7bc-f670e2608d01.png)

![image](https://user-images.githubusercontent.com/109040029/195968068-ec0cf4d5-41e1-4078-8888-66234aae0543.png)

![image](https://user-images.githubusercontent.com/109040029/195968075-88737416-c1ab-40d5-bc09-26a0b8e8622e.png)

![image](https://user-images.githubusercontent.com/109040029/195968078-dca70199-a391-4b0b-b6ac-c87e4fa404f2.png)




