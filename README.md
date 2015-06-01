AdvancedGraphicImageRenderer
============================

Advanced PrimeFaces Graphic Image renderer for dynamic content.

See [blog text](http://jsfcorner.blogspot.be/2012/11/advanced-primefaces-graphic-image.html) for more information.

Version | For PrimeFaces
-----------| -------------
1.0     | 3.5
1.1     | 4.0
1.2.1   | 5.x

Version 1.2 has a bug!

When you want to add the artifact, put following snippets in your `pom.xml`

    <repositories>
       <repository>
          <id>nexus_C4J</id>
          <url>http://nexus-osc4j.rhcloud.com/content/groups/public/</url>
       </repository>
    </repositories>

    <dependency>
        <groupId>be.rubus.web.jsf.primefaces</groupId>
        <artifactId>advanced-graphic-image</artifactId>
        <version>1.2.1</version>
    </dependency>




This branch is intented to hold fixes to the advanced graphic image functionlity found in the base.
Current set of issues fixed on the current branch.
The functionlity of the advanced graphic image is being tested aginst the bug reporting repository:
https://github.com/99sono/delta-spike-dynamic-content_issue
Which comprises a small application that tests the primefaces graphic image using static and dynamic content with beans of different scopes. The main purpose of the fixes is siply to ensure that this advanced graphic image feature will work when using delta spike view scoped beans - while there isn't an officional resolution for this from either prime-faces or deltaspike team. 
<ul>
    <li> ISSUE 1: The base code cannot be deployment against weblogic due to the web-fargment.xml
    The problem of the file is two-fold. It uses an out of data namespace that gets rejected on deployment.
    It declares a listener that needs not be declared and causes deployment problems.
    
    <li> ISSUE 2: The base code is leaking files of 0 bytes on page refresh. On the initial navigation to the page
    the delta spike view access scoped labrador would be able to displayed, ans it was hoped with the library.
    But on page refreshes new files would be created with size 0 on the temp folder. The GraphicImageManager needed fixing.
</ul>
