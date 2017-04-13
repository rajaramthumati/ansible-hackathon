# Pre-requisites

ansible version 2.0 or later

tomcat user should exists with sudo permissions on remote server where we need to deploy tomcat.

# Installation instructions to deploy Tomcat

1) git clone -b develop https://scm.lhstaging.com/allergan/lh-ansible.git

2) Goto tomcat_deployment directory under lh-ansible

3) Change the values in inventory file

4) Create file with group name what you mentioned in inventory file with .yml extension under group_vars directory

     Example for content in inventory file:
        [dev]
        locahost
     
     In the above example dev is group name and localhost is the target machine which is part of dev group.
     
     as per the above example dev is the group name and we should create file under group_vars directory as dev.yml with variables like below
     
     http_port: 8080
     https_port: 8443
     tomcat_directory_name: tomcat8
5) Run below command to deploy Tomcat

   ansible-playbook -vvvv -i inventory deploy_tomcat.yml --extra-vars '{"environment":"dev","artifact_url":"url-to-download-artifact","context":"context-of-artifact"}' --vault-password-file password_file.txt
   
    In the above command environment value should be your group name in inventory file (example: dev)
    artifact_url should be artifact url to download artifact (like http://10.60.16.81:8082/repository/allergan-snapshots/com/liquidhub/api/batch-api/1.0.0-SNAPSHOT/batch-api-1.0.0-20170412.084929-35.war)
    context value should be context of deployed war file (like batch-api).
     
     
      
