# Prerequisites

- JDK 17 or 21
- Maven 3.9
- MySQL 8

# Technologies 
- Spring MVC
- Spring Security
- Spring Data JPA
- Maven
- JSP
- Tomcat
- MySQL
- Memcached
- Rabbitmq
- ElasticSearch
# Database
Here,we used Mysql DB 
sql dump file:
- /src/main/resources/db_backup.sql
- db_backup.sql file is a mysql dump file.we have to import this dump to mysql db server
- > mysql -u <user_name> -p accounts < db_backup.sql

# CI/CD
Staging pipeline: stagePipeline/Jenkinsfile
- Build, test and checkstyle with Maven
- SonarQube analysis and quality gate
- Upload the war artifact to Nexus
- Build the app Docker image and push it to Amazon ECR
- Deploy the image to the ECS staging cluster (vproappstaging)

Production pipeline: ProdPipeline/Jenkinsfile
- Deploy the latest image from Amazon ECR to the ECS production cluster (vproapp-prod)

Both pipelines are triggered automatically by a GitHub webhook on every push

