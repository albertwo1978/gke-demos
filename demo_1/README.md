### Demo 1 - Build a simple NGINX Docker container and push to Artifact Registry
Contents referenced from [NGINX-Demos/hello](https://github.com/nginxinc/NGINX-Demos/tree/master/nginx-hello)

![hello](https://github.com/nginxinc/NGINX-Demos/blob/master/nginx-hello/hello.png?raw=true)

### Assumptions
- Run from CloudShell
    - Docker installed by default
- Target Project with the following enabled:    
    - Compute Engine API
    - Kubernetes Engine API
    - Artifact Registry API
- Following services installed: 
    - Default VPC Network
    Artifact Registry created with a `demo` repo created in us-east1

### Steps
#### Create Docker image and push to registry
1. Clone repo and navigate to demo_1 folder
2. Open files and talk through them (ex. dockerfile)
3. Build the image `docker build -t gke-demo .`
4. List the images `docker image list`
5. Run the image `docker run -d -p 8080:80 gke-demo`
6. Optional Commands: 
    - `docker ps -a`
    - `docker exec -it <container_id> sh`
    - `ps aux`
6. Preview in CloudShell on port `8080`

#### Push to Google Artifact Registry - Reference [here](https://cloud.google.com/artifact-registry/docs/docker/pushing-and-pulling#pushing)
1. Tag the image `docker tag gke-demo us-east1-docker.pkg.dev/<project_id>/<repo>/gke-demo:latest`
2. Add host to credfile `gcloud auth configure-docker us-east1-docker.pkg.dev`
3. Push to Artifactory `docker push us-east1-docker.pkg.dev/<project_id>/<repo>/gke-demo:latest`
4. Go to [Repositories page](https://console.cloud.google.com/artifacts?_ga=2.195332204.1964474193.1647886615-787155117.1645886534) to see uploaded image


Go to [Demo 2](https://github.com/albertwo1978/gke101-demos/tree/main/demo_2).