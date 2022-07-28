# ongoing-project
Itay's project
Contains a "python.py" file running a web app using flask inside folder "flaskexample" 
+ a Dockerfile with a python image to run the python code from.
an image built from this Dockerfile was uploaded to my private Amazon ECR (url available in Deployment.yaml image)
inside /flaskexample/helmsd/ongoing-project there's the default helm charts/values files and a folder titled "templates"
inside it are the 4 k8s yaml files used for deploying the application - a Deployment, Service, Ingress & CronJob
for obtaining new aws auth tokens(without the access key secret file, which is located locally on my machine to prevent
security breaches).
