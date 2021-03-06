# immudb Java Examples

This sample uses the [official immudb Java client].

[Official immudb Java client]: https://github.com/codenotary/immudb4j

`immudb` must be already running. Follow instructions to download and run it at https://immudb.io/docs/quickstart.html


### Configuring Maven to use GitHub Packages

`immudb4j` package is published at [GitHub Packages] and it requires authentication to download dependencies.

[GitHub Packages]: https://docs.github.com/en/packages

Please refer to GitHub documentation for a detailed explanation about [Authenticating with a personal access token]. But basically you will need to do two things in order to download a Maven dependency hosted in `GitHub Packages`, authenticate and add the GitHub repository into your Maven settings:

[Authenticating with a personal access token]: https://docs.github.com/en/packages/using-github-packages-with-your-projects-ecosystem/configuring-apache-maven-for-use-with-github-packages

1. Create GitHub personal access token: https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token

2. Configure Maven to use GitHub Packages

Following info needs to be included into your `~/.m2/settings.xml` file. You will need to place your GitHub username and personal token in the `github` server.

```xml
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
                      http://maven.apache.org/xsd/settings-1.0.0.xsd">

  <activeProfiles>
    <activeProfile>github</activeProfile>
  </activeProfiles>

  <profiles>
    <profile>
      <id>github</id>
      <repositories>
        <repository>
          <id>central</id>
          <url>https://repo1.maven.org/maven2</url>
          <releases><enabled>true</enabled></releases>
          <snapshots><enabled>true</enabled></snapshots>
        </repository>
        <repository>
          <id>github</id>
          <name>GitHub codenotary/immudb4j Apache Maven Packages</name>
          <url>https://maven.pkg.github.com/codenotary/immudb4j</url>
        </repository>
      </repositories>
    </profile>
  </profiles>

  <servers>
    <server>
      <id>github</id>
      <username>USERNAME</username>
      <password>TOKEN</password>
    </server>
  </servers>
</settings>
```
