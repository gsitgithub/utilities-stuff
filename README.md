# utilities-stuff
General utilities files and links.

DI        : https://github.com/zsoltherpai/feather | https://github.com/google/tiger | https://github.com/osglworks/java-di |Dagger2, Guice |https://github.com/vanillasource/jaywire
Reflection: https://github.com/EsotericSoftware/reflectasm
Converter : https://github.com/brettwooldridge/HikariJSON
MVC       : https://github.com/actframework/actframework, https://github.com/osglworks/java-mvc
DB-Pool   : https://github.com/brettwooldridge/HikariCP
Logging   : minlog, tinylog, minlog-slf4j

http://blog.nqzero.com/2016/01/asynchronous-java-webserver-hello-world.html
Comsat (Quasar) added a substantial overhead on top of async Jetty, and exhibited some failures at high concurrency. i've tried several different implementations based on the documentation and code from TEBM, and all performed about the same

http://blog.paralleluniverse.co/2014/05/29/cascading-failures/

Indeed a full scale Java/Spring/Hibernate/JSF implementation may be a bit too engineered for the requirements of many small scale systems, however I typically evaluate new application requirements on the following factors to help myself determine the appropriate architecture:
#Anticipated User Load
    What is the anticipated user load?
    Are there potentially an enormous amount of users?
    Are the users performing tasks that will utilize high amounts of resources?
    Will the application need to scale horizontally with increased load?

#Anticipated Future Scope
This one is hard to judge sometimes because the scope can sometimes be at the whim or will of a product manager or sales person. If you anticipate that there is even the smallest possibility that a salesperson could try to brand it and sell it to anybody other than the original stakeholders then it is probably best to go with a more layered approach.

#Distributed System Needs
Are there any anticipated needs for various differing consumers to achieve different information in different ways (Mobile app, ETL, SSO, public web services, etc...) then you always want to have a three tier distribution approach and have logical seperation of components and layers. These types of architectural requirements will be better served by a more engineered approach.

#Budget Constraints
What is the allocated budget for hosting the application in production? Will it require expensive proprietary software licenses, multiple VPS's, high availability cloud computing? Perhaps if you are only allowed a limited budget then CHEAP hosting technologies like PHP may make a lot more sense.

#Knowledge Constraints
What is your team more efficient in implementing? What are their skills and weaknesses. Sure Play Framework may look cool for rapid application development, however if there is a significant learning curve there then perhaps you take less risk in the more cumbersome over-engineered approach that is well understood.

#Time Constraints
How much time do you have to develop the application. This also plays into Knowledge Constraints as time needed to learn a new technology can be an imposition on time.

A curated list of awesome C/C++ frameworks, libraries, resources, and shiny things. Inspired by awesome-... stuff. http://fffaraz.github.io/awesome-cpp/     https://github.com/fffaraz/awesome-cpp

Be a Professional Programmer : http://tools.zhaishidan.cn/    https://github.com/stanzhai/be-a-professional-programmer

Java-projects : consistency-hash, load-balance, j2se-project, j2ee-project, template.
http://blog.longjiazuo.com/   https://github.com/longjiazuo/java-project

http://ufasoli.blogspot.in/2016/12/use-github-as-cdn-to-store-and-serve.html  http://rawgit.com/

https://github.com/NitorCreations/tomcat8-war-runner/blob/master/src/main/java/org/apache/tomcat/maven/runner/Tomcat8Runner.java
http://web.archive.org/web/20090228071059/http://blog.platinumsolutions.com/node/234
http://commons.apache.org/proper/commons-daemon/procrun.html
Besides that, you may look at the bin\service.bat in Apache Tomcat to get an idea how to setup the service. In Tomcat they rename the Procrun binaries (prunsrv.exe -> tomcat6.exe, prunmgr.exe -> tomcat6w.exe).
Something I struggled with using Procrun, your start and stop methods must accept the parameters (String[] argv). For example "start(String[] argv)" and "stop(String[] argv)" would work, but "start()" and "stop()" would cause errors. If you can't modify those calls, consider making a bootstrapper class that can massage those calls to fit your needs.

http://yajsw.sourceforge.net/ , http://nssm.cc/


#Handlebars
https://stackoverflow.com/questions/10037936/node-js-with-handlebars-js-on-server-and-client problem
You should use pre-compiled client templates. They are faster executing and allow you to use the same template language on the server and client.
    Install handlebars globally npm install handlebars -g
    Precompile your templates handlebars client-template1.handlebars -f templates.js
    Include templates.js <script src="templates.js"></script>
    Execute the template var html = Handlebars.templates["client-template1"](context);
https://stackoverflow.com/a/13884587/8360
https://gist.github.com/utsengar/2287070
http://berzniz.com/post/24743062344/handling-handlebarsjs-like-a-pro
http://www.korenlc.com/precompiling-handlebars-templates/
<script> 
    $(function(){
      var postData={title: "My New Post", content: "This is my first post!"};
     getTemplate('template-1',postData).done(function(data){
       $('body').append(data)
     })
    });
    
    function getTemplate( name,data){
      var d=$.Deferred();
      $.get(name+'.html',function(response){
        var template = Handlebars.compile(response);
        d.resolve(template(data))
      });
      return d.promise();
    }
  </script>