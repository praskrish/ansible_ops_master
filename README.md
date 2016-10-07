Lab Instructions to work with Ops Playbooks

Playbook # 1
VALIDATE OS SECURITY VULNERABILITIES - ~10min

Login to Ansible Tower machine

Browse to: https://tower-GUID.rhpds.opentlc.com
Browse Projects
Ansible projects containing playbooks

ansible Ops

Browse Inventories

Hosts which playbooks are applied to, can be static (demonstrated) and dynamic (i.e. ec2, pre-built scripts, custom)

Click on "JOB TEMPLATES" 
Job Templates: Check OS Security Vulnerabilities

Start job (rocket)
Watch job - wait until the job status is: Successful

Playbook #2
SETUP TOMCAT STANDALONE

Job Templates: Deploy Tomcat Standalone
Start job (rocket)
watch job - wait until the job status is: Successful
Web Browser: Test Tomcat Home page

Playbook #3

SETUP WORDPRESS APP with NGINX and Maria DB
Job Templates: eap domain - setup infrastructure - modify

start job (rocket)
Web Browser: Test Wordpress App

Pre-requisites

Red Hat Customer Support Portal credentials
Red Hat Subscription - like JBoss NFR
