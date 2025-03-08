# Linux-Management_Pramoda Medis
 
 Question 27

 README: User Management and Server Security Tasks

Summary

This document outlines the tasks required to configure user management, SSH access, and firewall settings on a Linux server. The goal is to create a new user, configure secure access, grant necessary permissions, implement a firewall, and document the process.

Tasks Breakdown

1. Create a New User

Create a new user named student on the Linux server.

Set a secure password for the user.

2. Configure SSH Key-Based Authentication

Switch to the student user.

Generate a public and private SSH key pair.

Configure SSH to use key-based authentication for the student user.

Store the private key (student_private_key.pem) for later use in SSH clients.

3. Grant Website Content Modification Permissions

Assume the web server's document root is /var/www/html.

Modify permissions to allow student to modify website content.

Ensure proper ownership and access rights.

4. Implement a Firewall

Configure a firewall to protect the server.

Allow TCP traffic on ports 80, 22, and 443 from:

192.168.1.0/24 network

10.0.0.0/24 network

The current connection’s IP address.

Block all other incoming connections.

Ensure the firewall logs blocked traffic to system logs.

5. Enable Firewall on Boot

Configure the firewall to start automatically on system boot.

6. Export Firewall Rules

Export firewall rules and settings to firewall_rules.txt.

Ensure the exported file is included in the final submission.

7. Document the Steps and Configurations

Take screenshots of relevant commands and configurations.

Create a document (PowerPoint or PDF) containing:

Steps followed.

Commands executed.

Screenshots.

Server IP address or DNS hostname.

Attach the documentation file to the submission.

8. Provide Required Files for Submission

student_private_key.pem: Contains the student user’s private SSH key.

firewall_rules.txt: Contains the exported firewall rules.

documentation.pptx or documentation.pdf: Contains screenshots and explanations of configurations.

Submission Checklist

✅ student_private_key.pem (private SSH key for student user)

✅ firewall_rules.txt (exported firewall rules)

✅ documentation.pptx or documentation.pdf (screenshots and configurations)




