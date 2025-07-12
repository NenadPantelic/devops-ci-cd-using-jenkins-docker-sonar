# DevOps - CI/CD with Jenkins, Docker and Sonar

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
