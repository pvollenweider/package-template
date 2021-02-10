# package-template

> This project package some modules

## How to use it?

You can fork this repository and adapt it for your needs.

### Configuration

First you need to adapt your modules basic information such `artifactId`, `name`, `version` and `description` in the pom.xml
```xml
<artifactId>package-template</artifactId>
<name>Package Template</name>
<version>1.0.0</version>
<description>This project package my modules</description>
```
Once it's done, you need to set a few properties used for the manifest and the package name.

```xml
<jahia.final.package.name>package-template</jahia.final.package.name>
<jahia.manifest.package.id>package-template</jahia.manifest.package.id>
<jahia.manifest.description>my-module, another-module</jahia.manifest.description>
```
Then you will need to add as dependencies all modules that you want to package. 

In the following example we want to add the following modules:

 - `my-module` from `org.jahia.modules` in version `1.0.0`
 -  `another-module` from `org.foo.modules` in version `2.0.0`

Note that these 2 modules are released and available in my local repository.
If you need to create a package with snapshots, then you have to change the version as needed.

```xml
<dependencies>
    <dependency>
        <groupId>org.jahia.modules</groupId>
        <artifactId>my-module</artifactId>
        <version>1.0.0</version>
    </dependency>
    <dependency>
        <groupId>org.foo.modules</groupId>
        <artifactId>another-module</artifactId>
        <version>2.0.0</version>
    </dependency>
</dependencies>
```
If your modules have a `groupId` different from `org.jahia.modules`, you will need to 
configure a list of all `groupId` you want to include, using a `includeGroupIds` configuration. 

For instance if you have modules with `groupId` with `org.jahia.modules` and `org.foo.modules` then you should set this in both `copy-dependencies-sources` and `copy-dependencies` goals:

```xml
<includeGroupIds>org.jahia.modules,org.foo.modules</includeGroupIds>
```
### Time to build

To create your package, simply use maven:

```shell
mvn install
```

It's done. If everything went good, your package is available under the `target` directory.
