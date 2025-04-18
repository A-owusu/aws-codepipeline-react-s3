# ![aws](https://github.com/julien-muke/Search-Engine-Website-using-AWS/assets/110755734/01cd6124-8014-4baa-a5fe-bd227844d263) Deploy React App with Full CI/CD Pipeline on AWS | GitHub + CodePipeline + S3 🚀

<div align="center">

  <br />
    <a href="https://youtu.be/Tbp6VJrq2ho?si=htW_VrEVu3E4XiEn" target="_blank">
      <img src="https://github.com/user-attachments/assets/9f9b55f3-c9c2-4b87-97c7-030be3464a83" alt="Project Banner">
    </a>
  <br />

<h3 align="center">Deploying a React app using EC2 and Terraform</h3>

   <div align="center">
     Build this hands-on demo step by step with my detailed tutorial on <a href="http://www.youtube.com/@julienmuke/videos" target="_blank"><b>Julien Muke</b></a> YouTube. Feel free to subscribe 🔔!
    </div>
</div>

## 🚨 Tutorial

This repository contains the steps corresponding to an in-depth tutorial available on my YouTube
channel, <a href="http://www.youtube.com/@julienmuke/videos" target="_blank"><b>Julien Muke</b></a>.

If you prefer visual learning, this is the perfect resource for you. Follow my tutorial to learn how to build projects
like these step-by-step in a beginner-friendly manner!

<a href="https://youtu.be/Tbp6VJrq2ho?si=htW_VrEVu3E4XiEn" target="_blank"><img src="https://github.com/sujatagunale/EasyRead/assets/151519281/1736fca5-a031-4854-8c09-bc110e3bc16d" /></a>

## <a name="introduction">🤖 Introduction</a>

In this tutorial, you'll learn how to build a fully automated CI/CD pipeline using AWS CodePipeline, CodeBuild, and Amazon S3 to deploy a React.js application hosted on GitHub. Say goodbye to manual deployments, every time you push to your repo, your app will automatically build and deploy to a static website on S3!


## <a name="steps">☑️ Steps</a>

1. Setup your React App on GitHub
2. Create S3 Bucket for Hosting
3. Create CodeBuild Project
4. Create CodePipeline
5. Test the Pipeline
6. Clean Up Resources

## ➡️ Step 1 - Setup your React.js App on GitHub

First, we’ll set up a React app by cloning the React app from my GitHub repository. You can use your own or follow along with mine. Make sure the app is committed to GitHub.


```bash
git clone https://github.com/julien-muke/saas-landing-page.git
```

## ➡️ Step 2 - Create S3 Bucket for Hosting

For the deploy provider we are going to use Amazon S3, we will create an S3 bucket.
1. Head over to the S3 service.
2. Click Create bucket.
3. Name it something unique like `my-react-cicd-demo`

Once the s3 bucket is created, leave it for now, as we will come for it to finish the setup later.

## ➡️ Step 3 - Create CodeBuild Project

Now let’s set up CodeBuild, which will handle building the React app.

1. Go to CodeBuild, click Create Build Project.
2. Name it something like `react-app-builder`
3. Connect to GitHub or choose AWS CodePipeline as the source later.
4. Choose a managed image: aws/codebuild/standard:6.0 (or latest).
5. Set the buildspec file as default (we’ll add it to our repo).

Inside your GitHub repo, create a file named buildspec.yml in the root:

```yaml
version: 0.2

phases:
  install:
    runtime-versions:
      nodejs: 16
    commands:
      - npm install
  build:
    commands:
      - npm run build
artifacts:
  files:
    - '**/*'
  base-directory: build

```