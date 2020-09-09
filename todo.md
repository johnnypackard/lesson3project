# Deploy a high-availability web app using CloudFormation

## Create an architectural diagram on LucidChart
### Needs:

1. Launch Configuration for application servrs to deploy four servers across two Availability Zones:
- [ ] two private subnets
- [ ] two public subnets
- [ ] two vCPUs
- [ ] at least 4GB of RAM
- [ ] OS is Ubuntu 18, so an appropriate Instance size and Machine Image (AMI) is necessary
- [ ] Allocate at least 10 GB disk space

2. Security Groups and Roles
- [ ] Create an IAM role that allows instances to use S3
- [ ] App communicates on default `HTTP Port: 80` - servers will need this inbound port open since it will be used with the **Load Balancer** and **Load Balancer Health Check**
- [ ] Outbound network needs to be unrestricted in order to download and update its software
- [ ] Load balancer should allow all public traffic `(0.0.0/0)` on `port 80` inbound (`default HTTP port`). Outbound will only use `port 80`
- [ ] App needs to be deployed into private subnets with a Load Balancer located in a public subnet
- [ ] One of the output exports of the **CloudFormation** script should be the public URL of the **LoadBalancer**
- [ ] **Bonus**: add `http://` in front of the load balancer **DNS Name** in the output, for convenience