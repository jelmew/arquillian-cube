#Deploy to artifactory
Set settings.xml to:
amenj@amenj-Precision-5520:~/Projects/Own/arquillian-cube$ cat ~/.m2/settings.xml 
<?xml version="1.0" encoding="UTF-8"?>
<settings xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.1.0 http://maven.apache.org/xsd/settings-1.1.0.xsd" xmlns="http://maven.apache.org/SETTINGS/1.1.0"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <servers>
    <server>
      <username>#username</username>
      <password>#password</password>
      <id>artifactory</id>
    </server>
  </servers>
  <profiles>
    <profile>
      <repositories>
        <repository>
            <id>artifactory</id>
            <name>ArtifactoryPRO-releases</name>
            <url>http://artifactory.crv4all.com:80/artifactory/arquillian-cube</url>
            <layout>default</layout>
        </repository>
      </repositories>
      <id>artifactory</id>
    </profile>
  </profiles>
  <activeProfiles>
    <activeProfile>artifactory</activeProfile>
  </activeProfiles>
</settings>

Run
mvn clean deploy -Dmaven.test.skip -DaltDeploymentRepository=artifactory::default::http://artifactory.crv4all.com:80/artifactory/arquillian-cube
