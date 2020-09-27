# Deploy a high-availability web app using CloudFormation

## To access the Load Balancer for output values, please click the link below
<a href="http://WebAppLB-1774696290.us-west-2.elb.amazonaws.com" target="_blank">http://WebAppLB-1774696290.us-west-2.elb.amazonaws.com</a>

## Create an architectural diagram on LucidChart
### Needs:

1. Launch Configuration for application servrs to deploy four servers across two Availability Zones:
- [x] two private subnets
- [x] two public subnets
- [x] two vCPUs
- [x] at least 4GB of RAM
- [x] OS is Ubuntu 18, so an appropriate Instance size and Machine Image (AMI) is necessary
- [x] Allocate at least 10 GB disk space

2. Security Groups and Roles
- [x] Create an IAM role that allows instances to read S3
- [x] App communicates on default `HTTP Port: 80` - servers will need this inbound port open since it will be used with the **Load Balancer** and **Load Balancer Health Check**
- [x] Outbound network needs to be unrestricted in order to download and update its software
- [x] Load balancer should allow all public traffic `(0.0.0/0)` on `port 80` inbound (`default HTTP port`). Outbound will only use `port 80`
- [x] App needs to be deployed into private subnets with a Load Balancer located in a public subnet
- [x] One of the output exports of the **CloudFormation** script should be the public URL of the **LoadBalancer**
- [x] **Bonus**: add `http://` in front of the load balancer **DNS Name** in the output, for convenience.

## Project Rubric

### The Basics
- [x] Parameters: The more the better, but an exaggerated number of params can be messy (say, 10 or more). 1 or 0 is definitely lacking.
- [x] Resources: This is a mandatory section of the script. It's required to have a LoadBalancer, Launch Configuration, AutoScaling Group, a health check, security groups, a Listener, and a Target Group.
- [x] Outputs: This is optional, but it would be nice to have a URL here with the Load Balancer, DNS Name, and "http" in front of it.

- [x] Working Test: If the student provides a URL to verify his work is running properly, it will be a page that says "it works! Udagram, Udacity"

### Load Balancer
- [x] Target Group: The auto-scaling group needs to have a property that associates it with a target group. The Load Balancer will have a Listener rule associated with the same target group.
- [x] Health Check and Listener: Port 80 should be used in Security Groups, Health Checks, and Listeners associated with the Load Balancer.

### Auto-Scaling
- [x] Subnets: Students should be using PRIV-NET (private subnets) for their auto-scaling instances.
- [x] Machine Specs: The machine should have 10 GB or more of disk and should be a t3.small or better.
- [x] SSH Key: There shouldn't be a 'keyname' property in the launch config.

### Bonus
- [x] Output: Any values in the output section are a bonus.
- [ ] Bastion Host: Any resource of type AWS::EC2::Instance, optional, but nice to have.
