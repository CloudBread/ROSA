


## Prerequisites

### Step 1
Review the prerequisites documentation https://docs.openshift.com/rosa/rosa_getting_started/rosa-aws-prereqs.html

### Step 2
AWS CLI, AWS Config

### Step 3 - install ROSA CLI, SetUp

참조 : https://docs.openshift.com/rosa/rosa_getting_started/rosa-setting-up-environment.html

1. Download the [latest release](https://access.redhat.com/products/red-hat-openshift-service-aws/) of the rosa CLI for your operating system.

```bash
wget https://github.com/openshift/rosa/releases/download/v1.0.2/rosa-linux-amd64
chmod 755 rosa-linux-amd64
sudo mv rosa-linux-amd64 /usr/local/bin/rosa
```

2. download and install oc
```
rosa download oc
ls
tar zxvf openshiftxxxx
chmod 755 oc
sudo mv oc /usr/local/bin/
```

3. enable ROSA
![](images/enable-rosa.gif)

4. ROSA init
```bash
rosa init

```

![](images/rosa-init.gif)


### Step 4 - Create Cluster
```bash
rosa create cluster --interactive
```

![](images/create-cluster.gif)


```bash
rosa list clusters

## describe cluster

rosa describe cluster -c <cluster-name>
```


```bash
rosa

rosa completion > /etc/bash_completion.d/rosa

source /etc/bash_completion.d/rosa

## verify AWS account permission
rosa verify permissions

## Red Hat account login
rosa login

rosa verify quota --region=ap-northeast-2

rosa whoami

rosa init

```


### Step 4 - ROSA Config
se

Open https://portal.aws.amazon.com/billing/signup.
Follow the online instructions.
Part of the sign-up procedure involves receiving a phone call and entering a verification code on the phone keypad.
Step 3
Create a Red Hat account

If you do not already have a Red Hat account, create one here https://cloud.redhat.com. Accept the required terms and conditions. Then check your email for a verification link.
Step 4
Create an IAM user

https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html
https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html
Step 5
Create SCP

https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create.html
https://docs.openshift.com/rosa/rosa_getting_started/rosa-aws-prereqs.html#rosa-minimum-spc_prerequisites
Step 6
Download, install and configure AWS CLI

https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html

If you’ve just installed the AWS CLI or want to simply make sure it is using the correct AWS account, follow these steps in a terminal:

aws configure
provide the AWS Access Key ID and press enter
provide the AWS Secret Access Key and press enter
provide default region you want to deploy into
It should look like the following as an example:

$ aws configure AWS Access Key ID: AKIA0000000000000000 AWS Secret Access Key: NGvmP0000000000000000000000000 Default region name: us-west-2 Default output format: table Verify the Configuration#

If you are making use of AWS cloud 9, Cloud 9 comes with the AWS CLI pre-installed, you will however need to run aws configure to update and make sure that the credencials being used have the policies needed for ROSA and that you have the correct AWS region.

Step 7
Download, install and configure ROSA CLI

The ROSA CLI is a command line tool used to provision and manage Red Hat OpenShift clusters on AWS, this tool does not replace the more traditiona oc or kubectl commands for manageing OpenShift. The ROSA CLI will depend on and interact with the AWS CLI. Permissions needed for creating AWS resources such as VPCs, EC2 instances etc will be defined when configuring the AWS CLI in Step 6.

You can download the latest version of the ROSA CLI fro you OS here: https://github.com/openshift/rosa/releases/tag/v1.0.2

Linux instructions

wget https://github.com/openshift/rosa/releases/download/v1.0.2/rosa-linux-amd64
chmod 755 rosa-linux-amd64
sudo mv rosa-linux-amd64 /usr/local/bin/rosa
Step 8
download and install oc

rosa download oc
ls
tar zxvf openshiftxxxx
chmod 755 oc
sudo mv oc /usr/local/bin/
Step 9
Enable the ROSA service

Go to the AWS ROSA console home
console.aws.amazon.com/rosa/home
Click on the Enable ROSA button
Rosa console
Step 10
ROSA init

ROSA init will run through several steps, it launch a CloudFormation infrastructure as code stack which creates an IAM user within the account. It will validate if the correct SCP permisions are in place, check AWS service limits such as VPC, EC2 instances, EIPS. Check if the ROSA service has been enabled. Rosa init will link to your Red Hat accout. ROSA init need only be run once within the account and each of these steps can be run separately however I find it faster to simply process the init and have it do everything for me.

rosa init

Create ROSA Cluster
Configuring users and IDP
Cluster Access