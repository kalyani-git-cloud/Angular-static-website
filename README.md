# Angular Static Website CI/CD using Azure DevOps

## Project Overview

This project demonstrates a complete CI/CD implementation for an Angular static website using Azure DevOps and Azure Storage Static Website Hosting.

The objective of this project is to automate the build and deployment process across multiple environments (Development, Testing, Staging, and Production) using Azure DevOps YAML pipelines, environment approvals, and artifact-based deployments.

---

## Architecture

Developer (VS Code)
│
▼
Azure Repos / GitHub
│
▼
Build Pipeline
│
▼
Publish Artifact
│
▼
Release Pipeline
│
┌──────┼──────┬──────┐
▼      ▼      ▼      ▼
DEV    TEST   STAGE  PROD
│
▼
Azure Storage Static Website

---

## Technologies Used

### Frontend

* Angular
* TypeScript
* HTML
* CSS

### DevOps

* Azure DevOps
* Azure Pipelines (YAML)
* Azure Artifacts
* Multi-Stage Deployment
* Environment Approvals
* Release Promotion Strategy

### Azure Services

* Azure Storage Account
* Static Website Hosting
* Azure Resource Groups
* Azure Service Connections

### Development Tools

* Visual Studio Code
* Git
* GitHub

---

## Project Structure

```text
hello-world-app/
│
├── src/
├── public/
├── angular.json
├── package.json
├── azure-pipelines-build.yml
├── azure-pipelines-release.yml
└── README.md
```

---

## CI Pipeline (Build Pipeline)

### Purpose

The build pipeline automatically:

1. Retrieves source code.
2. Installs Node.js dependencies.
3. Builds Angular application.
4. Generates production-ready files.
5. Publishes build artifacts.

### Build Process

```bash
npm install
npm run build
```

### Output

The build output is generated inside:

```text
dist/
```

and published as a pipeline artifact.

---

## CD Pipeline (Release Pipeline)

### Purpose

The release pipeline deploys the same artifact to multiple environments.

Environments:

* Development
* Testing
* Staging
* Production

This ensures consistency across all environments.

---

## Deployment Strategy

### DEV

Automatically deploys the latest build artifact.

Purpose:

* Initial validation
* Developer testing

### TEST

Deploys after DEV validation.

Purpose:

* Functional testing
* QA validation

### STAGE

Deploys after TEST approval.

Purpose:

* Pre-production validation
* Final verification

### PROD

Deploys only after manual approval.

Purpose:

* Production release

---

## Environment Approval Gates

Manual approvals are configured before critical environments.

Benefits:

* Prevent accidental deployments
* Increase deployment control
* Improve release governance

---

## Artifact-Based Deployment

The application is built only once.

Build Artifact:

```text
AngularBuild
```

The same artifact is promoted through:

DEV → TEST → STAGE → PROD

Benefits:

* Consistent deployments
* Reduced deployment risk
* Faster releases

---

## Azure Storage Static Website Hosting

The Angular application is hosted using:

Azure Storage Account Static Website Feature

Deployment command:

```bash
az storage blob upload-batch \
--destination '$web'
```

Purpose:

Uploads the generated Angular files to the Azure Storage static website container.

---

## Key DevOps Concepts Demonstrated

### Continuous Integration (CI)

Automatically builds code whenever changes are committed.

### Continuous Delivery (CD)

Automates deployment across environments.

### Infrastructure Reusability

Environment-specific variables are managed using YAML templates.

### Release Promotion

Same artifact promoted across environments.

### Deployment Governance

Manual approvals implemented for controlled production releases.

---

## Skills Demonstrated

* Azure DevOps Pipelines
* YAML Pipelines
* Azure Storage Static Websites
* CI/CD Implementation
* Multi-Stage Deployments
* Environment Approvals
* Artifact Management
* Azure Service Connections
* Git Version Control
* VS Code Development

---

## Project Outcome

Successfully implemented an enterprise-style CI/CD pipeline for an Angular static website using Azure DevOps.

The solution automates application build, artifact generation, multi-environment deployment, approval workflows, and production release management while following DevOps best practices.
