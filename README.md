# AWS EC2 Web App Deployment

Project 1 in my DevOps/Cloud Engineering learning path: deploy a simple web application on AWS using core networking and compute services, configured manually through the AWS Console.

## Goals
- Practice AWS networking fundamentals (VPC, subnets, route tables)
- Practice EC2 provisioning and security group configuration
- Deploy and serve a simple web app on a public instance

## Todo
- [ ] Create a VPC with public and private subnets
- [ ] Configure an internet gateway and route tables for the public subnet
- [ ] Launch an EC2 instance (Ubuntu) in the public subnet
- [ ] Configure security groups to allow SSH (22) and HTTP (80) access
- [ ] Install and configure a web server (Nginx or Apache)
- [ ] Deploy a simple static site or small app (Node/Flask) to the server
- [ ] Verify access via the instance's public IP
- [ ] Document architecture with a simple diagram
- [ ] Write up README with steps taken and challenges solved

## Stretch Goals: Full-Scale Architecture

Once the base deployment above is working, extend it into a more production-like, highly available architecture with a database layer, autoscaling, load balancing, and backups.

### Database Layer
- [ ] Add a private subnet (if not already present) dedicated to data services
- [ ] Launch an RDS instance (e.g., MySQL/PostgreSQL) inside the private subnet
- [ ] Create a security group for RDS that only allows inbound access from the web tier's security group
- [ ] Update the application to read/write from the RDS database instead of local storage
- [ ] Verify the app can connect to RDS but the database itself is not publicly reachable

### Load Balancing & Autoscaling
- [ ] Create an Application Load Balancer (ALB) in front of the web tier
- [ ] Create a Launch Template based on the existing EC2 configuration (AMI, user-data, security group)
- [ ] Create an Auto Scaling Group (ASG) using the Launch Template across multiple Availability Zones
- [ ] Attach the ASG to the ALB as its target group
- [ ] Configure scaling policies (e.g., scale out on CPU > 60%, scale in on CPU < 20%)
- [ ] Test scaling behavior by generating load and observing new instances launch
- [ ] Confirm the app stays reachable through the ALB DNS name even as instances scale in/out

### Backups & Resilience
- [ ] Enable automated RDS snapshots with a defined retention period
- [ ] Take a manual RDS snapshot and practice restoring it to a new instance
- [ ] Set up periodic AMI backups of the web tier configuration (or rely on the Launch Template + user-data instead)
- [ ] Document a simple disaster recovery plan: what would you do if the primary AZ went down?

### Outcome
- [ ] Document the final architecture with an updated diagram showing web tier, ALB, ASG, and database tier across multiple AZs
- [ ] Write up what changed from the original single-instance design and why each addition improves availability, security, or resilience
