## Using the Command Line interface ##

From your console run _java -jar oxpath-2.0-cli.jar -help_ to show the usage

## Using Maven ##


Add the following server specifications to your .m2/settings.xml file

```
   <server>
  	<id>diadem-nexus</id>
  	<username>oxpath</username>
  	<password>oxpath</password>
   </server> 
   <server>
  	<id>oxpath-releases</id>
  	<username>oxpath</username>
  	<password>oxpath</password>
   </server>
   <server>
  	<id>oxpath-snapshots</id>
  	<username>oxpath</username>
  	<password>oxpath</password>
   </server>
```

Add the following dependency to your pom.xml

```
   <dependency>
      <groupId>uk.ac.ox.cs.diadem</groupId>
      <artifactId>oxpath</artifactId>
    <version>2.0</version>
</dependency>
```

## Using the OXPath Maven Archetype ##


OXPath provides an archetype to generate a new project, which contains working examples.
(replace the info with your data)

```
mvn archetype:generate -DarchetypeArtifactId=archeoxpath -DarchetypeGroupId=uk.ac.ox.cs.diadem  -DarchetypeVersion=2.0 -DarchetypeRepository=http://diadem.cs.ox.ac.uk:8081/nexus/content/repositories/oxpath-public
-DgroupId=org.your.company -DartifactId=project -Dpackage=org.your.company.project  -Dversion=1.0-SNAPSHOT 
```

Test if the generate project builds successfully with

```
mvn clean compile
```

Import the generated project in your preferred IDE, and run the provided examples:

OXPathXMLExample.java
> Extracts publications from google scholar and returns a XML document
OXPathDBExample.java
> As above, but stores the extracted data in a DB (requires a DB to be configured)
OXPathRDFExample.java
> Extracts real estate listings from wwagency.com and builds RDF triples

Notes: the extraction expressions may not work as the target website could have changed from the time the expression was tested. We will update these over time.