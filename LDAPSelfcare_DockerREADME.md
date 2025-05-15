# LDAPSelfCare-OnDocker
Move  my Ldapself care app at https://github.com/tushar4631/LDAPSelfCare.git on docker.
LDAP Password change app for most of the LDAP implementation like IBM SDS, AD

## Motivation
Modernazation of app on docker and running it as container
This app supports password change for a user by self and change password to new password.
It takes old password for validation of current user and changes the password if the aclentry allows the user to change its own password.


## Installation

1) Install docker ce on your PC/VM.

2) There is docker hub repository where I have pushed the IBM Websphere Liberty with my LdapSelfcare app
```txt
docker pull tushar4631/tushar_ldapselfcarev1
```
3) Download the zip of this github repository and unzip it on Local.

4) Open the LdapCon.properties file in the repos. Change it as per your need
```txt
INITIAL_CONTEXT_FACTORY = com.sun.jndi.ldap.LdapCtxFactory
PROVIDER_URL= ldap://<ldaphostname>:<port>
SECURITY_AUTHENTICATION=simple
SECURITY_PRINCIPAL=cn=root
SECURITY_CREDENTIALS=<password>
BASE_DN=<base dn of the ldap instance>
USER_SEARCH_ATT=<uid or cn or any other user search att you use>
```
5) Check the Dockerfile at current location in local and run the following command to build the image as per your environment 
```txt
docker build -t ldapselfcare:myenv .
```
6) Run the docker image you just build to run the application
```txt
docker run -d -p 81:9080 --name=ldapselfcare ldapselfcare:myenv
```
7) Access this container using the bash by below command:
```txt
docker container exec -it ldapselfcare /bin/bash
```
8) Once you get into the container bash. Run the command

```txt
/tmp/copying.sh
```
Press exit to exit the container bash

9) You can now access the application on :
http://<hostname>:81/LDAPSelfCare/


10) You can check the logs of application by command

```txt
docker logs -f ldapselfcare
```
