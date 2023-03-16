# 1. scalafmt

## 1.1 Definition

Scalastyle examines your Scala code and indicates potential problems with it.
Based on rules, it examines your Scala code and points out potential problems with it. 

The latest stable version of Scalastyle is 1.0.0 for Scala 2.10/2.11/2.12.

There are 69 rules that are currently implemented

__Pros__:

- Flexible
- Complete documentation
- Configurable & Possibility to add your own rules
- Several ways to use it: Maven plugin, SBT plugin, command line, Intellij...

## 1.2 Configuration

scalastyle:check performs a violation check against the scalastyle config file to see if there are any violations. It counts the number of violations found and displays it on the console if verbose is enabled.

The latest stable version of Scalastyle is 1.0.0 for Scala 2.10/2.11/2.12. See the Release Notes

There are several ways of using it:

- Maven Plugin
- Eclipse plugin (for 4.2 Juno and 4.3 Kepler and 4.4 Luna)
- SBT plugin
- Command line
- Gradle Plugin
- Intellij - You can enable scalastyle in Intellij by selecting Settings->Editor->Inspections, then searching for Scala style inspections.
- Codacy - You get out-of-the-box analysis on your git repositories.
- Git pre-commit hook
And you’ll need a configuration. If you have your own custom rules, then see custom rules http://www.scalastyle.org/custom-rules.html

For the list of possible rules, see Implemented Rules. http://www.scalastyle.org/rules-1.0.0.html

### Usage - scalastyle as part of build cycle

 ```<build>
        <plugins> 
          ...
          <plugin>
            <groupId>org.scalastyle</groupId>
            <artifactId>scalastyle-maven-plugin</artifactId>
            <version>1.0.0</version>
            <configuration>
              <verbose>false</verbose>
              <failOnViolation>true</failOnViolation>
              <includeTestSourceDirectory>true</includeTestSourceDirectory>
              <failOnWarning>false</failOnWarning>
              <sourceDirectory>${project.basedir}/src/main/scala</sourceDirectory>
              <testSourceDirectory>${project.basedir}/src/test/scala</testSourceDirectory>
              <configLocation>${project.basedir}/lib/scalastyle_config.xml</configLocation>
              <outputFile>${project.basedir}/scalastyle-output.xml</outputFile>
              <outputEncoding>UTF-8</outputEncoding>
            </configuration>
            <executions>
              <execution>
                <goals>
                  <goal>check</goal>
                </goals>
              </execution>
            </executions>
          </plugin>
            ...
        </plugins>
    </build>
  ```




You can also specify multiple source directories if necessary. Replace the <sourceDirectory> element with <sourceDirectories>:

```
 <sourceDirectories>
      <dir>${project.basedir}/src/main/scala</dir>
      <dir>${project.basedir}/src/main/generated-scala</dir>
    </sourceDirectories>
```

and similarly for <testSourceDirectory> & <testSourceDirectories>.

