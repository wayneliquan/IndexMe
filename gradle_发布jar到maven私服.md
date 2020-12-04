# Gradle发jar到maven私服nexus

[toc]


## 1. gradle.build
```
plugins {
    id 'maven-publish'
}

// ...

publishing {
    publications {
        myPublish(MavenPublication){
            from components.java
        }
    }
    repositories {
        maven {
            def releasesRepoUrl = "http://192.168.1.100:8081/repository/maven-releases/"
            def snapshotsRepoUrl = "http://192.168.1.100:8081/repository/maven-snapshots/"
            url = version.endsWith('SNAPSHOT') ? snapshotsRepoUrl : releasesRepoUrl
            credentials {
                username 'nexus用户名'
                password 'nexus密码'
            }
        }
    }
}
```

## 2. 执行发布命令

```shell
gradle publish
```

## 3. 问题解决

1. maven-metadata.xml ··· Remote repository doesn't support sha-256.

   日志如下：

```
Cannot upload checksum for snapshot-maven-metadata.xml. Remote repository doesn't support sha-256. Error: Could not PUT 'http://.../x.y.z-SNAPSHOT/maven-metadata.xml.sha256'. Received status code 400 from server: Invalid path for a Maven 2 repository
Cannot upload checksum for snapshot-maven-metadata.xml. Remote repository doesn't support sha-512. Error: Could not PUT 'http://.../x.y.z-SNAPSHOT/maven-metadata.xml.sha512'. Received status code 400 from server: Invalid path for a Maven 2 repository
Cannot upload checksum for module-maven-metadata.xml. Remote repository doesn't support sha-256. Error: Could not PUT 'http://.../x.y.z-SNAPSHOT/maven-metadata.xml.sha256'. Received status code 400 from server: Invalid path for a Maven 2 repository
Cannot upload checksum for module-maven-metadata.xml. Remote repository doesn't support sha-512. Error: Could not PUT 'http://.../x.y.z-SNAPSHOT/maven-metadata.xml.sha512'. Received status code 400 from server: Invalid path for a Maven 2 repository
```

解决方案

gradle.properties 添加配置如下：

```properties
systemProp.org.gradle.internal.publish.checksums.insecure=true
```

或命令行执行添加参数：

```shell
-Dorg.gradle.internal.publish.checksums.insecure=true
```

参考： https://github.com/gradle/gradle/issues/12355

## 4. 参考资料
https://docs.gradle.org/current/userguide/publishing_maven.html

