# Serverless Cloud Run

### Why do this
 - RUN stateless, short-term compute tasks
 - RUN your analysis job tasks individually, or chained into a workflow (or pipeline)
 - PAY only **when a function is called (or invoked)**, rather than for a long-running VM or container

### What is this
 - Use functions where you supply your own containers, rather than GCP-supplied containers or VMs for compute
 - Use GCP Cloud Run to host your function(s) on GCP

### Key considerations
 - In Cloud Run, you supply the code and container file (Dockerfile), GCP builds, registers and runs your container image. Your function can be called via HTTP requests
 - State is NOT automatically saved after the function is invoked.  If you need to persist information, then you must write the logic to save the output to files (bucket) or a database and then to retrieve that information in a later part of the workflow

### How to do this
 - WRITE and test your function code
 - BUILD a docker image w/that code by running 'docker build....' on a DOCKERFILE
 - REGISTER your docker container image in Google Container Registry
 - ASSOCIATE your image to CloudRun 
 - TEST (invoke) and monitor your service

### How to verify you've done it
 - INVOKE the function manually or via a test script
 - REVIEW the Stackdriver logs to see the result of the function invocation

### Other Things to Know

 - Serverless patterns are often used for workloads that have spikes in demand
 - Using the 'revision settings' you can set a min/max number of instances for autoscaling for your deployment.  You can also set the 'maximum requests per container'
 - Serverless auto-scales (to your GCP account limits) by default
 - Cloud Run has two execution modes - within CloudRun and CloudRun for Anthos using Kubernetes (GKE)
 - GAE (AppEngine) is a serverless service which can be used to host web sites and support common programming language.  Python example [here](https://cloud.google.com/appengine/docs/python/)
 - Cloud Build (for serverless continuous deployment) is integratable into CloudRun functions.  Use it for CD in building updated Docker images 

### How to learn more

- 📘 Link to [choosing a serverless option](https://cloud.google.com/serverless-options/)
- 📓 Do a GCP Codelab to use CloudRun on GKE(K8) - [link](https://codelabs.developers.google.com/codelabs/cloud-run-gke/)
- 📺 Demo of 'R Shiny on Cloud Run' - shows configuration and set up - [link](https://www.youtube.com/watch?v=uu97P0IWsO0)
 - :octocat: Link to [Try Cloud Run from a GitHub Repo](https://github.com/lynnlangit/hello-cloud-run).  
 - 📺 Watch to "What is Cloud Run?" 3 minute demo video - [link](https://www.linkedin.com/learning/google-cloud-platform-essential-training-3/google-cloud-run)
- 📺 Watch to "What is Cloud run on GKE?" 4 minute demo video - [link](
https://www.linkedin.com/learning/google-cloud-platform-essential-training-3/google-cloud-run-on-gke)

### See it in action

- :octocat: demo repo --> https://github.com/lynnlangit/hello-cloud-run
  - builds a docker container from the Dockerfile
  - registers the container image on gcr.io 
  - creates a serverless function from the container image 
 <img src="https://github.com/lynnlangit/gcp-for-bioinformatics/blob/master/images/hello-cloud-run.png" width=400 align="left">
 <img src="https://github.com/lynnlangit/gcp-for-bioinformatics/blob/master/images/container-registry.png" width=400 align="right">
<img src="https://github.com/lynnlangit/gcp-for-bioinformatics/blob/master/images/cloud-run.png" width=400 align="right">




