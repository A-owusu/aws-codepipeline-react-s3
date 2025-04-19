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
3. Create CodePipeline
4. Create CodeBuild Project
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


## ➡️ Step 3 - Create CodePipeline

Now the fun part—building the pipeline.

1. Go to AWS CodePipeline, click Create pipeline.
2. Name your pipeline: `reactapp-cicd-demo`
3. Choose a new service role or an existing one.

![Image](https://github.com/user-attachments/assets/718b0040-e0f8-43e4-81ce-3b7e6d55c162)

4. Add source stage:
<br>- Source provider: GitHub (connect your GitHub account).
<br>- Select your repository and branch.

Note: Make sure you select the repository that we cloned in Step 1

![Image](https://github.com/user-attachments/assets/7d7d6e7f-8a39-47e3-9271-ffa8c045c3cf)

<br>- Once you are connected to your Github and select your repository, then choose "Next"

![Image](https://github.com/user-attachments/assets/2177e920-30a3-4196-b673-5ae4f1733391)

5. Add build stage:
<br>- Provider: AWS CodeBuild.




6. Add deploy stage:
<br>- Provider: Amazon S3.
<br>- Bucket: Select the one you created earlier.
<br>- Extract file option: YES.

## ➡️ Step 4 - Create CodeBuild Project

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
      nodejs: 18
    commands:
      - echo Installing dependencies...
      - npm ci --force or --legacy-peer-deps

  build:
    commands:
      - echo Building the React app...
      - npm run build

artifacts:
  files:
    - '**/*'
  base-directory: dist
  discard-paths: no

```

Note: This file tells CodeBuild to install dependencies, build the app, and copy the contents of the build/ folder as artifacts.



## ➡️ Step 5 - Test the Pipeline

Let’s test the whole pipeline. I’ll make a small change to the homepage text and push it to GitHub.

As soon as the code is pushed, CodePipeline is triggered. You’ll see it run through the source, build, and deploy stages.