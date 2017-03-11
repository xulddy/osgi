# Bundles

* Bundles are the unit of modularity in OSGi.
* They are are also a kind of JAR file.
* As files, bundles are physical modules. Bundles can be moved or copied. Contrast with packages, which are logical modules.
* **Literally** a JAR file with special headers in its `MANIFEST.MF` file.

## Maven & Bundle Plugin
* Maven builds the JAR files.
* Maven bundle plugin. Generates the special headers in the `MANIFEST.MF` file.

## Grouping Things: modules, bundles, packages, and artifacts
* Modules - Maven compile-time construct
* Artifacts - Maven run-time construct
* Packages - Java compile-time construct
* JARs - JRE run-time construct
* Bundles - OSGi run-time construct.

These constructs have a loose relationship to each other. If I had to draw a UML diagram of it, it would look like this:

![Groups](UML-diagram.png)

* JAR files are a kind of Maven artifact
* Bundle are a kind of JAR file
* Bundles can import, export, or embed packages
* Maven builds modules into artifacts
* Maven modules can be nested
* Packages can be nested
* Maven modules can contain multiple packages
* Classes are .java files
* Packages can import classes from other packages
* Classes belong to a package


#### How to install a bundle
* `bundle:install file://{bundle_folder}/filename.jar`
* `bundle:install mnv:{group ID}/{artifact ID}/{version}`
* Copy the JAR file to Karaf's deploy directory

When a bundle is installed it is copied to a cache and is always loaded from the cache. 

#### Preferred to install a bundle
* Use the Maven address

## Karaf Shell 

#### Command Line Basics
* `list`, `start`, `stop`, `refresh`

#### Updating Bundles
* `list -u <id>` to find bundle location
* `update <id>` to reload a bundle by its ID
* `bundle:watch <id>` to reload bundle when  Maven  installs the artifact in the local repository

#### Karaf Shell Magic
* `($.context bundle 1) location`
* See [Karaf Scripting](https://svn.apache.org/repos/asf/karaf/site/production/manual/latest/scripting.html) for more information.

#####See also [Karaf Documentation](http://supergsego.com/apache/karaf/documentation/4_x.html)