# AWS Two-Tier To-Do Application Deployment

## Project Overview

In this project, I deployed a To-Do List web application on AWS using two EC2 instances, an RDS MySQL database, and an Application Load Balancer.

The goal was to practice AWS networking, application deployment, database connectivity, and load balancing through a hands-on project.

The application allows users to add, view, update, and delete tasks.

## AWS Services and Tools

- **Amazon VPC:** Created a custom network with two public and two private subnets across two Availability Zones.
- **Amazon EC2:** Deployed the Node.js application on two instances.
- **Amazon RDS MySQL:** Used a private database to store tasks.
- **Application Load Balancer:** Routed application traffic between the two EC2 instances.
- **Security Groups:** Configured network access between AWS resources.
- **Internet Gateway and Route Tables:** Configured network routing.
- **Bastion Host:** Connected to the private RDS database from an EC2 instance.
- **Nginx:** Used as a reverse proxy for the Node.js application.
- **PM2:** Managed the application processes.
- **Git and npm:** Downloaded the application code and installed its dependencies.

## How It Works

1. A user opens the application through the ALB DNS address.
2. The ALB forwards the request to one of the two EC2 instances.
3. Nginx forwards the request to the Node.js application.
4. The application reads or updates data in the RDS MySQL database.
5. Both EC2 instances use the same database, so users can access the same tasks.

## Testing

I tested the deployment by:

- Opening the application through the ALB.
- Checking that both EC2 instances were healthy in the Target Group.
- Adding tasks and confirming they remained after refreshing the page.
- Testing the application API using curl.
- Checking that API requests used the ALB address.

## Challenges and What I Learned

During deployment, I worked through several issues:

- Fixed an Nginx configuration conflict that initially displayed the default welcome page.
- Investigated a `502 Bad Gateway` error and found a port conflict affecting the Node.js process.
- Fixed a `503 Service Temporarily Unavailable` error by registering the EC2 instances in the Target Group.
- Corrected API configuration issues that prevented tasks from appearing in the browser.

These issues helped me better understand Linux commands, networking, application processes, and troubleshooting on AWS.

## Application Source

The original To-Do List application code comes from the educational repository [Todo-Two-Tier](https://github.com/Himanshu-Sangshetti/Todo-Two-Tier).

My hands-on work focused on configuring the AWS infrastructure, deploying the application, connecting the database, troubleshooting issues, and testing the final deployment.

## Project Screenshots

Screenshots and an architecture diagram will be added to document the final deployment.
