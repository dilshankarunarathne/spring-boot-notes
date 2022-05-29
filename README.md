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

The Application Context wraps the Bean Factory, which serves 