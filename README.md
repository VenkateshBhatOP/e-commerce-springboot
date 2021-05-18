# ECommerce

## Description

This project is about a simple Ecommerce website created using SpringBoot as a middleware.There are two roles given, one for Admin who can add, modfily and delete the products and the other is User who after login can add a comment or buy products and can also add the produts to the cart.

## Tools to be used

1. Use any IDE to develop the Spring and Hibernate project. It may be STS/Eclipse/Netbeans. Here, I am using IntelliJ idea.
2. Mssql for the database.
3. Server: Apache Tomcat/JBoss/Glassfish/Weblogic/Websphere.

> ## Spring MVC

Spring MVC is the primary web framework built on the Servlet API. It is build on the popular MVC design pattern. MVC (Model-View-Controller) is a software architecture pattern, which separates application into three areas: model, view, and controller. The model represents a Java object carrying data. The view represents the visualization of the data that the model contains. The controller controls the data flow into model object and updates the view when the data changes. It separates the view and model.

 ## Spring Boot Architecture

![Screenshot (329)](https://user-images.githubusercontent.com/74126223/118713188-467d4f80-b83f-11eb-9591-f5a54d05463e.png)

Spring Boot is a module of the Spring Framework. It is used to create stand-alone, production-grade Spring Based Applications with minimum efforts. It is developed on top of the core Spring Framework.

> ## About MsSQL

___MsSQL___ is a database management system that allows you to manage relational databases. It is open source software backed by Microsoft. It means you can use ___MsSQL___ without paying a dime. Also, if you want, you can change its source code to suit your needs.


> ## Introduction to the POM

___POM___ A Project Object Model or POM is the fundamental unit of work in Maven. It is an XML file that contains information about the project and configuration details used by Maven to build the project. It contains default values for most projects. Examples for this is the build directory, which is ___target___; the source directory, which is src/main/java; the test source directory, which is ___src/main/java___; and so on. When executing a task or goal, Maven looks for the POM in the current directory. It reads the POM, gets the needed configuration information, then executes the goal.

```bash
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>2.4.2</version>
		<relativePath /> <!-- lookup parent from repository -->
	</parent>
	<groupId>com.restuarent</groupId>
	<artifactId>ecommerce</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<name>ecommerce</name>
	<description>Demo project for Spring Boot</description>

	<properties>
		<java.version>1.8</java.version>
	</properties>

	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-jpa</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>

		<dependency>
			<groupId>javax.validation</groupId>
			<artifactId>validation-api</artifactId>
			<version>2.0.1.Final</version>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-devtools</artifactId>
			<scope>runtime</scope>
			<optional>true</optional>
		</dependency>
		<dependency>
			<groupId>com.microsoft.sqlserver</groupId>
			<artifactId>mssql-jdbc</artifactId>
			<scope>runtime</scope>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>
		<dependency>
			<groupId>org.springframework.security</groupId>
			<artifactId>spring-security-test</artifactId>
			<scope>test</scope>
		</dependency>
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>

</project>

```

> ## Properties file

``` bash
spring.datasource.url = jdbc:sqlserver://localhost;databaseName=Ecommerce
spring.jpa.hibernate.ddl-auto=update
spring.datasource.username = sa
spring.datasource.password =niit@123
spring.jpa.properties.hibernate.dialect = org.hibernate.dialect.SQLServerDialect
server.port=8080
spring.datasource.driver-class-name = com.microsoft.sqlserver.jdbc.SQLServerDriver

```

## Class Diagram

![class diagram](https://user-images.githubusercontent.com/74126223/118715590-6ca3ef00-b841-11eb-8a49-ec619902ce9a.png)


> ## Modals / Entities

An entity is a lightweight persistence domain object. Typically, an entity represents a table in a relational database, and each entity instance corresponds to a row in that table. The primary programming artifact of an entity is the entity class, although entities can use helper classes.

> #### We need to create these entities

1. `Cart `:Cart.java This object content id, name, price, quantity, pictureUrl and relational @ManyToOne with User

1. ` Category` :Category.java This object content id, name, and relational @ManyToOne with User and @OneToMany with Product

1. `Comment `:Comment.java This object content id, title, message, addedBy, addedAt and relational @ManyToOne with Product

1. `Order` :Order.java This object content id, dateCreated, status, and relational @ManyToOne with orderProducts

1. ` OrderProduct `:OrderProduct.java This object content quantity @EmbeddedId in OrderProductPK

1. `OrderProductPk` :OrderProductPK.java This object content relational @ManyToOne with Order and Product 

1. `Product `:Product.java This object content id, name, price, description, pictureUrl and relational @ManyToOne with Category @ManyToMany with Tag @OneToMany with Comment

1. ` Tag `:Tag.java This object content id, name and relational @ManyToOne with Product and @ManyToMany with Product

1. `User `:User.java This object content id, username, password, admin, email, nameOnCard, cardNumber, cvv, address and relational @ManyToOne with Category and Cart


> ## @RestController API

___@RestController___ is a convenience annotation for creating Restful controllers. It is a specialization of @Component and is autodetected through classpath scanning. It adds the @Controller and @ResponseBody annotations. It converts the response to JSON or XML. It does not work with the view technology, so the methods cannot return ModelAndView. It is typically used in combination with annotated handler methods based on the @RequestMapping annotation.


> #### We will create these classes in controller package:

1. CartController
2. CategoryController

3.  CommentController

4.  OrderController

5.  ProductController

6.  TagController

7.  UserController

In The Controller We'll inject this bean into the controller bean using ___@Autowired___ on the field definition: We need to add map requests with request mapping annotations e.g. ___@RequestMapping, @GetMapping and @PostMapping___

> ## EcommerceApplication

___@BookStoreApplication___ and its use in a simple Spring Boot application. We use the ___@SpringBootApplication___ annotation in our Application or Main class to enable a host of features, e.g. Java-based Spring configuration, component scanning, and in particular for enabling Spring.

```bash
package com.ecommerce;
import org.springframework.boot.autoconfigure.SpringBootApplication;


@SpringBootApplication
public class EcommerceApplication {

 public static void main(String[] args) {
   SpringApplication.run(EcommerceApplication.class, args);		
   System.out.println("App started....");
  }
  
}
```

## Conclusion

We also take a look at client-server architecture for REST API using Spring Web MVC & Spring Data JPA, as well, we are going to continue with Angular 10 project structure for building a front-end app to make HTTP requests and consume responses.


