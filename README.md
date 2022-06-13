# BLOG-JAVAWEB

publish a website:
1. put your website down to the webapps dir in the Tomcat, then you can access. The localhost:8080 is the root address, then /dirname will access the dir you want 
--webapps: Tomcat server's web index.
--root:
--WEB-INF:
  -classes: java program
  -lib: web dependencies on the jar package.
  -web.xml: web dependencies
  -index.html:default home page.
  -static:
    -css
    -js
    -img

How the website be accessed:
1. type in a domain name, then Enter.
2. The computer checked local's c:\windows\system32\drivers\etc\hosts, under this properties file, if the reflex of the domain input existed.
  2.1: Yes: return the ip address, in this address, it contains the web program we wanna access, diresctly access it.
  2.2: No: go to DNS server to look for, find then return, can not find,return can not find

4: HTTP
Hypertext Transfer Protocol: A simple request respond protocol, run on TCP.
-terxt: html, string...
-hypertext: image, music, video, location, maps .....
- port 80

Https: safe
443

4.2 Two generation for http
-http1.0: When the client connect to server, only get one web resource, then disconnect.
-http1.1: When the client connect to server, only get multi resources.

4.4 HTTP request
client-send request-server

request nethod: get/ post
get:each rewquest contains less, limit size, display data info in the url addressline, not safe but efficiency
post:each request contaions unlimited, unlimited size, no info display in the url addressline, dafe while not efficiency.


4.5 HTTP respond
server-respond-client

respond code: 
200: request okay
3**: redirect to a new location
4**(404): can not find resources
5**: server erro code   502: webgate erro

interview question:
when you input address into the url lineand press enter, untill the moment the page display on the screen, what happened?


5.MAVEN
why maven: Maaven is used to deploy and configure the jar package when they are needed in the java web development.

5.1 Maven project structure management tool
Maven constrain how you code java

pom.xml file:
is this the cor econfig file of maven.

WE may meet question like under maven, we may find that our config file written by us may can not be import out or become useful problem:
add a resource in the build.

Serverlet:

6.1 servlet introduction: sn company used it to develop dynamic web page technology.
There is an interface in these APIS called servlet.
If you wanna develop a servlet program, two steps:1 code a class, implement Servlet interface. 2.deploy the developed java class into the server.

Java program which aimplement servlet interface called servlet.

6.2 HelloServlet.



