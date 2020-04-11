 -Dspring.profiles.active=staging
 java -jar application.jar --spring.profiles.active=cloud --spring.config.location=c:\config
 
 
 java -jar application.jar --spring.profiles.active=cloud 
 
 mvn package -DskipTests
mvn package -Dmaven.test.skip=true
mvn clean install 
-Dspring.profiles.active=peer1


##############################################################
##############################################################
# LOCATION TRANSPARANCY
		Naming Server (Eureka) 
	# Service Discoveries:
		  NetFlix Eureka
		  HashiCorp Consul
		  Apache Zookeeper

# Eureka Server Discovery :
    CartService Eureka Client ===> Service Registry Eureka Server ===> ProducetService Eureka Client 
	CartService Eureka Client ===> Product Service Eureka Client  ===> ProducetService Eureka Client 
	
	Note1: eureka server Start :
	           http://localhost:8761/

# HashiCorp Consul Discovery Agent :(It is Go Language)
   
           http://localhost:8500/ui/dc1/services
		   
# Zookeeper:
# zookeper Discovery Agent 
     zkServer.sh start
	 Then zkCli.sh 


           http://localhost:7081
##############################################################
##############################################################

# LOAD DISTRIBUTION
	Ribbon (Client Side)

#VISIBILITY AND MONITORING
		Zipkin Distributed Tracing
		Netflix API Gateway

#FAULT TOLERANCE
	Hystrix

# CENTRALIZED CONFIGURATION && MANAGEMENT
	Spring Cloud Config Server

# RESPONSE STATUS
	200 - SUCCESS
	404 - RESOURCE NOT FOUND
	400 - BAD REQUEST
	201 - CREATED
	401 - UNAUTHORIZED
	500 - SERVER ERROR


# MicroService Commuication through 
	Rest Template and Feign Client

# Dynamic Routing and Load Balcing using 
	Spring Cloud Ribbon

###############################################################
# NetFlix Zuul API Gateway 

Desktop  ---> API Gateway 
                                                ---> Product Service && Cart Service
Mobile ---> API Gateway  
 
 
  i. Reduce RoundTrips
  ii. Secuirty
  iii. Service Discovery integration
  iv. Cross cutting Concerns
  v. Load Balancing 
  vi. Caching the reponse
  vii. Dynamic Routing
  viii. Static response handing
  ix Rate Limiting and throuthing
  
# API Gateways:
   i. Netflix Zuul API Gateway
   ii. Spring Cloud Gateway
   iii. Apigee
   iv. Amazon AWS API gateway
   v. Azure API Gateway
   vi. Google Cloud Endpoints 
   vii. Express API Gateway     

############################################################### 

# Circuit Breaker
#  Monitoring : Netflix Hystrix Dashboard and Turbine

# Circuit Breker Implemenations:
 i.Netflix Hystrix (Not using)
 ii. Resilence4j (Using)
 iii. Sentinel (using)
 iv. Spring Retry 


# HYstrix Dashboard required : @EnableCircuitBreaker
http://192.168.0.3:8695/hystrix
URL : http://192.168.0.3:8695/actuator/hystrix.stream
http://192.168.0.3:8695/hystrix/monitor?stream=http%3A%2F%2F192.168.0.3%3A8695%2Factuator%2Fhystrix.stream
Enter:  http://192.168.0.3:8695/addMycart/12

# TurbineStream :
http://192.168.0.3:8695/hystrix
http://192.168.0.3:8095/turbine.stream

#  Distributed Tracing:  using Sleuth and Zipkin Server

 
 # Spring Cloud Seluth :
    Spring Cloud Sleuth 
	SPring Cloud Sleuth Logs are printed in the folloing format 
	  [ TraceID, SpanId, ZipKin ]
	  
	  
# Zipkin
	Zipkin is a distributed tracing system. It helps gather timing data needed to troubleshoot latency problems in service architectures. 
Features include both the collection and lookup of this data.	  
	http://localhost:9411/zipkin

	http://localhost:9411/zipkin/?serviceName=cartservice&spanName=all&lookback=3600000&startTs=1586642229946&endTs=1586645829946&annotationQuery=&minDuration=&limit=10&sortOrder=duration-desc


	 






 
 
 
