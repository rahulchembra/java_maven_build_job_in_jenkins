# Hello Java Maven – Jenkins CI/CD Pipeline

This project is a simple Java application built using **Maven** and automated with **Jenkins**. It demonstrates how to set up multiple Jenkins jobs (validate, compile, package) and chain them together into a pipeline.

## 📂 Project Structure
```
java_maven_build_job_in_jenkins
├── pom.xml                
├── src/
│   └── main/
│       └── java/
│           └── HelloWorld.java
├── jenkins_jobs/         
│   ├── validate.xml
│   ├── compile.xml
│   └── package.xml
└── screenshots/       

## 🛠️ Tools & Technologies Used
- **Java** – Programming language for application
- **Maven** – Build automation tool
- **Jenkins** – CI/CD automation server
- **Git & GitHub** – Version control
- **Ubuntu** – Build & execution environment

## 🔄 Jenkins Pipeline Workflow
The pipeline is split into **three jobs**:

1. **validate** – Runs Maven `validate` goal to ensure the project is correctly set up.
2. **compile** – Runs Maven `compile` goal to compile the Java source code.
3. **package** – Runs Maven `package` goal to create the JAR file in `target/` folder.

Jobs are **triggered in sequence**:
```
validate → compile → package
```
This is achieved by configuring **Post-build Actions** in each job:
- `validate` job → triggers `compile` job after success
- `compile` job → triggers `package` job after success

## 📦 Output in Jenkins
After the pipeline runs successfully, the packaged JAR file is located in:
```
/var/lib/jenkins/workspace/<job_name>/target/


