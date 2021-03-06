### Demo 2 - Create a GKE Cluster and Deploy Demo NGINX Workload

### Assumptions
- Step 1 Assumptions Apply
- Step 1 Completed

### Steps
#### Create a GKE cluster
1. Create the GKE cluster in `us-east1`
    - Do it however you want ... I would assume in the portal and talking through it (but also calling out this can be scripted, TF, etc)
    - <b>NOTE:</b> You should already have a precreated GKE cluster deployed and ready to move to the next step

#### Deploy the container to the cluster
1. Clone repo and navigate to demo_2 folder
2. Set the project `gcloud config set project <project_id>`
3. Authenticate to the cluster `gcloud container clusters get-credentials <cluster_name> --region us-east1`
4. Grant cluster permission to the Artifact Registry: 
    ```
    gcloud artifacts repositories add-iam-policy-binding demo \
        --location=us-east1 \
        --member=serviceAccount:<gke_service_account> \
        --role="roles/artifactregistry.reader"
    ```
5. Modify `nginx.yaml`
6. Deploy NGINX to GKE `kubectl apply -f nginx.yaml`
7. Optional Commands: 
    - `kubectl get deployments -w`
    - `kubectl get pods`
    - `kubectl get all`
8. Navigate to the GKE cluster in the GCP console, observe workload, services, etc. 

Go to [Demo 3](https://github.com/albertwo1978/gke101-demos/tree/main/demo_3).