![Image](https://github.com/user-attachments/assets/2f5c0ba4-bc46-446c-be1a-e29d826513c0)
# Project Overview.
This project demonstrates the deployment of a Node.js application to an AWS EKS (Elastic Kubernetes Service) cluster using a complete CI/CD pipeline powered by GitHub Actions. It follows production-grade best practices for build, testing, analysis, and deployment automation.

# Prerequisites
Before proceeding, ensure you have the following components set up:
- An AWS EKS Cluster for application deployment.
- A JFrog Artifactory server, integrated with GitHub Actions using an OIDC provider for secure authentication.
- Sonarqube for static code analysis.
- Docker for containerization.
- A registered domain hosted on Amazon Route 53.

# Project Description
In this project, we deploy a Node.js application to an EKS cluster using an external MongoDB database for data persistence.
The application is exposed publicly via a Route 53–hosted domain, secured using AWS Certificate Manager (ACM) for TLS encryption, ensuring secure HTTPS communication.

The CI/CD pipeline, built with GitHub Actions, automates the following key processes:

1. Build and Code Quality
The pipeline builds the Node.js application and performs static code analysis using SonarQube to identify vulnerabilities and code smells.
If the application passes all SonarQube quality gates, the pipeline proceeds; otherwise, it fail automatically to maintain code integrity.

2. Testing and Code Coverage
The CI workflow includes comprehensive unit testing using frameworks such as Mocha, Chai, and Chai HTTP to validate API endpoints and core functionality.
We use a matrix strategy and dependency caching to optimize build time and resource usage across different test environments.
Code coverage reports are generated, archived, and reused in subsequent steps of the pipeline for efficiency and traceability.

3. Artifact Management with JFrog Artifactory
A JFrog Artifactory server is configured with local, remote, and virtual repositories for managing build artifacts.
User groups and permissions are established for controlled access.

The pipeline integrates JFrog with GitHub Actions using OIDC authentication, allowing secure publishing of build artifacts without storing long-lived credentials.

All build artifacts are uploaded and versioned in Artifactory for reference and future deployments.

![Image](https://github.com/user-attachments/assets/f7003745-39ce-4733-a36d-8abb6ae227a8)

# integrating Jfrog Artifactory with Github
![Image](https://github.com/user-attachments/assets/9297b418-5ce1-4625-9174-a9fdcc1a9c3d)

4. Deployment to EKS
Once the build and testing stages are successful, the application is deployed to the development environment within a dedicated Kubernetes namespace (e.g., dev).

Post-deployment, integration tests are executed to verify:
Application health status.
Reachability of all API endpoints.
Connectivity with the external MongoDB database (read/write validation).
![Image](https://github.com/user-attachments/assets/2c44bdf5-d23d-4a66-8054-b3834bcbece4)

# nslookup
![Image](https://github.com/user-attachments/assets/58f33471-6783-4e78-932f-098967c71dc8)

Successful completion of these stages ensures that the application is production-ready, secure, and fully validated before being promoted to higher environments.

# 🎬 Demo Video
[![Watch the video](https://img.youtube.com/vi/2h8u8PYVMnU/maxresdefault.jpg)](https://www.youtube.com/watch?v=2h8u8PYVMnU)




