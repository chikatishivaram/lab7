Go to Root Account
$ sudo  su –

Open browser (https://get.docker.com/) go to that link
Copy the commands and paste it in terminal

# curl -fsSL https://get.docker.com -o get-docker.sh ( this will download shell script in the machine)

# sh get-docker.sh  ( This will execute the shell script, which will install docker )

   Copy and paste the below two commands

#    sudo curl -L "https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

# sudo chmod +x /usr/local/bin/docker-compose

	
How to check docker compose is installed or not?


# docker-compose  --version

Create a docker compose file for setting up LAMP architecture

# docker pull httpd 

# vim docker-compose.yml

---
version: '3'

services:
 mydb:
  image: mysql:5
  environment:
   MYSQL_ROOT_PASSWORD: sunilsunil

 apache:
  image: httpd
  ports:
   - 6060:8080
  links:
   - mydb:mysql


 php:
  image: php
  links:
   - mydb:mysql
   - apache:tomcat
...



# docker-compose up -d

To see the list of the containers
# docker container ls
( Observation - we are unable to see the php container)

# docker ps -a
