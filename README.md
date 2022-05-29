# Spring Boot

## Spring Framework 

Spring framework is built and designed to provide comprehensive support when developing applications for the JVM. Including abstractions for some of the most powerful and common enterprice integrations, specifically around common infastructure.  

* Framework for providing comprehensive infastructural support for developing Java Applications.  
Spring essentially is designed to provide the plumbing for using these enterprice authoring in common components used in both internet and enterprice applications.  
This plumbings allows us to easily consume these authorings while focusing on the business logics.  

* Object-Oriented Programming best practices built in  
Spring is built on solid Object-Oriented programming concepts, and its style promotes the users to do the same thing when consuming the framework.  

* DRY Principles - Don't Repeat Yourself  
Spring promotes DRY Principle. By leveraging the powerful abstractions of the framework, instead of rebuilding the scaffolding, we can focus on the actual needs of our application.   


### Definitions of Common Terms 

* POJO - Plain Old Java Objects  
In Spring, this is any class that contains both attributes and methods. And those methods are not just getters and setters.  

* Java Beans - These are also essentially POJOs. But they only contain accessor methods, such as getters and setters.  

* Spring Beans - These are POJOs configured in the application context.  
Anything that Spring manages during the life-cycle of the application is considered **application context**.  

* DTO - Data Transfer Objects  
These are Java Beans with the specific purpose of moving state between logical layers of the application. There are times when we don't want to expose the details of our classes. And instead, translate to a DTO which often is written as an immutable object before sending the state data out to the logical layer.  

### Inversion of Control **IoC**

IoC provides mechanism of dependency injection. But there is more to that. With Spring's use of IoC, all operations of the life-cycle of those dependencies are controlled - not just the injection.  

The Application Context wraps the Bean Factory (which is the IoC Container itself), which serves the Beans at the runtime of the application.  
We as users and developers, never really interact with the IoC Container itself, instead we interact with its wrapper - the Application Context.  
There are several implementations of the Application Context.  

One of the most powerful aspects of Spring Boot is, it provides auto-configuration of the Application Context. So, we as developers can leverage simple properties and conventions to configure the Beans that loaded into the bean factory and used by the IoC container.  

## Spring Boot 

Spring Boot, at its core - is all rapid application development. But it starts at the initial setup phase of the application as well as common configuration.  
With its structure, Spring Boot removes much of the boilerplate actions that are associated with just the application creation and initial setup.  
It also has many uses. The use cases are unlimited. If the application needs to run on the JVM, Spring Boot will most likely save our time.  
Spring Boot was designed with a Cloud-Native role in mind. And many of the constructs are for Cloud-Native applications. But there are no reasons traditional - enterprise - monolithic applications cannot leverage effectively with spring boot, and leverage many of its benefits.  

### Key Aspects of Spring Boot

* Embeded application server (tomcat or other) support.  
Spring Boot with the Web package, brings in a pre-configured tomcat instance to the application.  
We can change the application server, but this is very differnt from traditional JVM-based applications, where we would build a **war** file and drop it into the application server.  
With Spring Boot, the application server exists within the spring boot jar file.  

* Auto-configuration of Application Context  
In traditional Spring development, much of our time is spent configuring the Application Context, often through copy-pasting.  
But with Spring Boot, much of the configuration is done for us in many cases within logical set of defaults and with the ability to add properties to modify those defaults as we need to.  

* Automatic Servlet Mappings  
This goes hand-in-hand with embeded application servers as well as way that the Application Context is auto configured.  
We get a default and effective servlet mapping without to having to write any XML or any Java configuration to the core servlet container of our applications.  

* Spring Boot provides database support and configuration for embeded and remote databases with Hibernate mappings as the default implementation of the JPA.  
With Spring Boot, a few key properties allow us to connect to remote databases or leverage embeded files with default schema and default data provided by SQL files embeded in our application.  
This embeded case is fantastic for POC type solutions or demos.  

* We also get Automatic Controller Mappings for MVC based applications. With raw Spring framework, we had to configure these mappings earlier in the framework's life-cycle, and it was rather tedious.  
New Spring Boot developers don't have to deal with any of that. With a few simple annotations handle everything for wiring web requests for appropriate classes and methods via the servlet contacts.  

### Auto Config 

Auto configuration refers to the Application Context or more specifically the Inversion of Control container, which is the Bean Factory.  

* Spring Boot provides a Default and opinionated configuration of common constructs.  
The opinionated defaults are very common and often we don't need to change them. 

* But they are very easy to override.  