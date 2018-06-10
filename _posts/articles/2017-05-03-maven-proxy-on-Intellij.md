---
published: true
layout: post
excerpt: description
categories: articles
share: true
tags:
  - java
  - intellij
  - maven
---
## 1 Maven Proxy setup

If your company uses a proxy to access internet and your artifacts are not available within your company's nexus, you need to download and install [CNTLM](http://cntlm.sourceforge.net/) 

Edit your cntlm.ini file
```ini
Username    [username]
Domain      [domain]
Password    [password]
Proxy       [your proxy]:[port]
Listen      [port number of cntlm]
```

On Intellij, go to File > Default Settings > Other Settings > Maven > User Settings File

Create a settings file settings.xml on the specified folder and configure your proxy

```xml
<proxy>
   <id>optional</id>
   <active>true</active>
   <protocol>http</protocol>
   <host>localhost</host>
   <port>3133</port>
</proxy>
```

You may then launch your cntlm service using the service manager (Windows)

## 2 Find the appropriate groupId/artifactId of a specific dependency

Maven lets you download all the needed dependencies.
If you need the following classe for instance
```java
import org.apache.hadoop.security.UserGroupInformation;
```

You need first to find the corresponding groupId (org.apache.hive) and the artifacatId (hive-jdbc)

**It may be tricky to find the proper artifactId. As you may see the artifactId hadoop-common is the one that contains the org.apache.hadoop.security package.**

You may use the following tool : [http://search.maven.org/#advancedsearch](http://search.maven.org/#advancedsearch)

You need to add this dependency into your pom.xml with its version
```xml
<dependencies>
    <dependency>
        <groupId>org.apache.hadoop</groupId>
        <artifactId>hadoop-common</artifactId>
        <version>2.7.1</version>
    </dependency>
</dependencies>
```    
## 3 Setting many repos

Your artifacts may be on different repos. Maven lets you define several repos : 
```xml
<repositories>
    <repository>
        <snapshots>
            <enabled>true</enabled>
        </snapshots>
        <id>central</id>
        <name>Central Repository</name>
        <url>http://repo.maven.apache.org/maven2</url>
    </repository>
    <repository>
        <snapshots>
            <enabled>false</enabled>
        </snapshots>
        <id>centralhortonn</id>
        <name>Central Repository</name>
        <url>http://repo.hortonworks.com/content/repositories/releases/</url>
    </repository>
</repositories>
```