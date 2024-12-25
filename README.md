# Azure YouTube Clone Website

This repository contains the source code and deployment configuration for a YouTube clone website. The project demonstrates end-to-end implementation of a modern web application hosted on Azure App Services with a fully automated CI/CD pipeline.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Features](#features)
3. [Technologies Used](#technologies-used)
4. [Getting Started](#getting-started)
    - [Prerequisites](#prerequisites)
    - [Setup Instructions](#setup-instructions)
5. [CI/CD Implementation](#cicd-implementation)
    - [Azure Build Pipeline (CI)](#azure-build-pipeline-ci)
    - [Azure Release Pipeline (CD)](#azure-release-pipeline-cd)
6. [Deployment Slots and Blue-Green Deployment](#deployment-slots-and-blue-green-deployment)
7. [Testing and Updates](#testing-and-updates)
8. [Screenshots](#screenshots)
9. [Conclusion](#conclusion)

---

## Introduction

This project showcases a scalable YouTube clone application developed using Angular. The application is hosted on Azure App Services, leveraging Azure DevOps pipelines for Continuous Integration (CI) and Continuous Deployment (CD). The project follows industry best practices, including Blue-Green deployment for seamless updates and automated testing workflows.

---

## Features

- **Frontend Framework**: Built with React for a responsive and dynamic UI.
- **CI/CD Automation**: Full automation of build, test, and deploy stages.
- **Azure Hosting**: Deployed on Azure App Services.
- **Blue-Green Deployment**: Safe rollout of updates using deployment slots.

---

## Technologies Used

- **React.js**: Frontend framework
- **Azure Repos (Git)**: Source code management
- **Azure Build Pipeline (CI)**: Automates build and test processes
- **Azure Release Pipeline (CD)**: Automates deployment stages
- **Azure App Service**: Hosting platform
- **GitHub**: Version control and repository hosting

---

## Getting Started

### Prerequisites

Ensure you have the following installed:

- Node.js and npm
- Azure CLI
- Git

Additionally, an Azure DevOps organization is required to set up pipelines.

### Setup Instructions

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/azure-youtube-clone.git
   cd azure-youtube-clone
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Build the application:
   ```bash
   ng build --prod
   ```

---

## CI/CD Implementation

### Azure Build Pipeline (CI)

1. Navigate to your Azure DevOps project.
2. Create a new YAML pipeline and link it to your repository.
3. Use the following YAML configuration:

    ```yaml
    trigger:
      - main

    pool:
      vmImage: 'ubuntu-latest'

    steps:
      - task: UseNode@2
        inputs:
          version: '16.x'

      - script: |
          npm install
          npm run build -- --prod
        displayName: 'Build Angular App'

      - task: PublishBuildArtifacts@1
        inputs:
          pathToPublish: 'dist/'
          artifactName: 'drop'
          publishLocation: 'Container'
    ```

4. Save and run the pipeline.

### Azure Release Pipeline (CD)

1. Go to **Releases** in Azure DevOps and create a new pipeline.
2. Add a stage for deployment to Azure App Services.
3. Configure the pipeline to fetch artifacts from the build pipeline.
4. Define deployment tasks:

    - Deploy to Azure App Service.
    - Configure environment variables if needed.

5. Set up Continuous Deployment triggers.

---

## Deployment Slots and Blue-Green Deployment

1. Enable deployment slots in Azure App Service.
2. Create a `staging` slot for Blue-Green deployment.
3. Modify the release pipeline to deploy first to the `staging` slot.
4. Test the deployment in `staging` and then swap to the `production` slot.

---

## Testing and Updates

- Test each CI/CD step by making small changes in the codebase.
- Update pipelines to ensure seamless integration and deployment.
- Use Azure Monitor for error tracking and performance monitoring.

---

## Screenshots

Include screenshots for the following:

1. **Azure Build Pipeline Configuration**
2. **Azure Release Pipeline Configuration**
3. **App Service Deployment Slots**
4. **Running Application**

---

## Conclusion

This project demonstrates a professional-grade implementation of a YouTube clone application hosted on Azure with robust CI/CD pipelines. By leveraging Azure DevOps and deployment slots, it ensures reliable and seamless application delivery.

