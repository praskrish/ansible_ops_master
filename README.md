#Ansible Ops Playbook Setup and Execution

##Ansible Tower Login Credentials

- Login to Ansible Tower machine
https://tower-GUID.rhpds.opentlc.com

- Two roles:
admin / r3dh4t1!
user / passw0rd

- Verify Tower
$ansible-tower-service status
$ tower-manage changepassword admin


##Test Ansible Ops Jobs in Tower

###Add Hosts for Playbook Usage
 
- Click on Inventories/Security Vulnerability/SecurityFix_Servers
  Add Host
  rhel1.example.com, rhel2.example.com

- Click on Inventories/Tomcat Servers/Add Host
  rhel4.example.com
  
##Run Playbooks

###Click on "JOB TEMPLATES" 
Playbook #1: Check Open SSL Vulnerability 
Start job (rocket) 
Watch job - wait until the job status is: Successful

Playbook #2: SETUP TOMCAT STANDALONE
Deploy Tomcat Standalone Start job (rocket) 
watch job - wait until the job status is: Successful 
Web Browser: Test Tomcat Home page
http://rhel4-GUID.rhpds.opentlc.com:8080/

Playbook #3: Setup Wordpress App.
Inventories - Wordpress App Server - Add Host
rhel3.example.com
Click on "JOB TEMPLATES" 
Playbook #1: WORDPRESS APP
Start job (rocket) 
Watch job - wait until the job status is: Successful
Web Browser: Test Wordpress App
http://rhel3-GUID.rhpds.opentlc.com/wp-admin/install.php

