Java SpringBoot and MariaDB on Android Mobile or Tablet

In this project, I successfully set up a full Spring Boot development environment directly on an Android device. Using tools like Smart IDE All in One and AWebServer, I was able to:
✅ Create and run Spring Boot projects
✅ Automatically install and configure OpenJDK and Maven
✅ Set up a local MariaDB server with phpMyAdmin
✅ Connect Spring Boot to the local database and test it all on mobile
This project shows how Android devices can be turned into lightweight development environments, perfect for learning, prototyping, or coding on the go!

1-Step One (install applications)

	1-1- Install Smart IDE all IN one
	Create a Spring Boot project easily
	Automatic installation of Maven and OpenJDK
	development environment
download Link : https://play.google.com/store/apps/details?id=org.smartide.code

	1-2- Install AWebServer Http Apache PHP Sql
	Easy installation of MariaDB with the phpMyAdmin management panel
download Link : https://play.google.com/store/apps/details?id=com.sylkat.apache&hl=en_GB



2-Step Two (add dependency and config)

	2-1- Run MariaDB Server

 ![photo_2025-05-04_20-26-27](https://github.com/user-attachments/assets/8f915cfd-2c0d-47c3-9f16-58e28cb644cb)


	2-2- Create Spring Boot project
	Add dependency (JPA, MariaDB Driver)
	Config application.properties
	Create Entity

![1](https://github.com/user-attachments/assets/21f99217-52bd-4616-815e-1554e508185d)

 
•	When you create a Spring Boot project for the first time, a button to install OpenJDK and Maven will appear. Just make sure your internet is connected and tap the button. The rest of the setup will be done automatically. After the installation is complete, you can go ahead and create your project.

	2-3 Add dependency (JPA, MariaDB Driver) and Config application.properties and Create Entity

File Name: Pom.xml
```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
 <modelVersion>4.0.0</modelVersion>
 <parent>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-parent</artifactId>
  <version>3.4.0</version>
  <relativePath/>
 </parent>

 <groupId>com.example</groupId>
 <artifactId>demo</artifactId>
 <version>0.0.1-SNAPSHOT</version>
 <name>demo</name>
 <description>Demo project for Spring Boot with JPA and MySQL</description>

 <properties>
  <java.version>21</java.version>
 </properties>

 <dependencies>
  <!-- Spring Boot Starter for Web -->
  <dependency>
   <groupId>org.springframework.boot</groupId>
   <artifactId>spring-boot-starter-web</artifactId>
  </dependency>

  <!-- Spring Boot Starter for JPA -->
  <dependency>
   <groupId>org.springframework.boot</groupId>
   <artifactId>spring-boot-starter-data-jpa</artifactId>
  </dependency>
  <dependency>
   <groupId>com.mysql</groupId>
   <artifactId>mysql-connector-j</artifactId>
   <version>8.0.33</version>
  </dependency>
  <dependency>
   <groupId>org.projectlombok</groupId>
   <artifactId>lombok</artifactId>
   <scope>provided</scope>
  </dependency>
  <dependency>
   <groupId>org.springframework.boot</groupId>
   <artifactId>spring-boot-starter-test</artifactId>
   <scope>test</scope>
  </dependency>
 </dependencies>

 <build>
  <plugins>
   <plugin>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-maven-plugin</artifactId>
   </plugin>
   <plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-compiler-plugin</artifactId>
    <version>3.8.1</version>
    <configuration>
     <source>21</source>
     <target>21</target>
     <annotationProcessorPaths>
      <path>
       <groupId>org.projectlombok</groupId>
       <artifactId>lombok</artifactId>
       <version>1.18.30</version>
      </path>
     </annotationProcessorPaths>
    </configuration>
   </plugin>
  </plugins>
 </build>
</project>
```

File Name: APPLICATION.PROPERTIES
```
spring.application.name=demo
spring.datasource.url=jdbc:mysql://IP_OF_MARI DB:PORT/Your_Data_Bace?createDatabaseIfNotExist=true
spring.datasource.username=root
spring.datasource.password=root
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.database-platform=org.hibernate.dialect.MySQL8Dialec
```
File Name : User.java
```
import jakarta.persistence.*;
@Entity
@Table(name = "users")
public class User 
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String username;
    private String email;
    // Getters & Setters
}
```
Final Run Project and enjoy 😉
