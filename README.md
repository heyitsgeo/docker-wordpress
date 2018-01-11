# Docker Wordpress
## Overview
This is a simple docker-compose project to spin up a WordPress environment. This workspace include access to WordPress:latest, mysql:5.7 and phpmyadmin:latest.

# Getting Started
Follow these instructions to get a working Wordpress development build on you machince. All of this was built on mac. Some additional configurations or prerequisites may be required for other systems.

### Credits
While I did use a lot of different resources for this including the Docker docs and the Docker image docs I do want to credit [Peter Suhm](https://gist.github.com/petersuhm). His blog "[The easiest way to use Docker for WordPress Development](https://wppusher.com/blog/the-easiest-way-to-use-docker-for-wordpress-development/)" helped a ton when I was having some issues with docker-compose.

### Prerequisites
1. Docker

### Clone into project
```bash
git clone https://github.com/heyitsgeo/docker-wordpress.git <project-folder>
```
### Bring containers up
```bash
cd <project-folder>
docker-compose up -d
```
Navigate to [http://localhost](http://localhost).

### Configuration

#### MySQL

##### Environment
- MYSQL_ROOT_PASSWORD: yourRootPassword
- MYSQL_DATABASE: yourDatabase
- MYSQL_USER: yourDatabaseUser
- MYSQL_PASSWORD: yourDatabaseUserPassword

##### Volumes
- db_data:/var/lib/mysql

##### Ports
Port that mysql runs on.
- "3306:3306"

#### WordPress

##### Environment
- WORDPRESS_DB_HOST: db:3306
- WORDPRESS_DB_PASSWORD: wordpress

#### Volumes
This gives you access to all plugins and themes from root.
- /wp-content:/var/www/html/wp-content/

#### Ports
Port that Wordpress container with run on and forward to. Using 80 so it can be accessed through [http://localhost](http://localhost).
- "80:80"

#### phpmyadmin

##### Environment
- PMA_HOST: db:3306
- PMA_PORT: 3306
- MYSQL_USERNAME: phpmyadimRootUSer
- MYSQL_ROOT_PASSWORD: yourRootPassword

##### Ports
Forwarding port 80 to 8080
- "8080:80"



