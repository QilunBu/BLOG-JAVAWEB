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

6.5 ServletContext:
share information
present right now webapp,create a servlet Context obj for each web program when the web is started.
  sharing data :data saved in this servlet and can be get in another servlet.
  
  create a class save the data, then create a class read the data.
 
ServletContext context = this.getServletContext();
context.setAttribute;
context.getAttribute;
context.getInitParameter  //get initial parameter in the xml file
context.getRequestDispatcher  //show anothe rpage info to you without visiting address change

6.6 HttpServletResponse
When the web; server get http request feom client, based on this reqest, create HttpServletRequest obj, represent one HttpServletResponse.
If we want to get parameter from the client port, find HttpServletRequest.
If we wanna give some response to the client, find  HttpServletResponse.

6.6-1 : method which is responsible for sending data to web:
-getWriter
-getOutputStream
send response header to web:
-setCharacterEncoding(String var1);
-setContentLength(int var1);
-setDataHeader(String var1, long var2);
-addDataHeader(String var1, long var2);

6.6-2 downloadfile:
1.get path of file need to be downloaded
2.name of the file
3.set the web to support what we are going to download
4.get the input stream of the file
5.acreate a buffer zone
6.get outputstream
7.writer fileOutPutStream to the buffer zone
8.use outputstream to output file to the client.

6.6-3 verified code:
1.front end 
2.back end

```java```
package com.qilun.servlet;

import javax.imageio.ImageIO;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.awt.*;
import java.awt.image.BufferedImage;
import java.io.IOException;
import java.util.Random;

public class ImageServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //set browser refresh each 3s.
        resp.setHeader("refresh", "3");
        //in the memory, create a pic
        BufferedImage image = new BufferedImage(80, 20, BufferedImage.TYPE_INT_BGR);

        Graphics2D g = (Graphics2D) image.getGraphics();  //set a pen
        //set color
        g.setColor(Color.WHITE);
        g.fillRect(0, 0, 80, 20);
        //give data to the pic
        g.setColor(Color.BLACK);
        g.setFont(new Font(null, Font.BOLD, 20));
        g.drawString(makeNum(), 0, 20);

        //tell browser this request open with image
        resp.setContentType("image/jpeg");
        //website has cache, so let browser not cache
        resp.setDateHeader("expires", -1);
        resp.setHeader("cache-control", "no-cache");
        resp.setHeader("pragma", "no-cache");

        //write the pic to the browser
        ImageIO.write(image, "jpg", resp.getOutputStream());

    }

    //generate random number
    private String makeNum(){
        Random random = new Random();
        String num = random.nextInt(9999999) + "";
        StringBuffer sb = new StringBuffer();
        for (int i = 0; i < 7 - num.length(); i++) {
            sb.append("0");
        }
        String s = sb.toString() + num;
        return num;
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
--------------------------------------------------------------------------------------------------------

response redirect:
a web resource receive the request of the client and it acknowledge the client to access another web resource, it is called redirect.
normal case: customer login

6.7 HttpServletRequest
Represent the request of the client. user access server throuth http request, a;; the info in the http will be up to the httpservletrequest,


8.6 JSP tag, JSTL tag, EL expression


EL express language: ${}
1 get data 2 execute calculate  3 get web development object

----------------------------------------------------------------------
dependency : jspl-api  and standard 
        <dependency>
            <groupId>javax.servlet.jsp.jstl</groupId>
            <artifactId>jstl-api</artifactId>
            <version>1.2</version>
        </dependency>
<!--        standard store-->
        <dependency>
            <groupId>taglibs</groupId>
            <artifactId>standard</artifactId>
            <version>1.1.2</version>
        </dependency>



JSP tag:
<jsp:include page="jsptag2.jsp"></jsp:include>
<jsp:forward page="/jsptag2.jsp">  //when this page is accessed, forward the access to the new address in the pag=""
    <jsp:param name="age" value="12"/>  //set name and value to a parameter which canbe get in the new address
    <jsp:param name="name" value="value1"/>
</jsp:forward>

JSTL lable:
https://www.runoob.com/jsp/jsp-jstl.html
It isw the combination and collection of JSP tag. It package the JSP application general core function.
Using JSTL is to prevent the weak of HTML lable.

core tag: Core tags are the most commonly used JSTL tags. The syntax for referencing the core tag library is as follows:
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>

JSTL tag using steps: 
1. import the target taglib
2. using the method in it.
3. Also need to import jar package in the tomcat to avoid error.

9. JAVABEAN:
object class:must have non parameter construct, 
must private parameter,
must have set and get method

ORM: OBJECT RELATIONAL MAPPing
DAO: DATA ACCESS OBJECT

MVC:
Model: control service, DAO and javabean
view:show data, start servlet request
controller: receive the client request. Call model to execute different code. Control view jump.

Filter:
This filter is used for filting data.

Filter development fteps:
1.Import packages.
2.code filters
  -1. Filter belongs to javax.filter
  -2. Must override three methods: init destory and doFilter
  servlet need to config in the web.xml, also the filter do.
  -3. implement filter interface
 ------------------------------------------------------------------
 package com.qilun.filter;

import javax.servlet.*;
import java.io.IOException;

public class CharacterEncodingFilter implements Filter {
    @Override
    //initial
    public void init(FilterConfig filterConfig) throws ServletException {

    }

    @Override
    //all the code in the chain will process when doing specific request
    //chain.doFilter(request, response); must write, keep the whole chain run.
    public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain) throws IOException, ServletException {
        request.setCharacterEncoding("utf-8");
        response.setCharacterEncoding("utf-8");
        response.setContentType("text/html;charset=UTF-8");

        System.out.println("Character filter before operate");

        chain.doFilter(request, response); //let our request go. If not write, progress stops.
        System.out.println("Character filter after operate");

    }

    @Override
    //destroy
    public void destroy() {
        System.out.println("CharacterEncodingFilter has been destroyed.");

    }
}
-------------------------------------------------------------
  -4. config in the xml file
  <filter>
        <filter-name>CharacterEncodingFilter</filter-name>
        <filter-class>com.qilun.filter.CharacterEncodingFilter</filter-class>
    </filter>
    <filter-mapping>
        <filter-name>CharacterEncodingFilter</filter-name>
        <url-pattern>/servlet/*</url-pattern>
    </filter-mapping>
------------------------------------------------------------------

Listener:
1.code a listener
 -1.implement listener interface.
 ------------------------------------------------------------------------------------
 package com.qilun.listener;

import javax.servlet.ServletContext;
import javax.servlet.http.HttpSessionEvent;
import javax.servlet.http.HttpSessionListener;

//count session so you can count online number
public class OnlineCountListener implements HttpSessionListener {
    @Override
    //when create one session, active this method once.
    public void sessionCreated(HttpSessionEvent se) {
        ServletContext ctx = se.getSession().getServletContext();

        System.out.println(se.getSession().getId());
        Integer onlineCount = (Integer) ctx.getAttribute("OnlineCount");

        if (onlineCount==null){
            onlineCount= new Integer(1);
        }else {
            int count = onlineCount.intValue();
            onlineCount = new Integer(count + 1);
        }

        ctx.setAttribute("OnlineCount", onlineCount);
    }

    @Override
    public void sessionDestroyed(HttpSessionEvent se) {
        ServletContext ctx = se.getSession().getServletContext();
        Integer onlineCount = (Integer) ctx.getAttribute("OnlineCount");

        if (onlineCount==null){
            onlineCount= new Integer(0);
        }else {
            int count = onlineCount.intValue();
            onlineCount = new Integer(count - 1);
        }

        ctx.setAttribute("OnlineCount", onlineCount);

    }
}
-------------------------------------------------------------------------------------
  -2.config the listener
<listener>
        <listener-class>com.qilun.listener.OnlineCountListener</listener-class>
    </listener>
    
User login ten access home page, otherwise, cannot access.   

User filter, without login cannot access.
------------------------------------------------------------------------
    @Override
    public void doFilter(ServletRequest req, ServletResponse resp, FilterChain chain) throws IOException, ServletException {
        HttpServletRequest request = (HttpServletRequest) req;
        HttpServletResponse response = (HttpServletResponse) resp;


        if (request.getSession().getAttribute(Constant.USER_SESSION) == null){
            response.sendRedirect("/error.jsp");
        }
        chain.doFilter(request, response);
    }
-----------------------------------------------------------------------------------

junit:
dependency:
<dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>4.12</version>
        </dependency>

    
@Test only available on method.


SMBMS



























