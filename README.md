# DevOps - CI/CD with Jenkins, Docker and Sonar

Simple examples that demonstrate setting up CI/CD pipelines with Jenkins, Docker, and SonarQube. It automates build, test, and deployment processes while ensuring code quality through static analysis with SonarQube.

## DevOps

- Development + Operations
- the combination of best practices and tools which is designed to increase an organization/company's ability to deliver applications/projects and services faster than traditional software development processes
- under this model, the development and operations teams work together across the entire software application lifecycle, from development and test through deployment to operations
- Benefits:
  - speed; rapid delivery
  - reliability
  - improved collaboration
  - security
- DevOps lifecycle:

  1. **planning** the next iteration of the product's development
  2. **building** the code
  3. **testing and deploying** to the production environment
  4. **delivering** product updates
  5. **monitoring and logging** software performance
  6. **gathering** customer feedback

- Lifecycle:

1. continuous development
2. continuous integration
3. continuous testing
4. continuous monitoring
5. continuous feedback
6. continuous deployment
7. continuous operations

### Continuous integration, deployment & delivery

- the project starts with the functional requirements, defining the project details, needed resources (time, staff...) which is gathered from a client
- the company establishes a team of developers that is going to work on that project
- the source code is managed with the VCS (e.g. git) and stored on GitHub -> continuous development
- continuous integration:
  - build the code/packages - Maven, npm, Python, Go...
  - take care of the code quaility (build can be checked with Sonarqube)
  - built artifacts can be stored in Nexus/JFrog repositories
- the code is deployed to staging
  - deploy to test environment
  - run integration tests, load tests...
- developed software can be tested continuously for bugs using tools like Selenium, TestNG... -> continuous testing
- customer feedback to improve the working of s/w product and release new version based on the response -> continuous feedback
- after staging, we deploy to production environment
- continuously monitor each functionality like server not being reachable or low memory -> continuous monitoring
  - tools like ELK, Grafana, Prometheus, Nagios... are used here

NOTE: SSH settings are defined in `/etc/ssh/sshd_config`; `systectl restart sshd`

- once key pair is generated, copy the public key into `/root/.ssh/authorized_keys`
- to achieve passwordless authentication from a Linux client to an Ubuntu server, we have to:
  - generate an SSH key pair on the Linux client
  - copy the public key to the Ubuntu serve's `~/.ssh/authorized_keys` file
  - configure SSH server on the Ubuntu server to allow key-based authentication

### User management

- `id` - get the user identification
- create a user: `useradd <user-name>` -> e.g. `useradd nenadp`
- set the user password: `passwd <user-name>`

## Maven

- Apache Maven is a software project management and comprehension tool which based on the concept of a project object model (POM) manages project's build, reporting and documentation from a central piece of information
- POM is maintained by a dev team
- for the person building a project, this means that it is only necessary to learn a small set of commands to build any Maven project, and the POM will ensure they get the results they desired

### Maven lifecycle

- Three built-in build lifecycles:

  - the **default** lifecycle handles your project deployment
  - the **clean** lifecycle handles project cleaning
  - the **site** lifecycle handles the creation of your project's website

- 7 phases of the default lifecycle

1. validate - validate the project is correct and all necessary information is available
2. compile - compile the source code of the project
3. test - test the compiled source code using a suitable test framework. The tests should not require the code be packaged or deployed
4. package - take the compiled code and package it in its distributable format, such as JAR
5. verify - run any checks on results of integration tests to ensure quality criteria are met
6. install - install the package into the local repository, for use as a dependency in other projects locally
7. deploy - done in the buold environment, copies the final package to the remote repository for sharing with other developers and projects

- there are 3 types of repositories:

1. Local - `$HOME/.m2/repository`
2. Remote/Private - Nexus/JFrog
3. Central/Public -> Public from Maven website

- when a dependency is needed, it will search it in this order (dependencies are downloaded to the local repository)
- if POM file is not changed, `mvn clean package` will run very fast and archive file will be the same
- package will also include previous 3 steps (validate + compile + test)
