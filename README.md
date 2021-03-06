[![Travis Build Status](https://travis-ci.org/javafx-maven-plugin/javafx-maven-plugin.svg?branch=master)](https://travis-ci.org/javafx-maven-plugin/javafx-maven-plugin)
[![AppVeyor Build status](https://ci.appveyor.com/api/projects/status/64700ul3m9y88agi/branch/master?svg=true)](https://ci.appveyor.com/project/FibreFoX/javafx-maven-plugin/branch/master)
[![Maven Central](https://img.shields.io/maven-central/v/com.zenjava/javafx-maven-plugin.svg)](https://maven-badges.herokuapp.com/maven-central/com.zenjava/javafx-maven-plugin)
[![Dependency Status](https://www.versioneye.com/java/com.zenjava:javafx-maven-plugin/8.5.0/badge.svg)](https://www.versioneye.com/java/com.zenjava:javafx-maven-plugin/8.5.0)


JavaFX Maven Plugin
===================

The JavaFX Maven Plugin provides a way to assemble distribution bundles for JavaFX applications (8+) from within Maven.
 
For easy configuration please use our new website (currently getting updated/reworked):
**[http://javafx-maven-plugin.github.io](http://javafx-maven-plugin.github.io)**

For (outdated) documentation/examples, your can look at archived website:
**[https://web.archive.org/web/20141009064442/http://zenjava.com/javafx/maven/](https://web.archive.org/web/20141009064442/http://zenjava.com/javafx/maven/)**


Quickstart for JavaFX JAR
=========================

Add this to your pom.xml within to your build-plugin:

```xml
<plugin>
    <groupId>com.zenjava</groupId>
    <artifactId>javafx-maven-plugin</artifactId>
    <version>8.5.0</version>
    <configuration>
        <mainClass>your.package.with.Launcher</mainClass>
    </configuration>
</plugin>
```

To create your executable file with JavaFX-magic, call `mvn jfx:jar`. The jar-file will be placed at `target/jfx/app`.


Quickstart for JavaFX native bundle
===================================

Add this to your pom.xml within to your build-plugin:

```xml
<plugin>
    <groupId>com.zenjava</groupId>
    <artifactId>javafx-maven-plugin</artifactId>
    <version>8.5.0</version>
    <configuration>
        <vendor>YourCompany</vendor>
        <mainClass>your.package.with.Launcher</mainClass>
    </configuration>
</plugin>
```

To create your executable file with JavaFX-magic and some installers (please see official oracle-documentation which applications are required for this), call `mvn jfx:native`. The native launchers or installers will be placed at `target/jfx/native`.



Prepared for Java 9
===================

Add repository in your `pom.xml` for snapshot-versions of this plugin:

```xml
<pluginRepositories>
    <pluginRepository>
        <id>oss-sonatype-snapshots</id>
        <url>https://oss.sonatype.org/content/groups/public/</url>
        <snapshots>
            <enabled>true</enabled>
        </snapshots>
    </pluginRepository>
</pluginRepositories>
```

Set version to new SNAPSHOT-version:

```xml
<plugin>
    <groupId>com.zenjava</groupId>
    <artifactId>javafx-maven-plugin</artifactId>
    <version>9.0.0-SNAPSHOT</version>
    <configuration>
        <!-- your configuration -->
    </configuration>
</plugin>
```

*Some notes: as this isn't the main branch, a lot of features aren't present in that branch yet, deployment of new "-SNAPSHOT"-version are on-demand*
**This is currently heavily outdated and will be updated June 2016**


Last Release Notes
==================

**Version 8.5.0 (30-May-2016)**

Bugfixes:
* updated workaround-detection for creating native bundles without JRE, because [it got fixed by latest Oracle JDK 1.8.0u92](http://www.oracle.com/technetwork/java/javase/2col/8u92-bugfixes-2949473.html)
* added workaround for native linux launcher inside native linux installer bundle (DEB and RPM) not working, see issue [#205](https://github.com/javafx-maven-plugin/javafx-maven-plugin/issues/205) for more details on this (it's a come-back of the [issue 124](https://github.com/javafx-maven-plugin/javafx-maven-plugin/issues/124))

New:
* added ability to write and use custom bundlers! This makes it possible to customize the work which is required for your bundling-process.
* added new property to disable "native linux launcher inside native linux installer"-fix `<skipNativeLauncherWorkaround205>true</skipNativeLauncherWorkaround205>`

Improvements:
* added IT-project "23-simple-custom-bundler"
* added IT-project "24-simple-custom-bundler-failed", which fails to use custom bundler, but does not fail (normal behaviour)
* added IT-projects regarding workaround for issue 205 (currenty they do nothing, I still need to write some verify-beanshell files)
* moved workarounds and workaround-detection into its own class (makes it a bit easier to concentrate on the main work inside NativeMojo)


(Not yet) Release(d) Notes
==========================

upcoming Version 8.5.1 (???-2016)

* nothing changed yet