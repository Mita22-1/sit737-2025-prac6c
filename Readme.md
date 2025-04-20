### To begin this task, I cloned the project from my GitHub repository where I have made necessary updates to the application:

git clone https://github.com/Mita22-1/sit737-2025-prac5p.git
Checking Pod and Service Status

### After navigating into the project directory and deploying the YAML files, I used the commands below to verify that the pods and services were successfully created:

kubectl get pods
kubectl get services
### Exposing the Application via Port Forwarding
To access the application from my local machine, I executed:

kubectl port-forward svc/web-app-service 31111:3111

This allowed me to open the app at http://localhost:31111.

### Accessing the Running Application

Once the port forwarding was active, I opened the browser and accessed the live calculator application, confirming that the service was functioning as intended.

## Part 2: Updating the Application
### building a New Docker Image
I modified both the frontend (calculator.html) and backend (server.js) to improve UI/UX and enable additional operations. After testing locally, I built a new Docker image using:

docker build -t mitalikaur/web_app:2.0 .
## Pushing to Docker Hub
Once the image was built successfully, I pushed it to Docker Hub under my own account:

docker push mitalikaur/web_app:2.0

### Updating the Kubernetes Deployment

The deployment.yaml file was updated to use the new image:

image: mitalikaur/web_app:2.0
imagePullPolicy: Always

Then, I redeployed the application with:

kubectl apply -f deployment.yaml
kubectl rollout restart deployment web-app-deployment

### Application Output and Confirmation

After rollout, I used kubectl logs and browser testing to confirm the updated application was running successfully, displaying the new UI and processing calculator operations as expected.
