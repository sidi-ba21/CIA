# CI/CD Pipeline Documentation

## Overview
This CI/CD pipeline is designed to build Docker images for the backend and frontend, scan them for vulnerabilities using Trivy, check for high or critical vulnerabilities using Dependabot and CodeQL, and decide on deployment based on the scan results.

## Components
- **Trivy**: A vulnerability scanner for Docker images.
- **Dependabot**: A tool that automatically keeps your dependencies up to date.
- **CodeQL**: A tool for code analysis and security scanning.
- **GitHub Actions**: The CI/CD platform used to automate the pipeline.

## Pipeline Workflow
The workflow consists of several jobs:

- **Build**: Builds the Docker images.
- **Scan**: Scans the Docker images for vulnerabilities using Trivy.
- **Check Dependabot Alerts**: Checks for high or critical vulnerabilities reported by Dependabot.
- **Check CodeQL Alerts**: Checks for high or critical vulnerabilities reported by CodeQL.
- **Deploy**: Decides whether to deploy based on the scan results.

## Explanation of Each Job

### Build Job:
- Checks out the code.
- Sets up Docker Buildx.
- Caches Docker layers.
- Builds backend and frontend Docker images.
- Saves Docker images as files and uploads them as artifacts.

### Scan Job:
- Downloads and loads Docker images.
- Installs Trivy.
- Scans backend and frontend images with Trivy and saves the reports.
- Uploads Trivy reports as artifacts.
- Checks for critical vulnerabilities in the Trivy reports.

### Check Dependabot Alerts Job:
- Fetches Dependabot alerts using the GitHub API.
- Prints the fetched alerts for debugging.
- Checks for high or critical vulnerabilities in the alerts.

### Check CodeQL Alerts Job:
- Fetches CodeQL alerts using the GitHub API.
- Checks for high or critical vulnerabilities in the alerts.

### Deploy Job:
- Decides on deployment based on the results of the scan, Dependabot alerts, and CodeQL alerts.

## Enabling Dependabot Alerts
1. Go to your repository on GitHub.
2. Click on the **Settings** tab.
3. In the left sidebar, click on **Security & analysis**.
4. Ensure that **Dependabot alerts** and **Dependabot security updates** are enabled.

## Conclusion
This CI/CD pipeline ensures that your application is built, scanned for vulnerabilities, and only deployed if no high or critical vulnerabilities are found. It integrates Trivy for Docker image scanning, Dependabot for dependency updates and vulnerability checks, and CodeQL for code analysis and security scanning.
