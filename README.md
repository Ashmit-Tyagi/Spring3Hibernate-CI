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
