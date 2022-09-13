# Spring Boot, MySQL (via Docker), JPA, Hibernate Rest API Tutorial

Build Restful CRUD API for a simple Note-Taking application using Spring Boot, Mysql (via Docker), JPA and Hibernate.

## Requirements

1. Java - 1.8.x --> actually 18.0.2

2. Maven - 3.x.x --> actually 3.8.6

3. Mysql - 5.x.x -> actually 8.0.30

## Steps to Setup

**1. Clone the application**

```bash
git clone https://github.com/mcbarb/spring-boot-mysql-rest-api-tutorial.git
```

**2. Create Mysql database in Docker**
```bash
source aliases.sh
mysql_up
mysql_get_in
```

**3 Configure mysql and create testuser with testpassword**
```bash
# root and mypassword configured when running mysql via Docker
mysql -uroot -pmypassword

# now inside mysql shell
create database notes_app;
create user 'testuser'@'%' identified by 'testpassword';
grant all on notes_app.* to 'testuser'@'%';
```

+ Corresponding configuration in `src/main/resources/application.properties`

+ A Adminer UI interface to interact with MySQL will be available on `localhost:8081`

**4. Build and run the app using maven**

```bash
mvn package
java -jar target/easy-notes-1.0.0.jar
```

Alternatively, you can run the app without packaging it using -

```bash
mvn spring-boot:run
```

The app will start running at <http://localhost:8080>.

## Explore Rest APIs

The app defines following CRUD APIs.

    GET /api/notes
    
    POST /api/notes
    
    GET /api/notes/{noteId}
    
    PUT /api/notes/{noteId}
    
    DELETE /api/notes/{noteId}

You can test them using postman or any other rest client.

Note that each note shall receive a body with title and content as a JSON.
## Learn more

You can find the tutorial for this application on my blog -

<https://www.callicoder.com/spring-boot-rest-api-tutorial-with-mysql-jpa-hibernate/>
