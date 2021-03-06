# Mock Jedis

Mock Jedis is a library for mocking out [Jedis](https://github.com/xetorthio/jedis) clients.
It's useful for testing your code without actually having a live redis server up.
Currently, mock-jedis supports pipelining and all the basic Jedis commands, but if you find missing 
functionality you're welcome to submit a pull request.

## Compile
with gradle (preferred method):
```shell
gradle build
```
with buildr:
```shell
buildr package
```

## Adding mock-jedis to your project

Compile the JAR with gradle/build/maven, install locally, and add it as a dependency to your project.

Here's a sample gradle script that will pull mock-jedis 0.1.2 from github and compile
```gradle
buildscript {
    repositories {
        mavenCentral()
    }
    dependencies {
        classpath 'org.batcha.gradle.plugins:git-dependencies:0.1'
    }
}

apply plugin: 'java'
apply plugin: 'git-dependencies'

dependencies {
  testCompile('com.fiftyonred:mock-jedis:0.1.2').ext.git = 'git://github.com/50onRed/mock-jedis.git'
}
```

Sample maven dependency definition:
```xml
<dependency>
    <groupId>com.fiftyonred</groupId>
    <artifactId>mock-jedis</artifactId>
    <version>0.1.2</version>
    <type>jar</type>
    <scope>test</scope>
</dependency>
```

## Using mock-jedis
```java
Jedis j = new MockJedis("test");
j.set("test", "123");
assertEquals("123", j.get("test"));
```
