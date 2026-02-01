# CILabProject – Jenkins CI Assignment

## Project Overview
This project demonstrates the implementation of **Continuous Integration (CI)** using Jenkins. It includes:

- Freestyle and Multibranch Pipeline jobs
- Integration with GitHub source control
- Automated builds, testing, and notifications
- Plugin management for build tools, testing, and deployment

The goal is to show how CI improves code quality, reduces errors, and speeds up development cycles.

---

## Installation Guide

### 1. Prerequisites
- Java JDK 11+
- Jenkins LTS
- Git
- Apache Maven

### 2. Jenkins Installation
1. Download Jenkins from [https://www.jenkins.io/download/](https://www.jenkins.io/download/)
2. Install Jenkins on your system following the setup wizard.
3. During setup, install **recommended plugins**.
4. Create an **admin user** and configure the Jenkins URL.
5. Configure global tools:
   - Java JDK
   - Git
   - Maven

### 3. Plugin Installation
Install the following essential plugins via **Manage Jenkins → Manage Plugins → Available**:

- **Pipeline:** Pipeline, Stage View
- **SCM:** Git, GitHub
- **Build Tools:** Maven Integration, Gradle Plugin
- **Testing:** JUnit, TestNG
- **Notification:** Email Extension, Slack Notification
- **Deployment:** Publish Over SSH, Docker Pipeline

---

## User Manual

### 1. Project Structure
```CILabProject/
├── src/
│   ├── main/
│   │   ├── java/com/muj/ci/Calculator.java
│   │   └── resources/
│   └── test/
│       └── java/com/muj/ci/CalculatorTest.java
├── pom.xml
├── Jenkinsfile
├── docker/Dockerfile
├── scripts/
│   ├── build.sh
│   └── deploy.sh
└── README.md

```

### 2. Running the Jenkins Pipeline
1. Open **Jenkins dashboard → New Item → Multibranch Pipeline**.
2. Set the **Git repository URL** to this project.
3. Jenkins automatically discovers branches and runs the pipeline based on the `Jenkinsfile`.

**Pipeline stages include:**
- Checkout source code
- Build project using Maven
- Run unit tests using JUnit
- Generate test reports
> Check **console output** to verify success/failure of each stage.

### 3. Running Freestyle Job
1. Create a **Freestyle Project** in Jenkins.
2. Set **Source Code Management → Git**.
3. Add build steps to invoke top-level Maven targets:
```bash
clean test
```
### 4.Add post-build actions:
1. Archive artifacts 
2. Publish JUnit test result report

## Troubleshooting Guide

| Issue                           | Possible Cause                     | Solution                                        |
| ------------------------------- | ---------------------------------- | ----------------------------------------------- |
| Jenkins not starting            | Java not installed / wrong version | Install Java JDK 11+ and configure `JAVA_HOME`  |
| Git clone fails                 | Invalid credentials or URL         | Verify repository URL and Git credentials       |
| Build fails                     | Maven dependencies missing         | Run `mvn clean install` and check `pom.xml`     |
| JUnit tests not detected        | Incorrect test structure           | Ensure tests are under `src/test/java`          |
| Pipeline not detecting branches | Webhook not configured             | Configure GitHub webhook in repository settings |
