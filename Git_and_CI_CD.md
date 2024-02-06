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
