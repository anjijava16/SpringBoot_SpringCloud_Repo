# SpringBoot_SpringCloud_Repo


# 0. Spring DEV tools info

	<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-devtools</artifactId>
			<scope>runtime</scope>
		</dependency>
	
	

	{
	
	"_links": {
		"self": {
			"href": "http://localhost:8888/actuator",
			"templated": false
		},
		"auditevents": {
			"href": "http://localhost:8888/actuator/auditevents",
			"templated": false
		},
		"beans": {
			"href": "http://localhost:8888/actuator/beans",
			"templated": false
		},
		"health": {
			"href": "http://localhost:8888/actuator/health",
			"templated": false
		},
		"conditions": {
			"href": "http://localhost:8888/actuator/conditions",
			"templated": false
		},
		"configprops": {
			"href": "http://localhost:8888/actuator/configprops",
			"templated": false
		},
		"env": {
			"href": "http://localhost:8888/actuator/env",
			"templated": false
		},
		"env-toMatch": {
			"href": "http://localhost:8888/actuator/env/{toMatch}",
			"templated": true
		},
		"info": {
			"href": "http://localhost:8888/actuator/info",
			"templated": false
		},
		"loggers": {
			"href": "http://localhost:8888/actuator/loggers",
			"templated": false
		},
		"loggers-name": {
			"href": "http://localhost:8888/actuator/loggers/{name}",
			"templated": true
		},
		"heapdump": {
			"href": "http://localhost:8888/actuator/heapdump",
			"templated": false
		},
		"threaddump": {
			"href": "http://localhost:8888/actuator/threaddump",
			"templated": false
		},
		"metrics-requiredMetricName": {
			"href": "http://localhost:8888/actuator/metrics/{requiredMetricName}",
			"templated": true
		},
		"metrics": {
			"href": "http://localhost:8888/actuator/metrics",
			"templated": false
		},
		"scheduledtasks": {
			"href": "http://localhost:8888/actuator/scheduledtasks",
			"templated": false
		},
		"httptrace": {
			"href": "http://localhost:8888/actuator/httptrace",
			"templated": false
		},
		"mappings": {
			"href": "http://localhost:8888/actuator/mappings",
			"templated": false
		},
		"refresh": {
			"href": "http://localhost:8888/actuator/refresh",
			"templated": false
		},
		"features": {
			"href": "http://localhost:8888/actuator/features",
			"templated": false
			}
		}
	}



# Case 1: Implementing Eureka Server

https://github.com/anjijava16/SpringBoot_SpringCloud_Repo/blob/master/Eureka_hystrix_SpringBOOT.zip

Eureka Server is service discovery for your microservices, 
where all client applications can register by themselves and other microservices look up the Eureka Server to get independent microservices to get the job complete.
Eureka Server is also known as Discovery Server 
and it contains all the information about client microservices running on which IP address and port.
By Default Port: 8761
pom.xml

	<dependency>
	<groupId>org.springframework.cloud</groupId>
	<artifactId>spring-cloud-starter-netflix-eureka-server</artifactId>
	</dependency>  
	
@SpringBootApplication
@EnableEurekaServer
public class EurekaServerApplication {
main()
}	
# Case 2: Registering Client Application With Eureka Server
application.properties:
spring.application.name=eureka-client-service
server.port=8081
eureka.client.service-url.defaultZone=http://localhost:8761/eureka/

https://github.com/anjijava16/SpringBoot_SpringCloud_Repo/blob/master/Eureka_hystrix_SpringBOOT.zip

MainApplication:

	import org.springframework.boot.SpringApplication;
	import org.springframework.boot.autoconfigure.SpringBootApplication;
	import org.springframework.cloud.client.discovery.EnableDiscoveryClient;
	@SpringBootApplication
	@EnableDiscoveryClient
	public class EurekaClientApplication{
	public static void main(String[] args) {
	main()
	}
# Case 3: Implementing Zipkin Server For Distributed Tracing(Zipkin Server for Distributed Tracing)
Distributed Tracing is crucial for troubleshooting and understanding microservices. It is very useful when we need to track the request passing through multiple microservices.
Distributed Tracing can be used to measure the performance of the microservices. 
It is easy to identify which microservice is failed or having performance issues whenever there are multiple service calls within a single request.	

pom.xml:

		<dependency>
			<groupId>io.zipkin.java</groupId>
			<artifactId>zipkin-server</artifactId>
			<version>2.11.7</version>
		</dependency>
		<dependency>
			<groupId>io.zipkin.java</groupId>
			<artifactId>zipkin-autoconfigure-ui</artifactId>
			<version>2.11.7</version>
		</dependency>

application.properties:

	spring.application.name=zipkin-server
	server.port=9411

MainApplication.java

	import org.springframework.boot.SpringApplication;
	import org.springframework.boot.autoconfigure.SpringBootApplication;
	import zipkin.server.EnableZipkinServer;
	@SpringBootApplication
	@EnableZipkinServer
	public class ZipkinServerApplication {
	public static void main(String[] args) {
	main()
	}

# Case 4:Registering Client Application With Zipkin Server

Registering Eureka Server With Zipkin Server
you have seen how to implement the Eureka Server. You can register Eureka Server to Zipkin server by adding one property in
 application.properties file located at src/main/resources.

spring.zipkin.base-url=http://localhost:9411/
Note: spring.zipkin.base-url determines the address where Zipkin Server is running.
	
pom.xml 

	<dependency>
	            <groupId>org.springframework.cloud</groupId>
	            <artifactId>spring-cloud-starter-zipkin</artifactId>
	</dependency>

Once Eureka Server is up and running, you can find traces in Zipkin Server and even you can see eureka-server in Service Name of Zipkin Server UI.
Then Chek zipkin Server UI with port number :9411
localhost:9411/zipkin/
Now you have learned how to implement Zipkin Server for Distributed Tracing.

======================================================================================

# Case 5: Implementing Spring Cloud Config Server
# Spring Cloud Config Server:
https://github.com/anjijava16/SpringBoot_SpringCloud_Repo/blob/master/spring-cloud-config.zip

Spring Cloud Config Server is a Spring-based centralized application which manages the application related configuration.

Spring Cloud Config is a client-server application for storing and serving the distributed configuration across multiple environments and applications.

In microservices architecture, there are a lot of small services and each service gas its own configuration, making it very difficult to manage the configuration for each service. Spring Cloud Config Server solves the problem of managing the configuration by storing it on a centralized repository and that repository can be Git or SVN. One of the advantages you can get from Spring Config Cloud Server is that whenever you are doing any changes in configuration, you don't have to restart the services

pom.xml
	
	<dependency>
	<groupId>org.springframework.cloud</groupId>
	<artifactId>spring-cloud-config-server</artifactId>
	</dependency>
	
	<spring-cloud.version>Finchley.SR2</spring-cloud.version>
	<dependency>
	<groupId>org.springframework.cloud</groupId>
	<artifactId>spring-cloud-dependencies</artifactId>
	<version>${spring-cloud.version}</version>
	<type>pom</type>
	<scope>import</scope>
	</dependency>

@SpringBootApplication
@EnableConfigServer
public class SpringConfigServerApplication {
public static void main(String[] args) {
SpringApplication.run(SpringConfigServerApplication.class, args);
}
}


# Case 6: Integrating Client Application With Spring Cloud Config Server
	@SpringBootApplication
	public class LimitsServiceApplication {
	public static void main(String[] args) {
	main()
	}


https://dzone.com/articles/spring-cloud-and-spring-bootimplementing-spring-cl

======================================================================================

#Case 7: Implementing Spring Boot Admin Server

	Spring BOOT Admin Server:
	It is difficult to monitor the microservices using Spring Boot Actuator Endpoint. 
	If the number of microservices increases, it means the number of actuator endpoints also increases. 
	In such scenarios, it is difficult to manage and monitoring the microservices.  
	Spring Boot Admin Server manage and monitor your all microservices. To handle such situations, 
	CodeCentric provides Spring Boot Admin UI which can manage and monitor all the microservices Spring Boot Actuator at single place.
	
	import de.codecentric.boot.admin.server.config.EnableAdminServer;
	@SpringBootApplication
	@EnableAdminServer
	public class AdminServerApplication {
	
	}

spring.application.name=admin-server
server.port=9090
http://localhost:9090/.


# Case 8:Registering Client Application With Spring Boot Admin Server

# Application Properties File 
	You need to add below two properties file in application.properties file of the client application.
	
	spring.boot.admin.client.url: determines the path of Spring Boot Admin Server.
	
	management.endpoints.web.exposure.include: determines which actuator endpoints needs to be exposed and * represents all actuator enpoints will be exposed.
	
	spring.boot.admin.client.url=http://localhost:9090
	management.endpoints.web.exposure.include=*
