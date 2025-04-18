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

In this tutorial, you'll learn how to build a fully automated CI/CD pipeline using AWS CodePipeline, CodeBuild, and Amazon S3 to deploy a React.js application hosted on GitHub. Say goodbye to manual deployments—every time you push to your repo, your app will automatically build and deploy to a static website on S3!


## <a name="steps">☑️ Steps</a>

1. Clone React.js App from Github
1. Create an IAM User
2. Configure AWS profile and set up the AWS CLI
3. Set Up Terraform Configuration
4. Deploy the Infrastructure with Terraform
5. Clean Up Resources

## <a name="quick-start">🤸 Quick Start</a>

**Prerequisites**

Make sure you have the following installed on your machine:

- [Node.js](https://nodejs.org/en) installed on your system.
- [Terraform CLI](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli) (1.2.0+) installed.
- [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html) installed.
- [AWS account](https://aws.amazon.com/free/) and [associated credentials](https://docs.aws.amazon.com/IAM/latest/UserGuide/security-creds.html) that allow you to create resources.


## <a name="clone-repo">	:octocat:  Cloning the Repository</a>

First, we’ll set up a React app by cloning the React app from my GitHub repository. If you already have one, feel free to skip this part.

```bash
git clone https://github.com/julien-muke/brainwave.git
```

## ➡️ Step 1 - Create an IAM User, and the Access Key