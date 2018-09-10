# quickstart-rest-web-service
# Spring Overview 
Spring makes it easy to create Java enterprise applications with the flexibility to create many kinds of architectures depending on an application’s needs. As of Spring Framework 5.0, Spring requires JDK 8+ (Java SE 8+) and provides out-of-the-box support for JDK 9 already.

Spring supports a wide range of application scenarios, for example:

-	In a large enterprise, applications often exist for a long time and have to run on a JDK and application server whose upgrade cycle is beyond developer control. 
-	Others may run as a single jar with the server embedded, possibly in a cloud environment. 
- Yet others may be standalone applications (such as batch or integration workloads) that do not need a server.

Several initiatives (aka projects) have sprung since its original inception. These notes focus on the foundation, that is the **Spring Framework** which is divided into modules. Applications can choose which modules they need. At the heart are the modules of the core container, including a configuration model and a dependency injection mechanism. Beyond that, the Spring Framework provides foundational support for different application architectures, including messaging, transactional data and persistence, and web. It also includes the Servlet-based Spring MVC web framework and, in parallel, the Spring WebFlux reactive web framework.
![Spring Framework Runtime](/Users/Michael/ADevelopment/Programming/Udemy/Spring/images/spring_framework_runtime.png)


For more information, see [Spring Framework Overview](https://docs.spring.io/spring/docs/current/spring-framework-reference/overview.html#overview-spring). 

## Design Principles
The following are the guiding principles of the Spring Framework:

1.	**Provide choice at every level**. **Spring lets you defer design decisions as late as possible**. For example, you can switch persistence providers through configuration without changing your code. The same is true for many other infrastructure concerns and integration with third-party APIs.
2. **Accommodate diverse perspectives**. **Spring embraces flexibility **and is not opinionated about how things should be done. It supports a wide range of application needs with different perspectives.
3. **Maintain strong backward compatibility**. Spring’s evolution has been carefully managed to force few breaking changes between versions. Spring supports a carefully chosen range of JDK versions and third-party libraries to facilitate maintenance of applications and libraries that depend on Spring.
4. **Care about API design**. The Spring team puts a lot of thought and time into making **APIs that are intuitive and that hold up across many versions and many years**.
5. **Set high standards for code quality**. The **Spring Framework puts a strong emphasis on meaningful, current, and accurate Javadoc**. It is one of very few projects that can claim clean code structure with no circular dependencies between packages.


## Prerequisites

-  It is reccomended to use a tried and true **good IDE** environment. We suggest the following:
	- [Eclipse](http://wwww.eclipse.org/). Install the Spring IDE plugin as shown at [Spring Tools for Eclipse](https://www.eclipse.org/community/eclipse_newsletter/2018/february/springboot.php). 
	![Install Spring IDE plugin](/Users/Michael/ADevelopment/Programming/Udemy/Spring/images/spring_ide_plugin.png)
- **Other**
	- aaa. 
	- bbb.  



# Getting Started
If you are just getting started with Spring, you may want to begin using the Spring Framework by creating a Spring Boot-based application. Spring Boot provides a quick (and opinionated) way to create a production-ready Spring-based application. It is based on the Spring Framework, favors convention over configuration, and is designed to get you up and running as quickly as possible.

You can do one of the following:

-	Generate a basic project using [start.spring.io](https://start.spring.io/).   
- 	Follow one of the [Getting Started](https://spring.io/guides) guides, such as [Getting Started Building a RESTful Web Service](https://spring.io/guides/gs/rest-service/). As well as being easier to digest, these guides are very task focused, and most of them are based on Spring Boot. They also cover other projects from the Spring portfolio that you might want to consider when solving a particular problem.


## Projects
The following collection of projects demonstrates how to use and apply Spring Framework in actual projects. We are going to use Eclispe IDE with Spring Framework plugin installed. 

### RESTful Web Service
This project shows how to create a [RESTful Web Service](https://spring.io/understanding/REST). You can download the exanmples source code at [sprinf-guides/gs-rest-service](https://github.com/spring-guides/gs-rest-service).  

#### Overview
The Web service accepts **GET requests** at:

	http://localhost:8080/greeting

It responds with a **JSON representation** of a greeting:

	{"id":1,"content":"Hello, World!"}

You can customize the greeting with an optional name parameter in the query string:

	http://localhost:8080/greeting?name=UserName

The name parameter value overrides the default value of "World" and is reflected in the response:

	{"id":1,"content":"Hello, UserName!"}

#### Prerequisites
1. Eclipse IDE.
2. Assure that [JDK 1.8](http://www.oracle.com/technetwork/java/javase/downloads/index.html) or later is installed.
3. [Maven 3.2](https://maven.apache.org/download.cgi).   

#### Steps
1. Actiivate Eclipse IDE.
2. From the menu bar select **File->New->Other-Maven** Project.
3. In the pom UI enter information similar to the following:
![Initial pom.xml](/Users/Michael/ADevelopment/Programming/Udemy/Spring/images/rest_web_service_pom.png)
2. To the initial add the information shown next:

		<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
		xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 	http://maven.apache.org/xsd/maven-4.0.0.xsd">
		<modelVersion>4.0.0</modelVersion>
		
		<groupId>com.acloudysky.springframework</groupId>
		<artifactId>quickstart-rest-web-service</artifactId>
		<version>0.0.1-SNAPSHOT</version>
		<packaging>jar</packaging>
		<name>quickstart-rest-web-service</name>
		<url>http://localhost:8080/greeting</url>
		
		<parent>
		  <groupId>org.springframework.boot</groupId>
		  <artifactId>spring-boot-starter-parent</artifactId>
		  <version>2.0.3.RELEASE</version>
		</parent>

	    <dependencies>
	        <dependency>
	            <groupId>org.springframework.boot</groupId>
	            <artifactId>spring-boot-starter-web</artifactId>
	        </dependency>
	        <dependency>
	            <groupId>org.springframework.boot</groupId>
	            <artifactId>spring-boot-starter-test</artifactId>
	            <scope>test</scope>
	        </dependency>
	        <dependency>
	            <groupId>com.jayway.jsonpath</groupId>
	            <artifactId>json-path</artifactId>
	            <scope>test</scope>
	        </dependency>
	    </dependencies>
    
		  	<properties>
		    	<project.build.sourceEncoding>UTF-8
		    	</project.build.sourceEncoding>
		  	</properties>

			<build>
		        <plugins>
		            <plugin>
		                <groupId>org.springframework.boot</groupId>
		                <artifactId>spring-boot-maven-plugin</artifactId>
		            </plugin>
		        </plugins>
		    </build>
		
		    <repositories>
		        <repository>
		            <id>spring-releases</id>
		            <url>https://repo.spring.io/libs-release</url>
		        </repository>
		    </repositories>
		    <pluginRepositories>
		        <pluginRepository>
		            <id>spring-releases</id>
		            <url>https://repo.spring.io/libs-release</url>
		        </pluginRepository>
		    </pluginRepositories>
  
		</project>
	After the project setup; let's now build the actual web service.	
3. **Resource Representation Class**. Let's remember that the service must handle a **GET** request for */greetings*, with an optional *name* parameter in the query string. The request must return a **200 OK** response in *JSON* format in the body, which represents a greeting. The response should look like this:

		{
			"id": 1,
			"content": "Hello, World!" 
		}  
Where:
	- **id** is a unique identifier for the greeting.
	- **content** is the greetign textual representation.

	To **model the greeting representation**, you must **create a resource representation class**. Provide a plain old java object with fields, constructors, and accessors for the id and content data as shown next:
	
		package com.acloudysky.springframework.quickstart_rest_web_service;
		
		public class Greeting {

		    private final long id;
		    private final String content;
		
		    public Greeting(long id, String content) {
		        this.id = id;
		        this.content = content;
		    }
		
		    public long getId() {
		        return id;
		    }
		
		    public String getContent() {
		        return content;
		    }
		}
<div style="background-color:yellow">As you see in steps below, Spring uses the Jackson JSON library to automatically marshal instances of type Greeting into JSON.</div>
4. **Resource Controller Class**.  In Spring’s when building RESTful web services, HTTP requests are handled by a controller. These components are easily identified by the **@RestController** annotation. You can see this in the **GreetingController** class below which handles GET requests for 
*/greeting* by returning a new instance of the **Greeting** resource class.

		package com.acloudysky.springframework.quickstart_rest_web_service;

		import java.util.concurrent.atomic.AtomicLong;
		import org.springframework.web.bind.annotation.RequestMapping;
		import org.springframework.web.bind.annotation.RequestParam;
		import org.springframework.web.bind.annotation.RestController;
		
		@RestController
		public class GreetingController {

		   	private static final String template = "Hello, %s!";
		   	private final AtomicLong counter = new AtomicLong();
		
		    @RequestMapping("/greeting")
		    public Greeting greeting(@RequestParam(value="name", defaultValue="World") String name) {
		        return new Greeting(counter.incrementAndGet(),
		                            String.format(template, name));
		    }
		}
Let's analyze the GreetingController class which is deceptively simple but it implements very important Spring's concepts.


-	The class uses Spring 4’s new **@RestController** annotation, which marks the class as a controller allowing every method to <span style="background-color:yellow">return a domain object</span> instead of a view. It’s shorthand for @Controller and @ResponseBody rolled together. In this example, it returns a resource representation class Greeting obiect. 
<div style="background-color:#c2e7e7"> ![bullhorn](/Users/Michael/ADevelopment/Programming/Udemy/Spring/images/bullhorn.png) A key difference between a traditional MVC controller and the RESTful web service controller above is the way that the HTTP response body is created. Rather than relying on a view technology to perform server-side rendering of the greeting data to HTML, this RESTful web service controller simply populates and returns a Greeting object. The object data will be written directly to the HTTP response as JSON. The Greeting object is converted to JSON thanks to Spring’s HTTP message converter support; you don’t need to do this conversion manually. Because Jackson 2 is on the classpath, Spring’s MappingJackson2HttpMessageConverter is automatically chosen to convert the Greeting instance to JSON.</div>

- 	The **@RequestMapping** annotation <span style="background-color:yellow">ensures that HTTP requests to /greeting are mapped to the greeting() method</span>. <div style="background-color:#c2e7e7"> ![bullhorn](/Users/Michael/ADevelopment/Programming/Udemy/Spring/images/bullhorn.png) The above example does not specify GET vs. PUT, POST, and so forth, because @RequestMapping maps all HTTP operations by default. If you want to narrow the mapping to GET only, use @RequestMapping(method=GET) instead.</div>
-  The **@RequestParam** annotation binds the value of the query string parameter *name* into the name parameter of the greeting() method. If the *name* parameter is absent in the request, the defaultValue of "World" is used.
-  Finally, the implementation of the method body creates and returns a new Greeting object with id and content attributes based on the next value from the counter, and formats the given name by using the greeting template.

## Glossary

- **Fluid Grid**. The fluid grid system uses percents instead of pixels for column widths. It has the same responsive capabilities as our fixed grid system, ensuring proper proportions for key screen resolutions and devices.- sada
- **Parallax**. Parallax scrolling is a web site trend where the background content (i.e. an image) is moved at a different speed than the foreground content while scrolling. For more info, see [How TO - Parallax Scrolling](https://www.w3schools.com/howto/howto_css_parallax.asp). 
- **Font Awesome**. [Font Awesome](https://fontawesome.com/) is the web's mostg popular icon set and toolkit. 



##References

- [Spring Framework Overview](https://docs.spring.io/spring/docs/current/spring-framework-reference/overview.html#overview-spring)
- [Spring Site by Pivotal](http://spring.io)
- [REST in a Nutshell](https://spring.io/understanding/REST)




