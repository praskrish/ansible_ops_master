Lab Environment Credentials can be found in the lab provisioning description.

## Deploy EAP Domain - ~15min

Login to Ansible Tower machine
* Browse to: https://tower-GUID.rhpds.opentlc.com
* Browse Projects

Ansible projects containing playbooks
* ansible app - EAP Domain
* ansible middleware playbooks 

Browse Inventories
* Hosts which playbooks are applied to, can be static (demonstrated) and dynamic (i.e. ec2, pre-built scripts, custom)

Setup Infrastructure and Deploy App
* Job Templates: eap domain - setup infrastructure
  * Start job (rocket)
* watch job - wait until the job status is: Successful

Web Browser: Test Web Server and EAP domain
* http://web1-GUID.rhpds.opentlc.com:8888/mod_cluster_mananger
  * Should see Node eap1
* http://eapd-GUID.rhpds.opentlc.com:9990

Job Templates: eap domain - deploy app
* Start job (rocket)
* Watch job - wait until the job status is: Successful

Web Browser: Test Web Server and EAP domain
* http://web1-GUID.rhpds.opentlc.com:8888/mod_cluster_mananger
  * Should see Node eap1 and associated jboss-kitchensink context
* http://web1-GUID.rhpds.opentlc.com/jboss-kitchensink

Need additional node for testing
Add additional node to inventory
* Browse to Inventories
  * ansible app > eap > eap-nodes
  * + Add Host
  * Host Name: eap2.example.com
  * Variables, under ---
     * eap_node_name: eap2
  * Save

Add additional Node to EAP
* Job Templates: eap domain - setup infrastructure - modify
  * Extra variables (it’s yaml, ensure text lines up)
     * Uncomment (remove the hash): - eap2
  * Save
  
Job Templates: eap domain - setup infrastructure  
* start job (rocket)

Web Browser: Test Web Server and EAP domain
* http://web1-GUID.rhpds.opentlc.com:8888/mod_cluster_mananger
    * Should see Node eap1 and eap2
    
Job Templates: eap domain - deploy app
* start job (rocket)

Web Browser: Test Web Server and EAP domain
* http://web1-GUID.rhpds.opentlc.com:8888/mod_cluster_mananger
  * Should see Node eap1, eap2 and associated jboss-kitchensink context
* http://web1-GUID.rhpds.opentlc.com/jboss-kitchensink

## Additional deployment methods (bonus labs)
Pre-requisites
* Red Hat Customer Support Portal credentials
* Red Hat Subscription - like JBoss NFR 
* Jobs do require more time as the binaries will directly be downloaded from Red Hat Customer Support Portal

Deploy Standalone EAP - ~16 min
* Job Templates: middleware ansible - eap
  * Start job
  * Survey
    * RHCSP username
    * RHCSP password
  * Launch

Web Browser:
* http://eaps-GUID.rhpds.opentlc.com:8080/jboss-kitchensink

Deploy Standalone BPM Suite - ~
* Job Templates: middleware ansible - bpms
  * Same as above
* Web Browser:
  * http://bpms-GUID.rhpds.opentlc.com:8080/business-central

