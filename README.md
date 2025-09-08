# **CI Build Pipeline for Spring3Hibernate using Azure DevOps**

# This project focuses on building a CI pipeline for the Spring3Hibernate application, a Java-based project developed with the Spring Framework and Hibernate ORM. The pipeline is implemented in Azure DevOps, leveraging its capabilities for code management, build automation, and artifact publishing.

## **Clone** - [Spring3Hibernate](https://github.com/opstree/spring3hibernate)


## CI Pipeline Design

### Pipeline Stages

#### **1. Source Stage**

`Fetch the application code from the version control system (Azure Repos Git or GitHub).`

#### **2. Build Stage**

`Compile Java code using Maven.`

`Package the application into a distributable artifact (.jar or .war).`
  
#### **3. Artifact Stage**

`Store the generated artifact in Azure DevOps as a pipeline artifact.`

`Make the artifact available for downstream processes such as deployment.`


## Tools and Frameworks Used

#### **1. Azure DevOps Pipelines – Orchestration of build and artifact workflows.**

#### **2. Java (OpenJDK 11) – Execution environment for the application.**

#### **3. Apache Maven – Dependency management and build automation.**

#### **4. MySQL (Optional) – Relational database for integration testing.**


## Pipeline Configuration

     trigger:
     - main  
     
     pool:
       name: 'azure deadpool'   
     
     steps:
     - task: Maven@3
       displayName: 'Build with Maven'
       inputs:
         mavenPomFile: 'pom.xml'
         goals: 'package'
         options: '-Dmaven.test.skip=true'
         javaHomeOption: 'Path'
         jdkDirectory: '/usr/lib/jvm/java-11-openjdk-amd64'
     
     - task: PublishBuildArtifacts@1
       displayName: 'Publish build artifacts'
       inputs:
         PathtoPublish: '$(System.DefaultWorkingDirectory)/target'
         ArtifactName: 'drop'
         publishLocation: 'Container'



<img width="1919" height="1131" alt="Screenshot from 2025-09-07 14-56-14" src="https://github.com/user-attachments/assets/3022d1be-cbc1-4874-9944-39436f800654" />


## Pipeline Features


#### **1. Automated Code Integration**

`Source code is automatically fetched from the repository upon changes, ensuring that the pipeline always works with the latest version of the application.`


#### **2. Build Automation with Maven**

`Maven standardizes the build process by managing dependencies, compiling source code, and packaging the application into distributable formats (.jar/.war).`
     

#### **3. Artifact Management**

`Compiled outputs are published as build artifacts, making them accessible for deployment in later stages without requiring a rebuild.`


#### **4. Pipeline-as-Code (YAML)**

`The YAML configuration approach enables version-controlled pipelines, ensuring consistency, traceability, and maintainability of the CI process.`


#### **5. Scalability and Extensibility**

`The pipeline can easily be extended to include additional stages such as automated testing, security scanning, and deployment to staging/production environments.`



<img width="1919" height="1131" alt="Screenshot from 2025-09-07 14-58-48" src="https://github.com/user-attachments/assets/ce81a364-f0f5-4bb7-8b91-71e0e25ad637" />


