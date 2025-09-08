# CI Build Pipeline for Spring3Hibernate using Azure DevOps

## In this project, we outline the creation of a CI build pipeline for the Spring3Hibernate project, a Java-based application built using the Spring Framework and Hibernate ORM. The CI pipeline is implemented in Azure DevOps, which provides end-to-end DevOps capabilities including code management, build automation, and artifact storage.


## CI Pipeline Design

### Pipeline Stages

**1. Source Stage**

     Fetch the application code from the version control system (Azure Repos Git or GitHub).

**2. Build Stage**

    Compile Java code using Maven.

    Package the application into a distributable artifact (.jar or .war).
  
**3. Artifact Stage**

    Store the generated artifact in Azure DevOps as a pipeline artifact.

    Make the artifact available for downstream processes such as deployment.


## Tools and Frameworks Used

**1. Azure DevOps Pipelines – Orchestration of build and artifact workflows.**

**2. Java (OpenJDK 11) – Execution environment for the application.**

**3. Apache Maven – Dependency management and build automation.**

**4. MySQL (Optional) – Relational database for integration testing.**


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

