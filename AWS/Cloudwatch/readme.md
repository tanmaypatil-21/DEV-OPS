# $${\color {red} \textbf {Create Custom Metrics Using Cloudwatch:}}$$

 ## Step 1: 
- Create iam role with cloudwatch full access and ssm full access
   

## Step 2:
- launch ec2 instance and  attach  role
- select instance->click on Action>Security->Modify IAM Role

## Step 3 :
- go to AWS System Manager Service
- create ssm parameter
- dont forget to change aws:InstnceID
  
**Enter this Value for the SSM Parameter**

````
{
	"metrics": {
		"append_dimensions": {
			"InstanceId": "${aws:InstanceId}"
		},
		"metrics_collected": {
			"mem": {
				"measurement": [
					"mem_used_percent"
				],
				"metrics_collection_interval": 60
			},
            "disk": {
				"measurement": [
                     "disk_used_percent"
				],
				"metrics_collection_interval": 60
			}
		}
	}
}
````


## Step 4 : Cloudwatch Agent Installation

**1.Download Cloudwatch Agent**
````
wget https://s3.amazonaws.com/amazoncloudwatch-agent/linux/amd64/latest/AmazonCloudWatchAgent.zip
````

**2.Unzip**
````
unzip AmazonCloudWatchAgent.zip
````

**3.Install script**
````
sudo ./install.sh
````

**4. ssm-paramereter**
- Note: Change SSM parameter name
````
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -a fetch-config -m ec2 -c ssm:/ssm-parameter-name -s
````


**5.check status of cloudwatch agent**
````
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -m ec2 -a status
````

**Step 5:**

- go to cloudwatch and create alarm 
- you will see cloudwatch agent

![image](https://github.com/user-attachments/assets/e240a4b5-7b75-4e5d-83f2-e1632151c585)
