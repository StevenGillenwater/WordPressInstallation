# WordPress Installation Guide for Linux

### Install Docker
1. Type "sudo apt update"
2. Type "sudo apt install docker.io" to install the Docker package. \
&nbsp;&nbsp;&nbsp;&nbsp;*Note: to check the version/make sure that the package is properly installed, type 'docker -v'*

### Install Curl and Docker Compose
3. Type “sudo apt install curl” to install the Curl package.
4. To install the Compose package, type: \
“sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-	compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose”
5. To add execute privledges to all users, type: 
“sudo chmod +x /use/local/bin/docker-compose”

### Install WordPress
*Link used: https://docs.docker.com/samples/wordpress/* 

6. Create an empty project directory by typing “mkdir directory_name.”
7. Create the docker-compose.yml file with the touch command.
8. Add the block file to the docker-compose file by typing: \
\
`echo “version: "3.9"`\
\
`services:`\
&nbsp;&nbsp;&nbsp; `db:`\
&nbsp;&nbsp;&nbsp; `image: mysql:5.7`\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `volumes:` \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `- db_data:/var/lib/mysql`\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `restart: always`\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `environment: `\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `MYSQL_ROOT_PASSWORD: somewordpress`\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `MYSQL_DATABASE: wordpress`\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `MYSQL_USER: wordpress`\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `MYSQL_PASSWORD: wordpress`\
\
  `wordpress:`\
&nbsp;&nbsp;&nbsp; `depends_on:`\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `- db`\
&nbsp;&nbsp;&nbsp;`image: wordpress:latest`\
&nbsp;&nbsp;&nbsp;`volumes: `\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`- wordpress_data:/var/www/html`\
&nbsp;&nbsp;&nbsp;`ports: `\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`- "8000:80"`\
&nbsp;&nbsp;&nbsp;`restart: always`\
&nbsp;&nbsp;&nbsp;`environment:` \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`WORDPRESS_DB_HOST: db:3306`\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`WORDPRESS_DB_USER: wordpress`\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`WORDPRESS_DB_PASSWORD: wordpress`\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`WORDPRESS_DB_NAME: wordpress`\
`volumes:`\
&nbsp;&nbsp;&nbsp;`db_data: {}`\
&nbsp;&nbsp;&nbsp;`wordpress_data: {}” > docker-compose.yml`\
  \
  *Make sure that the version number is contained within quotation marks. 
9. Type “sudo docker-compose up -d” *while within the directory* to run the compose file.
10. Type “http://localhost:8000” into the browser to jump to the WordPress installation.
11. Type “docker-compose down” to stop the container. 

### Screenshot
![Screen Shot 2021-11-18 at 9 03 49 PM](https://user-images.githubusercontent.com/60118160/142562663-9bbc8a8d-8403-4677-ae6c-278c43f28807.jpeg)

  
  
  
  
  
  
  
  
  




