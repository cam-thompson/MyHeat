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

