Example to deploy a simple java proyect to a dockerized nexus

# Nexus

https://hub.docker.com/r/sonatype/nexus3/

Run the docker and when it is available execute a command to show the admin password

```
docker run -d -p 8081:8081 --name nexus sonatype/nexus3

curl http://localhost:8081

docker exec -u 0 -it nexus cat /nexus-data/admin.password
```


Loging in into [Nexus](http://localhost:8081) and change the password of user admin to 'admin'


# settings.xml

```
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
                          https://maven.apache.org/xsd/settings-1.0.0.xsd">
      <localRepository/>
      <interactiveMode/>
      <offline/>
      <pluginGroups/>
     
<servers>
   <server>
      <id>nexus3</id>
      <username>admin</username>
      <password>admin</password>
   </server>
</servers>

<!--
<mirrors>
        <mirror>
            <id>nexus-snapshots</id>
            <url>http://localhost:8081/repository/maven-public/</url>
            <mirrorOf>central</mirrorOf>
        </mirror>
   </mirrors>
-->

<mirrors/>

   <proxies/>
   <profiles/>
   <activeProfiles/>
</settings>
```