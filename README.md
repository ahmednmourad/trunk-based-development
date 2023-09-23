## Trunk-Based Development

This project follows a trunk-based development approach to maintain an efficient and streamlined development process. Trunk-based development is a version control management practice in which developers merge small, frequent updates directly into the main branch, known as the "trunk."

A key guiding principle is that Trunk-Based Development teams exclusively either release directly from the trunk (see [Release from Trunk](https://trunkbaseddevelopment.com/release-from-trunk/)), or they create a branch from the trunk specifically for the actual release (see [Branch for Release](https://trunkbaseddevelopment.com/branch-for-release/)). In this project, we have chosen the former option, releasing directly from the trunk to multiple environments (dev, staging, prod).

For more details on trunk-based development, please visit [trunkbaseddevelopment.com](https://trunkbaseddevelopment.com/).

## Setup Instructions

To get started with this project, follow these steps:

1. **Create a RELEASE_PLEASE_TOKEN Secret**

   To automate releases, you'll need to create a secret named `RELEASE_PLEASE_TOKEN`. This token allows the Release Please Action to manage releases in your repository:

   - Go to your GitHub repository.
   - Navigate to "Settings."
   - Under "Secrets," create a new repository secret named `RELEASE_PLEASE_TOKEN` and paste in your personal access token.

2. **Create Environments**

   This project uses three environments: Development, Staging, and Production. Here's how to set them up:

   - Navigate to your GitHub repository.
   - Click on "Settings" in the top-right corner.
   - Under "Code and automation," select "Environment."
   - Create the following environments: Development, Staging, and Production.
   - Customize each environment's settings as needed. It's recommended to configure manual approvals for the `Production` and `Staging` environments by clicking on "Required Viewers" and adding people who can review and approve deployments.

3. **Restrict Deployment Branches** (Optional but Recommended)

   Ensure that only the `main` branch can be used to deploy to the Staging and Production environments:

   - In the environment settings, select the Production environment.
   - Under "Deployment Branches," choose "Selected Branches" and add `main` as the allowed branch. Repeat this process for the Staging environment.

   This prevents unintended deployments from other branches. For instance, if a developer updates the workflow file to trigger the workflow on changes to a `test` branch, the `staging-deploy` job will run and fail due to the rule we've added above.

### Project Pipelines

This project includes two essential GitHub Actions pipelines:

- **Deployment Pipeline:** This pipeline simulates deploying code changes to different environments (Development, Staging, Production) based on branch pushes. It ensures code stability and compatibility before reaching the production environment.

- **Release Automation Pipeline:** This pipeline automates version management, changelog generation, GitHub releases, and version bumps for your projects using the release-please GitHub Action. This simplifies the release process and maintains your project's organization.

Feel free to adapt and expand upon these pipelines to meet your project's specific requirements.
