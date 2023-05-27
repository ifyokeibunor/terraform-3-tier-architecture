# 3-tier-architecture-on-aws-using-terraform
Terraform code to create 3 tier architecture on aws 

![image](https://github.com/ifyokeibunor/terraform-3-tirer-architecture/assets/104580680/f69412d1-aff2-4714-9fb2-91d41bd95342)

**TERRAFORM FILES IN THE PROJECT ARE:**
Let’s walk through the files involved in setting up the 3-tier architecture.

Root module files -

**provider.tf** : This file contains the provider definition for the project. So I have passed aws as the provider and region for the architecture setup.

**terraform.tfvars:** This file contains the values for the variables used in the configuration file. We can specify the values for the variables in this file instead of hardcoding them in the configuration file.

**variables.tf:** This file contains the variable definitions for the project.

**outputs.tf**: This file contains the output definitions for the project. Outputs allow us to retrieve information about the resources created by our configuration file.

**networking.tf**: This file contains the configuration code for VPC, Nat gateway, Elastic IP, Internet gateway, and route tables for private and public subnets.

web.sh and app.sh scripts : These scripts contains commands to setup httpd for testing .

**webTier.tf:** This file contains the configuration code for setting up the Web Tier .

**RESOURCES CREATED IN WEBTIER **-
> - Two public subnets
> - Public Route table association with subnets
> - Two security groups
>     * - Security group for load balancer
>     * - Security group for Web servers
> - Application load balancer-internet facing
> - Listener group
> - Target group
> - Two auto-scaling groups 
> -Launch template

**RESOURCES CREATED IN APP TIER **-
> - Two private subnets
> - Private Route table association with subnets
> - Two security groups
>  * - Security group for load balancer
>  * - Sec> urity group for APP servers
> - Application load balancer - internal
> - Listener group
> - Target group
> - Two auto-scaling groups
> - Launch template

**RESOURCES CREATED IN DATA TIER **-
> - Two private subnets
> - Security group for rds
> - Subnet group
> - RDS - multi AZ

**DEPLOYMENT:**
**Intialises provider plugin and modules**
> terraform init
**Validates the configuration files**
> terraform validate
**Shows the execution plan**
> terraform plan
**Creates the infrastructure**
> terraform apply

In addition , some reusable modules have been created using terraform to define different resources needed for the infrastructure and called them from the main configuration files. Modules allow us to abstract away complexity and reuse code for creating multiple copies of the same resource as per requirement.
**modules -**
> - application_load_balancer
> - autoscaling_group
> - elastic_ip
> - internet_gateway
> - launch_template
> - listener_group
> - nat_gateway
> - rds
> - route_tables
> - rt_association
> - security_group
> - subnet
> - subnet_group
> - target_group
> - vpc
