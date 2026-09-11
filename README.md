# DevOps Micro Site CI/CD Demo

## Overview

This project demonstrates a complete CI/CD implementation using GitHub Actions and GitHub Pages for a simple static micro site.

The objective of this project is to validate a typical software delivery workflow where code changes are automatically validated, tested, built and deployed following a pull request and merge process.

The solution includes:

- Pull Request validation
- Automated testing
- Automated build
- Artifact generation
- Continuous deployment
- Environment-based deployment controls
- GitHub Pages hosting

---

## Technology Stack

- HTML
- CSS
- JavaScript
- GitHub Actions
- GitHub Pages
- Node.js

---

## Repository Structure

```text
.
├── .github
│   └── workflows
│       └── deploy.yml
├── index.html
├── style.css
├── script.js
├── package.json
└── README.md
```

---

## CI/CD Workflow

The workflow is triggered during both validation and deployment stages.

### Validation Flow

```text
Feature Branch
      │
      ▼
Pull Request
      │
      ▼
GitHub Actions
      │
      ├── Checkout Code
      ├── Install Dependencies
      ├── Lint Validation
      ├── Automated Testing
      └── Build Verification
```

### Deployment Flow

```text
Merge to Main
      │
      ▼
GitHub Actions
      │
      ├── Checkout Code
      ├── Install Dependencies
      ├── Lint Validation
      ├── Automated Testing
      ├── Build Site
      ├── Upload Artifact
      └── Deploy to GitHub Pages
```

---

## Branching Strategy

The following branching approach is used:

```text
feature/*
    │
    ▼
Pull Request
    │
    ▼
Validation Pipeline
    │
    ▼
Merge to Main
    │
    ▼
Deployment Pipeline
    │
    ▼
GitHub Pages
```

This approach ensures that all code changes are validated before deployment.

---

## Workflow Features

### Pull Request Validation

The workflow automatically runs when a Pull Request is raised against the main branch.

Validation includes:

- Repository checkout
- Dependency installation
- Lint checks
- Automated tests
- Build validation

### Continuous Deployment

When changes are merged into the main branch:

- Build process executes
- Deployment artifact is generated
- Artifact is uploaded
- Site is deployed automatically to GitHub Pages

---

## Security Controls

The workflow follows the principle of least privilege.

```yaml
permissions:
  contents: read
  pages: write
  id-token: write
```

Benefits:

- Restricts unnecessary repository access
- Allows deployment to GitHub Pages
- Supports secure authentication

---

## Environment Controls

Deployment uses the GitHub Pages environment.

```yaml
environment:
  name: github-pages
```

Benefits:

- Deployment visibility
- Deployment history tracking
- Approval controls if required
- Audit trail of releases

---

## Build Process

The build stage creates a deployable static artifact.

Example:

```bash
npm run build
```

Output:

```text
dist/
├── index.html
├── style.css
└── script.js
```

The generated artifact is uploaded and deployed through GitHub Actions.

---

## Automated Validation

The pipeline performs the following validations:

### Lint Check

```bash
npm run lint
```

Purpose:

- Basic code quality validation
- Detect syntax issues early

### Automated Test

```bash
npm test
```

Purpose:

- Validate application functionality
- Prevent deployment of broken code

---

## Pipeline Validation Scenario

To verify pipeline controls, a failure scenario was intentionally tested.

### Test Failure Simulation

The test command was temporarily modified to return a non-zero exit code.

Example:

```json
"test": "exit 1"
```

Expected Result:

- Test stage failed
- Build stage did not execute
- Deployment was blocked

### Remediation

The test command was restored.

```json
"test": "echo Tests passed"
```

Result:

- Tests passed
- Build completed successfully
- Deployment resumed automatically

This exercise validated that deployment protection mechanisms were functioning correctly.

---

## Evidence of Successful Pipeline Execution

The following evidence demonstrates successful CI/CD implementation:

- Successful Pull Request validation
- Successful automated test execution
- Successful build execution
- Artifact upload confirmation
- Successful GitHub Pages deployment
- GitHub Pages environment deployment history
- Publicly accessible application URL

---

## Deployment URL

GitHub Pages Site:

```text
https://<github-username>.github.io/<repository-name>/
```

---

## Future Enhancements

Potential enhancements for enterprise environments:

- SonarQube integration
- Snyk security scanning
- Trivy container scanning
- Infrastructure as Code
- Terraform provisioning
- Kubernetes deployment
- ArgoCD GitOps integration
- Production approval gates
- Blue/Green deployment strategy
- Canary deployment strategy

---

## Conclusion

This project demonstrates a complete CI/CD workflow using GitHub Actions and GitHub Pages, incorporating automated validation, testing, artifact management and deployment controls. The implementation follows DevOps best practices and provides a foundation that can be extended for larger enterprise delivery pipelines.
