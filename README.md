# Spring Boot

## Spring Framework 

Spring framework is built and designed to provide comprehensive support when developing applications for the JVM. Including abstractions for some of the most powerful and common enterprise integrations, specifically around common infrastructure.  

* Framework for providing comprehensive infrastructural support for developing Java Applications.  
Spring essentially is designed to provide the plumbing for using these enterprise authoring in common components used in both internet and enterprise applications.  
These plumbings allows us to easily consume these authoring while focusing on the business logics.  

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

* Embedded application server (tomcat or other) support.  
Spring Boot with the Web package, brings in a pre-configured tomcat instance to the application.  
We can change the application server, but this is very different from traditional JVM-based applications, where we would build a **war** file and drop it into the application server.  
With Spring Boot, the application server exists within the spring boot jar file.  

* Auto-configuration of Application Context  
In traditional Spring development, much of our time is spent configuring the Application Context, often through copy-pasting.  
But with Spring Boot, much of the configuration is done for us in many cases within logical set of defaults and with the ability to add properties to modify those defaults as we need to.  

* Automatic Servlet Mappings  
This goes hand-in-hand with embedded application servers as well as way that the Application Context is auto configured.  
We get a default and effective servlet mapping without to having to write any XML or any Java configuration to the core servlet container of our applications.  

* Spring Boot provides database support and configuration for embedded and remote databases with Hibernate mappings as the default implementation of the JPA.  
With Spring Boot, a few key properties allow us to connect to remote databases or leverage embedded files with default schema and default data provided by SQL files embedded in our application.  
This embedded case is fantastic for POC type solutions or demos.  

* We also get Automatic Controller Mappings for MVC based applications. With raw Spring framework, we had to configure these mappings earlier in the framework's life-cycle, and it was rather tedious.  
New Spring Boot developers don't have to deal with any of that. With a few simple annotations handle everything for wiring web requests for appropriate classes and methods via the servlet contacts.  

### Auto Config 

Auto configuration refers to the Application Context or more specifically the Inversion of Control container, which is the Bean Factory.  

* Spring Boot provides a Default and opinionated configuration of common constructs.  
The opinionated defaults are very common, and often we don't need to change them. 

* But they are very easy to override. Usually through very simple properties of the environment.  

* Configuration on presence.  
One of the key aspects of auto-configuration is the ability to configure when a class, property or a component is present, and to bypass that configuration when it isn't.  
This configuration allows a simple set of defaults that only get added to the application context when the associated projects or JAR files are included.  

### IoC in Spring Boot 

* In Spring Boot, the IoC container maintains our class dependaencies, for the entire life-cycle of those dependaencies.  

* From the IoC container, objects can be injected as dependaencies into other classes at either start up time or at run time, depending on how the dependencies are defined in the class, and how the container manages them.  
Most commonly in Spring, dependaencies are injected at start up of the application as they are added to the Bean Factory.  

* One of the things in IoC, that is similar to dependency injection is that objects don't create dependant objects in their constructors or methods. Instead, the container manages them and injects them as needed.  

#### Traditional vs IoC Dependency Management 

Traditional:  
[]("/assets/1-traditional-dm.png")  

In this example, consider a Main class that contains the main() method. It will create two classes that it needs to do its work. Within the second class, in its constructor, it also creates a third class to do work. That class has two more classes that it needs to do work.  
So with that, we ends up creating five classes that all had to be managed at the creation from that main() method.  
If we think about configuring those classes as we create them, we now need to know things three levels deep, and how to properly create them and manage them for their life-cycle of our application. This would cause a lot of complication when it comes to a really large application.  

IoC:  
[]("/assets/2-ioc-dm.png")  

With IoC-based dependaency management, we start with an IoC Container. That IoC Container is usually triggered from the Main class.  
That IoC Container builds itself specific objects that are needed or referenced in Main, and then those classes again get their dependencies.  
But everything is comming from Main itself. Those become simply pointers in those classes, and the IoC Container is doing the injection of these specific classes, **into the parent class**.  
This is much easier to manage, cause now we don't need to know things three levels deep, they are simply configured in the way that we write our application to begin with, and then the IoC Container manages the life-cycle of those dependencies.  

#### Spring IoC 

* The Bean Factory is the IoC Container.  
We usually do not interact with the Bean Factory directly. But, if we ever find ourself in a situation where we have to impact the behaviour of the Bean Factory, we can utilize various hooks in the Spring Bean life-cycle, things like a Bean Factory post processor, or a Bean Processor.  

* The Application Context is what we interact with.  
Even if we don't do it ourself by writing code. Many times this isn't even needed because of the way that Spring Boot does its things. But the Application Context is a wrapper around the Bean Factory, and they share some common interfaces. And we can, any Spring Boot application, or any Spring application - interact with the Application Context if we needed to.  
We can even create Beans that are aware of the Application Context. 

* Bean Factory maintains References to the Spring Beans that either we configure, or Spring Boot auto configures for us.  
References are not added to the Bean Factory. They are configured, and Spring handles object initialization, as well as the instantiation of those objects.  

* Once Beans have been initialized, an order of operation for construction is created, based on the dependaencies. And then the Beans are instantiated in proper order by 