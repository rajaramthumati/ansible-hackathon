# Pre-requisites

ansible version 2.0 or later

# Installation instructions to deploy Tomcat

1) git clone -b develop https://scm.lhstaging.com/allergan/lh-ansible.git
2) Goto tomcat_deployment directory under lh-ansible
3) Change the values in inventory file
4) Create file with group name what you mentioned in inventory file with .yml extension under group_vars directory
   Example:
     [dev]
     locahost
     
     In the above example dev is group name and localhost is the target machine which is part of dev group.
     
     as per the above example dev is the group name and we should create file under group_vars directory as dev.yml with variables like below
     
     http_port: 8080
     https_port: 8443
     tomcat_directory_name: tomcat8
5) Run below command to deploy Tomcat
   ansible-playbook -vvvv -i inventory deploy_tomcat.yml --extra-vars '{"environment":"dev","artifact_url":"url-to-download-artifact","context":"context-of-artifact"}' --vault-password-file password_file.txt
     
     
      
