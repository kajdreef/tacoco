# tacoco

## Getting started...

1. get fresh tacoco.jar by typing

  mvn package
  
2. add tacoco.jar to local repo

  mvn install:install-file -Dfile=../tacoco.jar -DgroupId=tacoco -DartifactId=tacoco -Dversion=0.1 -Dpackaging=jar

3. add tacoco listener to surefire plugin
  ~~~xml
  <dependencies>
  ...
  <dependency>
    <groupId>tacoco</groupId>
		<artifactId>tacoco</artifactId>
		<version>0.1</version>
	  <scope>test</scope>
  </dependency>
  ...
  <dependencies>
  
  <build>
    <plugins>
    ...
      <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-surefire-plugin</artifactId>
      <version>2.18.1</version>
      <configuration>
        <properties>
          <property>
            <name>listener</name>
            <value>TacocoListener</value>
          </property>
        </properties>
      </configuration>
     </plugin>
    ...
    ~~~

## Running ExecDump utility to read the `jacoco.exec` file

0. Change the path of the jacoco.exec in pom.xml, where specified.
1. Use the following maven command on the command line: `mvn exec:java -Dexec.args="/path/to/your/jacoco.exec"`