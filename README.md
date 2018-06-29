Spring Boot RESTful Webservice Example
======================================
The main purpose of this sample project is to demonstrate the capabilities of spring boot.
But additionally, I want to show challenging problems that can occur during the development
while using the Spring Boot. 

First goal is to show how it is easy to start a web service with embedded tomcat and embedded
H2 database. This is the main goal of the project.

Secondly, we are using Spring and I have used dependency injection. But what is a challenging
problem about dependency injection. Assume that you have two implementations ready for one
implementation, how are you going to select the implementation? I'll explain several ways but
also I'll demonstrate how we can select our implementation via external configuration so that
we can update our configuration and don't need to touch the code, restart our jar file and
that's all.

Thirdly, I also have demonstrated how to use Java Application Configuration within the double
implementation for the single interface scenario I've explained above.

Lastly, I will explain all the deployment details, the main configuration of the whole project
including H2 database configuration.

Moreover, I will also demonstarte how you are going to test your RESTful application with
Postman tool.

TOC
---
- [0 Prerequisite](#0-prerequisite) <br/>
- [1 About Spring Boot](#1-about-spring-boot) <br/>
- [2 Spring Boot Setup](#2-spring-boot-setup) <br/>
- [3 Using Config Manager](#3-using-config-manager) <br/>
- [4 Logging](#4-logging) <br/>
- [5 Testing And Incoming Outgoing JSON Samples](#5-testing-and-incoming-outgoing-json-samples) <br/>
  * [5-a- Test Web Service](#5-a-test-web-service) <br/>
  * [5-b- Retrieve All Customer Collection](#5-b-retrieve-all-customer-collection) <br/>
  * [5-c- Retrieve Customer](#5-c-retrieve-customer) <br/>
  * [5-d- Create Customer](#5-d-create-customer) <br/>
  * [5-e- Update Customer](#5-e-update-customer) <br/>
  * [5-f- Delete Customer](#5-f-delete-customer) <br/>
  
 0 Prerequisite
---------------
To use this project, you are going to need;

- Java JDK 8 (1.8)
- Maven compatibile with JDK 8
- Any Java IDE

 1 About Spring Boot
--------------------
Whenever there is a new framework on the town, you must think two thinks. One, why should I use this
framework which means "what are the benefits of this framework", also can be interpreted like "what
this framework solves?". Two, "When should I use this framework?", also can be interpreted as "on
which specific scenarios this framework is useful" or can be simplified as "what is the problem domain
of this framework?".

When we make a web service with spring framework, we have to generate a war file, we need to configure
web.xml, and also if we are going to use the connection pool, the configuration is costly. All of these
increases the cost of time. So instead of writing your code, doing your development, you a lot of time
is wasted during the configuration. This is where Spring Boot comes to the action. Spring Boot simplifies
configuration, reduces boilerplate code that puts no any value to your software development.

So, what Spring Boot solves is the time lost for the configuration. For example, you can create a web
service with Spring Boot that runs on an embedded Tomcat server which is automatically configured and
you don't have to deal with the configuration. You can do all your configuration parameters via default
application properties. Also you can connect to an H2 embedded database, same applies for the
configuration here. 

Secondly, you don't have to generate a war file. All Spring Boot applications run as a standalone java
jar file. Where is it useful then? If you are using a microservice architecture which runs especially
on a cloud (but not necessarily), then you can easily do your development via Spring Boot. In my opinion,
Spring Boot is one of the best frameworks you should use on such a scenario and architecture. You can
easily create simple web services, put them inside a Docker container (which is not a part of this
tutorial) and run them on the Amazon Web Services or on any cloud environment.

 2 Spring Boot Setup
--------------------
What we need to setup a Spring Boot project. However there are other ways (like spring initializer),
I'll go with setting up our project with maven.

Because that we are creating a web application here, we will first create a maven project with web
application archetype, then we will add the spring boot dependencies;

You can use the following maven command to create a project. In this project, I've used this exact
maven command to create our project;

```mvn archetype:generate -DgroupId=com.levent.consultantapi -DartifactId=consultant-api  -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false```


