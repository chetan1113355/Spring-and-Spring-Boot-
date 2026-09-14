# Spring-and-Spring-Boot

# DAY 1

## 1. Client -> Server communication architecture

**Client:** who sends HTTP/HTTPS request to store, get, update or delete information

**Ex:**
- browser / mobile app / react app / postman / android / ios app
- client could be server which is calling other server

**Server:** Machine which receives HTTP/HTTPS request and sends HTTP/HTTPS response wrt to request type


## 2. HTTP

A set of rules that defines how clients and servers communicate, including the structure of requests/responses, HTTP methods, headers, status codes, and how data is transferred.

**Request structure** — how a client should send a request
- HTTP method (GET, POST, PUT, PATCH, DELETE, etc.)
- URL
- Headers
- Body

**Response structure** — how a server should send a response
- Status code (200, 201, 400, 401, 404, 500, etc.)
- Headers
- Body


## 3. HTTPS

does the same thing as above by doing encryption of request and response


## 4. HTTP Status Codes

- **200 – OK** → Request was successful.
- **201 – Created** → Request was successful and a new resource was created.
- **400 – Bad Request** → Server cannot process the request because the request is invalid (e.g., invalid/missing data).
- **401 – Unauthorized** → Authentication is required or the provided authentication/credentials are invalid or missing.
- **403 – Forbidden** → Server understood the request, but the client does not have permission to access the resource.
- **404 – Not Found** → Requested resource/endpoint was not found.
- **500 – Internal Server Error** → Unexpected error occurred on the server.
- **503 – Service Unavailable** → Server is currently unable to handle the request, often because it is overloaded or temporarily unavailable.

**Trick To Remember:**

```text
2xx → Success
3xx → Redirection
4xx → Client/request problem
5xx → Server problem
```

## 5. A port number

Port number is a logical number used to identify a specific network service/application on a device.

```text
- http://       → Protocol
- 192.168.1.10  → IP address : every device has its own IP address which is used to communicate with that device
- 3000          → Port
- /api/users    → Resource/path

- IP address = building address 🏢
- Port number = apartment/room number 🚪
- Application = person/service inside that room

```
## 6. servelet

- java class runs in servelet container

- **Servelet container:** generally called as server (which runs in JVM)
- Ex: tomcat, jetty

- **Realtime Example:**

Client sends an HTTP request to the Tomcat server, which forwards it to the appropriate Servlet.
The Servlet processes the request and sends an HTTP response back through Tomcat to the Client.

```text
Client
  ↓ HTTP Request
Tomcat
  ↓
1. Receives the HTTP request
2. Parses the HTTP request
3. Identifies the URL/path and HTTP method
4. Finds the Servlet mapped to that URL
5. Creates/provides HttpServletRequest & HttpServletResponse
  ↓
Servlet
  ↓
6. Servlet processes the request
7. Servlet generates an HTTP response
  ↓
Tomcat
  ↓ HTTP Response
Client
```



## 7. Sprint Framework 
```markdown                
                         Spring Boot
                              │
          ┌───────────────────┼───────────────────┐
          │                   │                   │
          ↓                   ↓                   ↓
     Spring MVC          Spring Data          Spring AOP
          │                   │                   │
          └───────────────────┬───────────────────┘
                              │
                              ↓
                       Spring Security
                              │
                              ↓
                         Spring Core
                              │
                    IoC • DI • Beans

	- Spring Core → The foundation of Spring. Provides IoC, Dependency Injection (DI), and Beans.
	- Spring MVC → Used to build web applications and REST APIs.
	- Spring Data → Simplifies database/data-access operations.
	- Spring AOP → Handles cross-cutting concerns such as logging, transactions, etc.
	- Spring Security → Provides authentication and authorization.
	- Spring Boot → Makes it easier to configure and build Spring applications by providing auto-configuration, embedded servers, starters, etc.

```

## 8. Sprint Framework Architecture Workflow 
```markdown   
                   Client
                      │
                      ↓
               Spring Boot App- Controller  →  Service  →  Repository  →  ( Spring Data JPA  →  Hibernate  →  JDBC )  →  Database
                      │
      ┌───────────────┼────────────────┐
      ↓               ↓                ↓
 Spring MVC      Spring Security    Spring AOP
      
      ↑               ↑                ↑
      │               │                │
      └───────────────┼────────────────┘

                  Spring Core 

```
# DAY 2

Day-2

## 9. JAR: Java Archives 
- package which conatins multiple class files , resources(images, properties), folders / packages
- used to share java code easily 

- Liberary: consists of packages and classes which doesnt contains main functions menas which doesnt runs independently 
- Application: which can run independently , liberaries can be used in applications or other liberaries 

- To use external liberaries we use jar files only
	Ex: for data base connection ( mysql-connector.jar)

## 10. Maven : is a project management tool 

- **Does below 4 jobs for java application**
	1. Maintains project folder structure
	2. Helps to compile java code 
	3. Creates jar file of app / liberary code 
	4. Downloads dependencies ( external jar files)



## 11. POM.xml: file in project code : project object modal XML ( important file for maven )

 - **contains complete information about the project which conatins**
	 - manages information about all the dependencies in project
	 - project group id , artifact id etc 

- **Process to download new dependency in project**

- Go to mvnreporsitory website, search dependency name and copy the maven code provided and add it to the dependency tag in POM.xml and click on sync POM xml then mavan will download that dependency and transitive dependencies related to it

## 11.Maven Lifecycle

```markdown 
	validate
	   ↓
	compile
	   ↓
	test
	   ↓
	package
	   ↓
	verify
	   ↓
	install
	   ↓
	deploy

Phase	     Purpose
validate ->  Checks whether the project is correctly configured
compile	 ->  Compiles Java source code
test	 ->  Runs unit tests
package	 ->  Creates the JAR/WAR file
verify	 ->  Performs additional checks on the packaged application
install	 ->  Installs the package into your local Maven repository
deploy	 ->  Uploads the package to a remote Maven repository

```


