# CI CD INTEGRATION GIT 

Below are the steps for integrating Continuous Integration (CI) and Continuous Deployment (CD) using GitHub Actions. 
This example assumes you are deploying a Node.js application to a cloud service like Heroku.

### Step 1: Create a GitHub Actions Workflow

Create a new file named `.github/workflows/main.yml` in the root of your repository. This file defines the workflow configuration.

```yaml
name: CI-CD Workflow

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout Repository
      uses: actions/checkout@v2

    - name: Setup Node.js
      uses: actions/setup-node@v2
      with:
        node-version: '14'

    - name: Install Dependencies
      run: npm install

    - name: Run Tests
      run: npm test

  deploy:
    runs-on: ubuntu-latest
    needs: build
    steps:
    - name: Deploy to Heroku
      uses: akhileshns/heroku-deploy@v3.12.12
      with:
        heroku_api_key: ${{ secrets.HEROKU_API_KEY }}
        heroku_app_name: "your-heroku-app-name"
        heroku_email: "your-heroku-email@example.com"
```

**You can see all the actions : Here [https://github.com/actions](https://github.com/actions)**

### Step 2: Set up Heroku

- Create an account on [Heroku](https://www.heroku.com/) if you don't have one.
- Create a new Heroku app.
- Obtain the Heroku API key from your Heroku account settings.

### Step 3: Add Heroku API Key to GitHub Secrets

In your GitHub repository, go to "Settings" > "Secrets" and add a new secret named `HEROKU_API_KEY` with the value being the Heroku API key obtained in Step 2.

### Step 4: Commit and Push Changes

Commit the `.github/workflows/main.yml` file and push it to your GitHub repository.

```bash
git add .github/workflows/main.yml
git commit -m "Add GitHub Actions workflow"
git push origin main
```

### Step 5: Trigger GitHub Actions Workflow

Make any change to your repository and push it to trigger the GitHub Actions workflow.

### Step 6: Monitor Workflow Execution

Go to the "Actions" tab in your GitHub repository to monitor the workflow execution. You should see the CI/CD workflow running, including the steps to install dependencies, run tests, and deploy to Heroku.

This is a basic example, and you can customize the workflow according to your project's needs.
Additionally, you might need to adjust the deployment steps based on the specific cloud service you are using.

### In a YAML file used for configuring Continuous Integration (CI) and Continuous Deployment (CD) workflows, each keyword serves a specific purpose. Here's an explanation of each keyword commonly found in such YAML files:

1. **name:**
   - **Purpose:** Specifies the name of the workflow.
   - **Example:** `name: CI-CD Workflow`

2. **on:**
   - **Purpose:** Defines the triggers that initiate the workflow.
   - **Example:** 
     ```yaml
     on:
       push:
         branches:
           - main
     ```

3. **jobs:**
   - **Purpose:** Contains one or more jobs to be executed as part of the workflow.
   - **Example:** 
     ```yaml
     jobs:
       build:
         ...
       deploy:
         ...
     ```

4. **runs-on:**
   - **Purpose:** Specifies the operating system and environment for job execution.
   - **Example:** `runs-on: ubuntu-latest`

5. **steps:**
   - **Purpose:** Contains a sequence of actions to be executed within a job.
   - **Example:** 
     ```yaml
     steps:
       - name: Checkout Repository
         uses: actions/checkout@v2
       - name: Setup Node.js
         uses: actions/setup-node@v2
         with:
           node-version: '14'
       ...
     ```

6. **uses:**
   - **Purpose:** Specifies an action or a reusable action that performs a specific task.
   - **Example:** `uses: actions/checkout@v2`

7. **with:**
   - **Purpose:** Provides input parameters or configuration options for an action.
   - **Example:** 
     ```yaml
     with:
       node-version: '14'
     ```

8. **secrets:**
   - **Purpose:** Enables access to encrypted secrets stored in GitHub repository settings.
   - **Example:** 
     ```yaml
     secrets:
       HEROKU_API_KEY: ${{ secrets.HEROKU_API_KEY }}
     ```

9. **needs:**
   - **Purpose:** Specifies dependencies between jobs, ensuring that one job waits for another to complete before starting.
   - **Example:** `needs: build`

10. **environment:**
    - **Purpose:** Defines the runtime environment for a job, such as production, staging, or testing.
    - **Example:** `environment: production`

These keywords are essential for configuring CI/CD workflows effectively in YAML files. They define the structure and behavior of the workflow, including triggers, actions, dependencies, and runtime environments.
