[toc]

# mvn deploy 配置

sudo apt install maven

cp /etc/maven/settings.xml .m2/

vim .m2/settings.xml

- 配置server, 配置用户名和密码

```
<servers>
	<server>
    	<id>local-nexus</id>
        <username>xxxxx</username>
        <password>123456</password>
     </server>
</servers>
```

- 配置私有maven参考

    <mirrors>
    	<mirror>
      		<id>nexus-local</id>
      		<mirrorOf>central</mirrorOf>
      		<name>Nexus local</name>
      		<!--url>http://maven.aliyun.com/nexus/content/groups/public</url-->
      		<url>http://192.168.1.100:8081/repository/alyun_maven/</url>
    	</mirror>
    </<mirrors>
- 配置发布地址

```
</profiles>
	<profile>
      <id>local-nexus</id>
      <repositories>
        <repository>
          <id>local-nexus</id>
          <name>my-local-nexus</name>
          <url>http://192.168.1.100:8081/repository/maven-public/</url>
          <layout>default</layout>
          <snapshotPolicy>always</snapshotPolicy>
        </repository>
      </repositories>
    </profile>
    
    <!-- 配置默认编译使用jdk8 -->
    <profile>
       <id>jdk8</id>
       <activation>
         <activeByDefault>true</activeByDefault>
         <jdk>1.8</jdk>
       </activation>
       <properties>
         <maven.compiler.source>1.8</maven.compiler.source>
         <maven.compiler.target>1.8</maven.compiler.target>
         <maven.compiler.compilerVersion>1.8</maven.compiler.compilerVersion>
       </properties>
     </profile>
  </profiles>
```

- 激活配置

```
  <activeProfiles>
        <activeProfile>local-nexus</activeProfile>
        <activeProfile>jdk8</activeProfile>
  </activeProfiles>
```



vim pom.xml

- jar 包发布配置

```
<distributionManagement>
    <repository>
      <id>local-nexus</id>
      <name>local-nexus</name>
      <url>http://192.168.1.100:8081/repository/maven-releases/</url>
    </repository>
    <snapshotRepository>
      <id>local-nexus</id>
      <name>local-nexus</name>
      <url>http://192.168.1.100:8081/repository/maven-snapshots/</url>
    </snapshotRepository>
  </distributionManagement>
```



发布：

```
mvn clean install deploy
```

