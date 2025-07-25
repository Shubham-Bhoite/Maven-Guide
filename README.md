# <h1 align="center">⚙️ Maven-Guide</h1>

## 📘 Introduction :
Maven Guide is a beginner-friendly resource to help you understand and use Apache Maven, a powerful build automation tool used primarily for Java projects. This guide covers the basics of Maven, including how to set it up, create and manage projects, handle dependencies, and run builds efficiently.
Whether you're a student, fresher, or developer new to Maven, this guide will help you get started quickly and confidently.


## What is Maven?
- Maven is a build automation tool primarily used for Java projects. It addresses two main aspects of building software: dependency management and project build lifecycle management.
- It simplifies the build process by managing dependencies, compiling source code, packaging it into a deliverable (such as a JAR file), and deploying it to a repository.
- Maven is based on the concept of a Project Object Model (POM), which is a central piece of information that manages a project’s build, reporting, and documentation.

## History and Evolution of Maven :
- Maven was developed by the Apache Software Foundation and released in 2004.
- It was created to address the problems with Apache Ant, a popular build tool at the time. Maven was designed to simplify the build process, provide a uniform build system, and offer project information that could be shared among developers.
- Over the years, Maven has become one of the most widely used build tools in the Java ecosystem.

## Installing Maven
### Prerequisites:
- Ensure that Java is installed on the machine. Maven requires Java to run. The trainees should have the Java Development Kit (JDK) installed and the JAVA_HOME environment variable set.

### Steps to Install Maven:

1.Download Maven:
- Go to the Maven official download page.
- Download the latest binary zip archive or tar.gz file.
  
2.Extract the Archive:
- Extract the downloaded archive to a directory of your choice (e.g. C:\\Program Files\\Apache\\maven on Windows or /usr/local/apache-maven on macOS/Linux).
  
3.Set Environment Variables:
- Windows:
1. Right-click on 'This PC' or 'My Computer', then go to Properties → Advanced System Settings → Environment Variables.
2. Add a new system variable named MAVEN_HOME pointing to the Maven directory.
3. Append the bin directory of Maven to the Path system variable: C:\\Program Files\\Apache\\maven\\bin.

   
- macOS/Linux:
1. Open .bash_profile or .zshrc file in your home directory and add:

       export MAVEN_HOME=/usr/local/apache-maven
       export PATH=$MAVEN_HOME/bin:$PATH

2. Run source ~/.bash_profile or source ~/.zshrc to apply the changes.
   

4.Verify Installation:
- Open a terminal or command prompt and type mvn -version.
- You should see the Maven version information along with Java details if Maven is correctly installed.


## Setting up Maven in IDEs ==>
- ### IntelliJ IDEA:

  1.Maven Integration :
  - IntelliJ IDEA has Maven integration built-in, so no additional setup is required.
  - When creating a new project, you can select Maven as the project type, and IntelliJ will automatically generate the pom.xml file and manage the project structure.
 
  2.Importing a Maven Project:
  - If you already have a Maven project, you can import it by opening IntelliJ and selecting File → Open, then navigating to the pom.xml file of your project.

  3.Maven Tool Window:
  - IntelliJ provides a Maven tool window where you can run Maven goals, view the lifecycle, and manage dependencies directly from the IDE.
 
- ### Eclipse :

  1.Installing the Maven Plugin:
  - Eclipse requires the m2e plugin for Maven integration, though many versions of Eclipse come with this plugin pre-installed.
  - To install it manually: Help → Eclipse Marketplace → Search for "m2e" → Install.
 
  2.Creating a Maven Project:
  -     Go to File → New → Project → Maven → Maven Project.
  - Follow the wizard to set up your project, specifying details like GroupId, ArtifactId, and packaging type.
 
  3.Importing a Maven Project:
  - If you have an existing Maven project, import it by selecting File → Import → Maven → Existing Maven Projects, then point to the directory containing the pom.xml.

  4.Maven Integration:
  - Eclipse provides a "Maven" perspective that allows you to run Maven commands, manage dependencies, and configure the build lifecycle from within the IDE.

## Understanding the .m2 Directory and settings.xml ==>
### The .m2 Directory: 
- Located in the user's home directory (e.g., C:\\Users\\YourName\\.m2 on Windows or /home/YourName/.m2 on macOS/Linux).
- Contains the repository folder where Maven stores downloaded dependencies. This is known as the local repository.
- You can delete this folder if you want to force Maven to re-download dependencies, but usually, Maven manages it automatically.

### settings.xml File:
- Located in the .m2 directory. This file allows you to customize the behavior of Maven globally across all projects.
- Common configurations include:
  - Mirror configuration to point Maven to a specific repository.
  - Proxy settings if you're behind a firewall or using a corporate network.
  - Local repository location customization.
  - Example settings.xml==>
  -     <settings>
        <mirrors>
        <mirror>
            <id>central</id>
            <mirrorOf>central</mirrorOf>
            <url><http://mycompany.com/maven2></url>
        </mirror>
        </mirrors>
        <proxies>
        <proxy>
            <id>example-proxy</id>
            <active>true</active>
            <protocol>http</protocol>
            <host>proxy.mycompany.com</host>
            <port>8080</port>
        </proxy>
        </proxies>
        </settings>



## Project Object Model (POM) :
- The POM (Project Object Model) is the core of a Maven project. Understanding the POM file is essential because it contains all the configuration details for a Maven project.


### Structure of a pom.xml File :
- The pom.xml file is an XML file that contains information about the project and configuration details used by Maven to build the project.
- Here’s a basic structure of a pom.xml file==>
        
      <project xmlns="<http://maven.apache.org/POM/4.0.0>"
         xmlns:xsi="<http://www.w3.org/2001/XMLSchema-instance>"
         xsi:schemaLocation="<http://maven.apache.org/POM/4.0.0>
                             <http://maven.apache.org/xsd/maven-4.0.0.xsd>">
      <modelVersion>4.0.0</modelVersion>

      <groupId>com.example</groupId>
      <artifactId>my-app</artifactId>
      <version>1.0-SNAPSHOT</version>
      <packaging>jar</packaging>

      <name>My App</name>
      <url><http://maven.apache.org></url>

      <dependencies>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
            <scope>test</scope>
        </dependency>
      </dependencies>

      <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
            </plugin>
        </plugins>
      </build>
      </project>


### Key Elements in POM ==>
1.modelVersion:
- This specifies the version of the POM model being used. Currently, 4.0.0 is the default and most widely used version.

2.groupId:
- The groupId uniquely identifies your project across all projects. Typically, it follows the reverse domain name convention (e.g., com.example).

3.artifactId:
- The artifactId is the name of the jar without the version. It is the name of the project.

4.version:
- The version is the project’s current version. Maven uses this version to distinguish between different versions of the same project.
- Versions can be specific like 1.0.0, or they can include SNAPSHOT, which indicates a version in development.

5.packaging:
- The type of artifact this project produces. Common packaging types are jar, war, pom, etc.
- If omitted, jar is assumed by default.

6.name and url:
- These are optional elements used to provide a human-readable name and project URL.

7.dependencies:
- The dependencies section lists all the external libraries your project depends on. Maven will download these libraries automatically from the central repository or other specified repositories.

8.build:
- The build section is used to specify how the project should be built. This includes specifying plugins, custom build directories, resources, etc.


### Dependencies and Dependency Management ==>
#### Dependencies:
- Dependencies are external libraries that your project needs to work. You specify these in the dependencies section of the POM.
- Maven automatically downloads the specified versions of dependencies and any transitive dependencies they require.
- Example ==>

      <dependencies>
        <dependency>
          <groupId>org.springframework.boot</groupId>
          <artifactId>spring-boot-starter-web</artifactId>
          <version>2.5.4</version>
        </dependency>
      </dependencies>
#### Transitive Dependencies:
- Maven resolves transitive dependencies automatically. For example, if your project depends on A, and A depends on B, Maven will include B as a dependency in your project.


### Maven Dependency Scopes and Profiles ==>
#### 1. Dependency Scopes
- Maven provides several scopes for dependencies, each determining at what phase of the build process the dependency is available and whether it is included in the final artifact (e.g., a JAR or WAR file). Understanding these scopes is crucial for managing project dependencies effectively.
- Here’s a detailed explanation of each scope, with examples:
##### a. compile Scope
- Availability: The dependency is available in all phases of the build lifecycle, including compilation, testing, and packaging.
- Default Scope: If no scope is specified, Maven uses compile by default.

#### b. provided Scope
- Availability: The dependency is available at compile-time but is not included in the final artifact.
- Typical Use: Used for dependencies that are provided by the runtime environment, such as servlet APIs provided by an application server.

#### c. runtime Scope
- Availability: The dependency is not required for compilation but is needed during runtime, including execution and tests.
- Typical Use: Used for dependencies that are needed only at runtime, like JDBC drivers.

#### d. test Scope
- Availability: The dependency is available only for the test compilation and execution phases.
- Typical Use: Used for libraries that are required only for testing, such as JUnit or Mockito.

#### e. system Scope
- Availability: The dependency is available for compilation and testing but must be explicitly provided by the developer on the system.
- Typical Use: Used rarely when the dependency is not available in any remote repository and must be provided locally.
- Important: You must explicitly provide the path to the JAR file using the <systemPath> element.

### Maven Profiles ==>
- Maven profiles allow you to customize the build process for different environments or situations. A profile can modify the default behavior by adding, removing, or overriding certain parts of the POM, such as dependencies, plugins, properties, etc.

#### How Profiles Work :
- Activation: Profiles can be activated explicitly using the P flag in the Maven command or automatically based on certain conditions (e.g., OS type, JDK version, environment variables).
- Scope: Profiles can modify the build process for a particular environment, such as development, testing, or production.


### Maven Build Lifecycle
The Maven build lifecycle is a sequence of phases that define the order in which tasks are executed during the build process of a Maven project. Maven has three built-in build lifecycles:

#### 1. Default Lifecycle (Build) :
This is the main lifecycle that handles project deployment. It consists of 23 phases, the most important of which are:
- 1.validate: Validates the project is correct and all necessary information is available.
- 2.compile: Compiles the source code of the project.
- 3.test: Runs the tests using a suitable unit testing framework (like JUnit).
- 4.package: Packages the compiled code into a distributable format, such as a JAR or WAR file.
- 5.verify: Runs any checks to verify the package is valid and meets quality criteria.
- 6.install: Installs the package into the local repository, for use as a dependency in other projects locally.
- 7.deploy: Copies the final package to the remote repository for sharing with other developers and projects.

#### 2. Clean Lifecycle :
This lifecycle is used to clean up artifacts created by the previous build. It consists of three phases:
- pre-clean: Executes processes needed before the actual project cleaning.
- clean: Removes files generated during the previous build.
- post-clean: Executes processes needed after the project cleaning.

#### 3. Site Lifecycle :
This lifecycle is used to create the project's site documentation. It consists of four phases:
- pre-site: Executes processes needed before the actual project site generation.
- site: Generates the project's site documentation.
- post-site: Executes processes needed after the site generation, preparing for site deployment.
- site-deploy: Deploys the generated site to a web server.

## Maven Repositories :
Maven repositories are a central part of the Maven build system. They are where Maven stores and retrieves project dependencies, plugins, and other artifacts. Understanding how repositories work and how to manage them is crucial for effectively using Maven.

### Types of Maven Repositories ==>
Maven supports three types of repositories:

### 1.Local Repository:
- The local repository is a directory on your computer where Maven stores downloaded dependencies, plugins, and other artifacts.
- When you build a Maven project, Maven first checks the local repository to see if the required dependencies are already available. If they are, Maven uses them; if not, Maven downloads them from a remote repository (such as the central repository) and stores them locally.
- The default location of the local repository is ~/.m2/repository (on Unix-based systems) or C:\\Users\\YourUsername\\.m2\\repository (on Windows).
- You can configure the location of the local repository in the settings.xml file==>

      <settings>
         <localRepository>C:/path/to/your/local/repo</localRepository>
      </settings>
### 2.Central Repository:
- The central repository is a global, publicly available repository hosted by the Maven project. It contains a vast collection of open-source libraries, plugins, and other project artifacts.
- The central repository is the default source from which Maven downloads dependencies if they are not found in the local repository.
- Maven automatically connects to the central repository when you request a dependency that is not available locally.

### 3.Remote Repository:
- A remote repository is any repository that is hosted on a web server other than the central repository. Organizations often maintain their own remote repositories to store proprietary artifacts, plugins, or third-party libraries that are not available in the central repository.
- You can configure Maven to use a remote repository by adding it to your pom.xml or settings.xml file.
- Example in pom.xml ==>

      <repositories>
       <repository>
        <id>my-company-repo</id>
        <url><http://repository.mycompany.com/maven2></url>
       </repository>
      </repositories>

### How Maven Resolves Dependencies ?
Maven follows a specific order to resolve dependencies:
- Local Repository: Maven checks the local repository first. If the dependency is found, Maven uses it.
- Remote Repositories: If the dependency is not found in the local repository, Maven checks any configured remote repositories.
- Central Repository: If the dependency is not found in any remote repositories, Maven checks the central repository.
- Fail: If Maven cannot find the dependency in any repository, the build fails with an error.

### Dependency Management in Multi-Module Projects :-
In multi-module projects, you often have a parent POM that defines dependencies for all modules. Maven provides a <dependencyManagement> section that allows you to centrally manage dependency versions across multiple modules.

#### Using <dependencyManagement> in the Parent POM ==>

    <project>
    <groupId>com.example</groupId>
    <artifactId>parent-project</artifactId>
    <version>1.0.0</version>
    <packaging>pom</packaging>

    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>org.springframework</groupId>
                <artifactId>spring-core</artifactId>
                <version>5.3.9</version>
            </dependency>
            <dependency>
                <groupId>org.slf4j</groupId>
                <artifactId>slf4j-api</artifactId>
                <version>1.7.30</version>
            </dependency>
        </dependencies>
    </dependencyManagement>
    
- Explanation: Dependencies defined in <dependencyManagement> are not automatically included in the child modules. Instead, they provide a version and scope template that child modules can use.


### Child Module POM==>

    <project>
     <parent>
        <groupId>com.example</groupId>
        <artifactId>parent-project</artifactId>
        <version>1.0.0</version>
     </parent>

    <artifactId>module-a</artifactId>

    <dependencies>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-core</artifactId>
        </dependency>
    </dependencies>
    </project>

- Explanation: The child module inherits the version and scope of spring-core from the parent POM, thanks to the <dependencyManagement> section.

### Excluding Unwanted Transitive Dependencies :
- Sometimes, you might want to exclude a transitive dependency that is brought in by one of your dependencies but is not needed by your project.

#### Example of Excluding Transitive Dependencies==>

    <dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
    <version>2.5.4</version>
    <exclusions>
        <exclusion>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-tomcat</artifactId>
        </exclusion>
    </exclusions>
    </dependency>

- Explanation: This configuration excludes the spring-boot-starter-tomcat dependency, which might be useful if you’re using a different server (e.g., Jetty) and don’t want Tomcat libraries included.

### Managing Conflicts with Dependency Mediation :
- When multiple versions of the same dependency are included via transitive dependencies, Maven uses a process called "dependency mediation" to determine which version to use. Maven usually selects the nearest definition (i.e., the version specified in the pom.xml or the version closest to the root of the dependency tree).
  
#### Example of Dependency Conflict:
- If A depends on B:1.0 and C depends on B:2.0, and both A and C are included in your project, Maven will choose one version of B.
- You can control which version is selected by explicitly declaring the desired version in your pom.xml.
  
      <dependency>
         <groupId>com.example</groupId>
         <artifactId>B</artifactId>
         <version>2.0</version>
      </dependency>
- Explanation: By explicitly declaring the version of B, you override the transitive versions and ensure that B:2.0 is used.


### Best Practices for Dependency Management

