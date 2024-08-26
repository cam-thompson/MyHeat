# Ansible Docker Automation with GitHub Actions

This repository demonstrates how to automate the management of Docker containers using an Ansible playbook and GitHub Actions. The provided GitHub Actions workflow installs Docker, Ansible, and necessary dependencies to spin up and tear down Docker containers on demand.

## Table of Contents

- [Introduction](#introduction)
- [Pre-requisites](#pre-requisites)
- [Setup](#setup)
- [GitHub Actions Workflow](#github-actions-workflow)
- [How to Use](#how-to-use)
- [Customization](#customization)
- [Troubleshooting](#troubleshooting)

## Introduction

This project automates the deployment and management of Docker containers using Ansible and GitHub Actions. It includes:

- An Ansible playbook (`ansible/docker-playbook.yml`) to manage Docker containers.
- A GitHub Actions workflow (`.github/workflows/ansible-docker.yml`) that installs required dependencies and runs the playbook.

## Pre-requisites

Before using this repository, ensure you have:

- A GitHub account.
- Basic knowledge of Git, Docker, and Ansible.
- Ansible playbook (`ansible/docker-playbook.yml`) prepared to manage Docker containers.

## Setup

To set up the automation, follow these steps:

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/your-username/your-repo.git
   cd your-repo
2. **Prepare the Ansible Playbook**:

   Ensure your Ansible playbook (`ansible/docker-playbook.yml`) is configured correctly to manage Docker containers. Refer to the provided example in this repository.

3. **Configure GitHub Secrets** (if needed):

   If your playbook requires additional secrets (like environment variables or API tokens), add them to your repository under **Settings** > **Secrets and variables** > **Actions**.

## GitHub Actions Workflow

The GitHub Actions workflow (`.github/workflows/ansible-docker.yml`) automates the following:

1. **Checkout the Repository**:  
   Uses `actions/checkout@v3` to check out the code.

2. **Install Dependencies**:
   - Removes any conflicting Docker packages.
   - Installs Docker and `containerd` from Docker’s official repository.
   - Installs Python, pip, Ansible, and the Ansible Docker collection.

3. **Run Ansible Playbook**:
   - Spins up Docker containers as defined in the playbook.
   - Tears down Docker containers at the end, ensuring a clean state.

## How to Use

1. **Push Changes**:  

   Make any changes to your Ansible playbook or repository content and push to the `main` branch.
   
2. **Trigger the Workflow**:

   - The workflow is automatically triggered on any push to the `main` branch.
   - You can also manually trigger the workflow via the **Actions** tab in GitHub.

3. **Monitor Workflow Execution**:

   Go to the **Actions** tab in your GitHub repository to monitor the workflow's progress and see logs for each step.

## Customization

- **Change Trigger Branch**: Modify the `on: push: branches` field in the workflow file to specify different branches that should trigger the workflow.
- **Modify Ansible Playbook**: Update the `ansible/docker-playbook.yml` as needed to manage different Docker containers or configurations.
- **Add Secrets or Environment Variables**: Use GitHub Secrets to securely manage any sensitive data required by your playbook. You can add secrets in the repository settings under **Settings** > **Secrets and variables** > **Actions**.

## Troubleshooting

- **Unmet Dependencies**: Ensure no conflicting packages exist before Docker installation. The workflow includes steps to remove existing Docker-related packages to avoid conflicts.
- **Permissions Issues**: Ensure the GitHub Actions runner has the necessary permissions to execute Docker commands.
- **Workflow Fails**: If the workflow fails, check the logs in the **Actions** tab for detailed error messages and adjust your playbook or workflow steps accordingly.

## Conclusion

By setting up this GitHub Actions workflow, you can automate the management of Docker containers using Ansible, enabling continuous integration and deployment directly from your GitHub repository.

Feel free to customize the workflow and playbook to suit your specific needs!
