## To log in your aws account via command line, first you need to install aws cli on your instance:
- amazon linux : already installed by default
- ubuntu installation steps:
  ````
   sudo apt install unzip -y
   curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
   unzip awscliv2.zip
   sudo ./aws/install
  ````
- windows:
  ````
  https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html
  ````

# log to aws using cli
````
aws configure
````   
- provide access_key:
- provide secret_key:
- enter region: 

# list buckets in your region
````
aws s3 ls
````
# create new s3 bucket

````
aws s3 mb s3://newbucket-b53
````
# copy index file to bucket
````
aws s3 cp index.html  s3://newbucket-b53
````
# download file from s3
````
aws s3 cp s3://newbucket-b53/error.html  .
````
# list objects inside bucket
````
aws s3 ls s3://newbucket-b53
````
# delete file in bucket
````
aws s3 rm s3://newbucket-b53/error.html
````
# remove bucket
````
aws s3 rb s3://newbucket-b53
````

**reference:** 
````
https://docs.aws.amazon.com/cli/v1/userguide/cli-services-s3.html
````
