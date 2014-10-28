# selenium-driver-binaries

Maven dependencies for binaries needed by [Selenium](http://www.seleniumhq.org/) for certain browsers

## What is it?

Some browsers require an external, binary file to help Selenium connect. For example, in order to use [Google Chrome](http://www.google.com/chrome/) on Windows, **chromedriver.exe** must be present.

The purpose of this project is to make these binaries available as a maven dependency, so that, instead of having to include them as part of your project, you can simply use maven to download them automatically.

## How do I use it?

We'll use Google Chrome as an example here.

### Download the appropriate executable

Add this to your **pom.xml**, in the build/plugins section:

```xml
    <plugin>
      <artifactId>maven-dependency-plugin</artifactId>
      <exeuction>
        <id>Get the chromedriver executable</id>
        <phase>generate-test-resources</phase>
        <goals>
          <goal>copy</goal>
        </goals>
        <configuration>
          <artifactItems>
            <artifactItem>
              <groupId>fr.fot</groupId>
              <artifactId>selenium-chromedriver-binary</artifactId>
              <version>2.11</version>
              <type>exe</type>
              <!-- Chrome comes in win32, mac32, linux32, linux64 -->
              <classifier>win32</classifier>
              <outputDirectory>${project.build.directory}</outputDirectory>
              <destFileName>chromedriver.exe</destFileName>
            </artifactItem>
          </artifactItems>
        </configuration>
      </execution>
    </plugin>
```

### (Optional) Set the system property for tests

*ChromeDriver* depends on a system property to find the executable. This build plugin will add it for all tests.

```xml
    <plugin>
      <artifactId>maven-surefire-plugin</artifactId>
      <configuration>
        <systemPropertyVariables>
          <webdriver.chrome.driver>${project.build.directory}/chromedriver.exe</webdriver.chrome.driver>
        </systemPropertyVariables>
      </configuration>
    </plugin>
```
