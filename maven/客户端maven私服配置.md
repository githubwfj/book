## 配置Maven私服
在项目的POM文件中配置,每个项目都需要配置
<font color=red size=4 face="微软雅黑">不推荐</font>
```
<repositories>
    <repository>
        <id>maven-nexus</id>
        <name>maven-nexus</name>
        <url>http://ip:8081/repository/maven-public/</url>
        <snapshots>
            <enabled>true</enabled>
        </snapshots>
        <releases>
            <enabled>true</enabled>
        </releases>
    </repository>
</repositories>
```
在setting.xml文件中配置，对所有项目起作用
```
<profiles>
    <profile>
        <id>nexus</id>
        <repositories>
            <repository>
                <id>maven-nexus</id>
                <name>Nexus</name>
                <url>http://ip:8081/repository/maven-public/</url>
                <releases>
                    <enabled>true</enabled>
                </releases>
                <snapshots>
                    <enabled>true</enabled>
                    <updatePolicy>always</updatePolicy>
                </snapshots>
            </repository>
        </repositories>
    </profile>
</profiles>

<activeProfiles>
    <activeProfile>nexus</activeProfile>
</activeProfiles>
```
先去访问私服，如果私服挂掉了，会直接去访问中央仓库

如果不想私服挂掉了，去访问中央仓库的话，可以这么配置
<font color=red size=4 face="微软雅黑">推荐</font>
```
<mirror>
      <id>maven-nuxus</id>
      <name>maven nexus</name>
      <url>http://ip:8081/repository/maven-public/</url>
      <mirrorOf>central</mirrorOf>
</mirror>
```

## 发布构件到Nexus私服
首先在setting.xml文件中配置帐号信息，admin，admin123是默认的帐号密码
```
<servers> 
  <server>  
	<id>releases</id>  
	<username>admin</username>  
	<password>admin123</password>  
  </server>  
  <server>  
	<id>snapshots</id>  
	<username>admin</username>  
	<password>admin123</password>  
  </server>
</servers>
```
然后在项目POM文件中加入如下配置：
```
<distributionManagement>
    <snapshotRepository>
        <id>snapshots</id>
        <name>Nexus Snapshot</name>
        <url>http://ip:8081/repository/maven-snapshots</url>
    </snapshotRepository>
    <repository>
        <id>releases</id>
        <name>Nexus Release</name>
        <url>http://ip:8081/repository/maven-releases</url>
    </repository>
</distributionManagement>
```

mav 常用命令说明
```
# package命令完成了项目编译、单元测试、打包功能，但没有把打好的可执行jar包（war包或其它形式的包）布署到本地maven仓库和远程maven私服仓库
mvn clean package

# install命令完成了项目编译、单元测试、打包功能，同时把打好的可执行jar包（war包或其它形式的包）布署到本地maven仓库，但没有布署到远程maven私服仓库
mvn clean install

# deploy命令完成了项目编译、单元测试、打包功能，同时把打好的可执行jar包（war包或其它形式的包）布署到本地maven仓库和远程maven私服仓库
mvn clean deploy
```