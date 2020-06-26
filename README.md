# Prerequisites

## Scope of the project is to create the VPC in AWS and install Jenkis using Terraform. Code should work in every region of AWS. 

VPC requirements
6 subnets
3 private subnets
3 public subnets  

Public subnets should have IGW attached to it in order to have access to the internet.  

Configure route tables properly.
Once private and public subnet created, please create ec2 instance (manually)  on public subnet and ping google.com. If everything is successful, you should have proper response

Moving forward, on that VPC you just provisioned, please create ec2 intance to install Jenkins:

Jenkins has to be installed using terraform provisioner.
One command should create VPC with the components, and build jenkins on top of it.
Once the Jenkins up and running, please print out the username password as an output
Please read the instructions and requirements of the instance needed for Jenkins.

## Since this project has two components we will split the presentation in two: First it will be the creation and components of the VPC. Second will be Jenkis instalation.

# VPC


- - ## Components of the VPC:

- - Private and Public Subnets

1.The configuration for this scenario includes a VPC with a public and private subnets. We recommend this scenario if you want to run a public-facing web application, while maintaining back-end servers that aren't publicly accessible.
2.We will use 3 private subnets and 3 public subnets. Our EC2 instance for Jenkis will be attached to a public subnets in order to have internet connections.

--Internet Gateway 
1. Internet gateway is a horizontally scaled, redundant, and highly available VPC component that allow communications between VPC and Internet.
2. Internet Gateway should be attached to VPC.
3. Add a route to your subnet's route that directs internet-bound traffic to the internet gateway. If a subnet is associated with a route table that has a route to an internet gateway, it's know as a public subnet. If a subent is associated with a route table that does not have a route to an internet gateway, it's know as a private subnet.

-- Route Table

Route table contains a set of rules, called route, that are used to determine where network traffic from your subnet or gateway is directed.
each subnet in your VPC must be associated with a route table.

-- Security Group AWS 

1. Security group acts as a virtual firewall for your instance to control inbound and outbound traffic.
when you launch an instance in a VPC, you can assign up to five security groups to the instance.
2. Security groups act at the instance level, not the subnet level.
3. Each instance in a subnet in your VPC can be assigned to a different set of security groups.
4. By default a security group is dening all traffic, we need to specify which ports we want to use.

--Key Pair 

amazon ec2 uses public key cryptography to encrypt and decrypt login information.
public key cryptography uses a public key to encrypt a piece of data, and then the recipiend uses the private key to decrypt the data.
the public and private keys are know as a key pair.
public key cryptography enables you to securely access your instance using a private a key instead of a password.
Availability Zones link

availability zone is one or more discrete data center with redundant power networking, and connectivity is an AWS Region.
availability zones allow you to operate production applications and databases that are more highly available, fault tolerant, and scalable than would be possible from a single data center.
each region has a different number of availability zones, at least two is the minimum.
Amazon Elastic Compute Cloud (EC2) link

Amazon EC2 provides scalable computing capacity in the AWS cloud
virtual computing environments, known as instances.
Jenkins
Automation Tool link

Jenkis is a self-contained, open source automation server which can be used to automate all sorts of tasks related to building, testing, and delivering or deploying software.
Deliver Infrastucture as code
Terraform

Write declarative configuration files.

collaborate and share configurations
evolve and version your infrastructure
automate provisioning
Plan and predict changes

clearly mapped resources dependencies
separation of plan and apply
consistent, repeatable workflow.
Create reproducible infrastructure

reproducible production, staging, and development environments
shared modules for common infrastructure patterns
combine multiple providers consistently
Terraform Structure.
backend.tf

backends determine where state is tored.
igw.tf

provided resources to create a VPC Internet Gateway
instance.tf

provides an EC2 instance resources
key_pair.tf

key_pair deployer
networking.tf

networking resources provided in this file
null_resource.tf

resources that implements the standar lifecycle.
Jenkis password will be displayd at the end.
all atributes for Jenkis installation called remote-exec provisioner.
private_subnet.tf

resources for private subnets
provider.tf

provider is responsible for understanding API interactions and exposing resources.
public_subnet.tf

 - resources for public subnets. 
securitygroupaws.tf

 - resources for security groups. 
setenv.sh

 - resources for set environmental variables
variable.tf

 - variables set-up
vpc.tf

VPC resources
/configurations/regions

.tfvarsfiles

variable definitions files, each regions has .tfvars files.
bahrain.tfvars

canada.tfvars

frankfurt.tfvars

hong_kong.tfvars

ireland.tfvars

london.tfvars

milan.tfvars

mumbai.tfvars

ohio.tfvars

oregon.tfvars

paris.tfvars

sao_paulo.tfvars

seoul.tfvars

singapore.tfvars

stockholm.tfvars

sydney.tfvars

tokyo.tfvars

virginia.tfvars
