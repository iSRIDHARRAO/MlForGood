# MlForGood
## Inspiration
A Brain Tumor is a pernicious issue, people cannot find its existence in the body directly because it is invisible However helping people to detect its presence in the body toward the early phase would be a great work.
So, here we're with our CNN model, easy to predict whether a person attacked with a Brain Tumor or not.

## What it does
Our web app predicts whether a person is suffering from a Brain Tumor by letting the user upload the picture of an MRI Scanned Image of the Brain 

- **How to Predict**

![Prediction Step](https://drive.google.com/uc?export=view&id=1UsKetsHOdfYIyBE3DF9r8jkl0__aa8TU)
1. Browse to [Brain Tumor Prediction Website](https://tinyurl.com/MlForGood)
2. Navigate to Predict step 
3. Upload Image for Prediction 
4. You will be routed to the result of the prediction. It will show the affected area

## How we built it


***Team Formation***

The primary step of this project is the same as any other project we formed as a team and we called ourselves ***Visual Velocity***. Team members are from all over India and from different colleges. we are connected over LinkedIn and connected with referrals of friends. All the participants are undergrads or Just finished their bachelor's degree. 
The team is a combo of multiple skilled people. So,  we divided into teams 

- **Machine Learning:**

![ML-Architecture](https://drive.google.com/uc?export=view&id=1DAVuSJeGlbcoOJ6ppo4sojomr9ed2pw5)

The Machine Learning team worked on code to create Convolutional Neural Network  Model for Brain Tumor prediction. They created Machine Learning Code with Keras.


- **User Interface and Experience:**

UI/UX team worked on website development. They created code for the website and the website is informative and has multiple details about Brain Tumors. 

- **Architecture team:**

The architecture team worked on the creation of the pipeline with Machine Learning code and Frontend code and automated from Development to Production with DevOps tools: Shell Scripting, Ansible, Docker, Kubernetes, Git Hub Actions, ArgoCD, Terraform, and Cloud Platforms: Microsoft Azure for AKS and AWS for S3

***Pipeline***

![Architecture](https://drive.google.com/uc?export=view&id=1WXsPiYihEpbjGqIU5NinemFOG5Sawe9Z)

Here is the complete flow of the project how it actually works. 

- There are two separated repositories for Frontend and Machine Learning. The Machine Learning team will update the model code in [MLMLOpsforGood](https://github.com/kethavathsivanaik/MLMLOpsforGood) repository and UI/UX team works on [FrontendMLOpsforGood](https://github.com/kethavathsivanaik/FrontendMLOpsforGood) repository. 

- The Architecture team/DevOps team has already pushed the GitHub Actions' code in .git/workflows/ directory in both the repositories. For every event of code change, the GitHub Actions will trigger and build a Docker Image and save the image in Docker Hub. The Docker hub credentials are passed from GitHub repository secrets 

-  The repositories also have the Helm charts uploaded by the DevOps team in the manifests directory to deploy the Machine Learning training deployment and Frontend Deployment with ArgoCD running on AKS

- The AKS Cluster is already provisioned and the ArgoCD Helm chart is deployed on top of AKS with Terraform, Infrastructure as a Code tool

- The DevOps team is doing operations from the Azure cloud shell. They created two ArgoCD projects with declarative manifests the projects will monitor those two repositories for code change and deploy on top AKS when they sync the repositories 

- The ML Model Training deployment will get the dataset from S3 Bucket with Ansible and Train Model and Save Model to S3 Bucket with the help of Ansible. The user ansible uses to upload has limited power to access S3 Buckets 

- The  Model will be downloaded to the frontend deployment with the help of Ansible and the client can see the website with the LoadBalancer IP of service created in AKS. 

- The website has a simple UI and is easy to navigate. When the client upload the image the model will predict the image and sends back the output to the client 

## [Complete Video](https://youtu.be/Ih7mSTgXZHw)
## Challenges we ran into
We faced a ton of challenges throughout the project : 
- Integration of multiple DevOps tools in the complete pipeline 
- Finding the correct hyperparameters when training the Model
- Making the website responsive 
- Securing the credentials of S3 Buckets we used for Dataset 
- Cache Issues in the website and showing previous predicted Images for the current prediction
- The real challenge is to integrate Frontend with Machine Learning Model

## Accomplishments that we're proud of

- Integrated 10+ tools to automate everything from development to production 
- The Website is designed in such a way it is very user-friendly and simple to navigate 
- The predictions are almost correct. 
- We  implemented the project in 3 days before the deadline of the Hackathon 

## What we learned

We understood the power of integrating multiple tools and technologies and solving real-world problems using them. Also as we worked in a team we learned how to work in a team.

## What's next for Brain Tumor Detection #MLOps @Visual-Velocity

- Multi-Branch build in GitHub Action to work on several models at the same time 
- Increase the Dataset of the model trained on
- Create a Mobile UI with Flutter and make this product available on Mobile 
- Notify the Data Scientist when the accurate model is created 
- We are going to work on the same as the Open Source tool and improve its performance and build a framework 


## References & Further Readings

- [Azure](https://docs.microsoft.com/en-us/azure/?product=featured)
- [AWS](https://docs.aws.amazon.com/)
- [Keras](https://keras.io/getting_started/)
- [Flask](https://flask.palletsprojects.com/en/2.0.x/)
- [Helm](https://helm.sh/docs/)
- [GitHub Actions](https://docs.github.com/en/actions)
- [Docker](https://docs.docker.com/)
- [Dockerfile](https://docs.docker.com/engine/reference/builder/)
- [Kubernetes](https://kubernetes.io/docs/home/)
- [ArgoCD](https://argoproj.github.io/argo-cd/)
- [Ansible](https://docs.ansible.com/)
- [Terraform](https://www.terraform.io/docs/index.html)
