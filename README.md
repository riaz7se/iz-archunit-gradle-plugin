# iz-archunit-gradle-plugin
ArchUnit Test in Gradle Custom Plugin
<br/>
This repository contains gradle custom plugin that has ArchUnit test.

This plugin can be added to any java-gradle project to test standard archunit test.

To add this plugin to your project, follow below steps

```gradle
//add this this to project build.gradle

buildscript {
	dependencies {
		classpath "com.iz.aunit:iz-archunit:1.0.0-SNAPSHOT"
	}
	repositories {
		mavenLocal()
		mavenCentral()
	}
}
```

```gradle
apply plugin: 'com.iz.aunit'
```

```gradle
izArchUnitTest {
    enable = true
    classesPath = sourceSets.main.output[0]
    modulesHiearchySet = ['myapp-common', 'myapp-webservices', 'myapp-account', 'myapp-customer', 'myapp-report']
    excludeModulesSet = ['bdd', 'myapp-config']
}

####
```



```
