
ArchUnit Test in Gradle Custom Plugin
This repository contains gradle custom plugin that has ArchUnit test.

This plugin can be added to any java-gradle project to test standard archunit test.

```gradle
configurations {
    // configuration that holds jars to include in the jar
    extraLibs
}

dependencies {
    compile 'org.codehaus.groovy:groovy-all:2.4.7'
    extraLibs group: 'net.java.dev.jna', name: 'jna-platform', version: '4.2.2'
    testCompile group: 'junit', name: 'junit', version: '+'
    configurations.compile.extendsFrom(configurations.extraLibs)
}

jar {
    from {
            configurations.extraLibs.collect { it.isDirectory() ? it : zipTree(it) }
        }
}

```

To add this plugin to your project, follow below steps

```gradle
//add this this to project build.gradle

buildscript {
	dependencies {
		classpath "com.iz.arunit:iz-arunit:1.0.0-SNAPSHOT"
	}
	repositories {
		mavenLocal()
	}
}
```

```gradle
apply plugin: 'com.iz.arunit'
```

```gradle
izArchUnitTest {
    enable = true
    classesPath = sourceSets.main.output[0]
    modulesHiearchySet = ['myapp-common', 'myapp-webservices', 'myapp-account', 'myapp-customer', 'myapp-report']
    excludeModulesSet = ['bdd', 'myapp-config']
}
```
####


```gradle
configurations {
    // configuration that holds jars to include in the jar
    extraLibs
}

dependencies {
    compile 'org.codehaus.groovy:groovy-all:2.4.7'
    extraLibs group: 'net.java.dev.jna', name: 'jna-platform', version: '4.2.2'
    testCompile group: 'junit', name: 'junit', version: '+'
    configurations.compile.extendsFrom(configurations.extraLibs)
}

jar {
    from {
            configurations.extraLibs.collect { it.isDirectory() ? it : zipTree(it) }
        }
}
```
