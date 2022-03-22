### Demo 3 - Modify NGINX service and expose via GCLB

### Assumptions
- Step 1 Assumptions Apply
- Step 2 Completed

### Steps
#### Review and deploy changes to NGINX service
1. Clone repo and navigate to demo_3 folder
2. Deploy NGINX to GKE `kubectl apply -f nginx.yaml`
3. Review  `nginx.yaml`
    - Reference [here](https://cloud.google.com/kubernetes-engine/docs/how-to/load-balance-ingress#creating_an_ingress) for notes on the ingress config
4. View the ingress settings `kubectl get ingress my-ingress --output yaml`
    - Reference [here](https://cloud.google.com/kubernetes-engine/docs/how-to/load-balance-ingress#testing_the)
5. Navigate to the GCLB settings, etc. 
6. Navigate to GKE workload and briefly show [autoscaling](https://cloud.google.com/kubernetes-engine/docs/how-to/horizontal-pod-autoscaling#resource-utilization)
