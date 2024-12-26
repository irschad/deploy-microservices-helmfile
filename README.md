# Deploy Microservices with Helmfile

## Project Overview
This project demonstrates how to deploy a set of microservices on Kubernetes using Helm and Helmfile. The deployment process is divided into two parts:
1. Deploy Microservices with Helm
2. Deploy Microservices with Helmfile

## Technologies Used
- Kubernetes
- Helm
- Helmfile

## Part 1: Deploy Microservices with Helm
### Steps

1. **Install Microservices with Helm**:
   ```bash
   helm install -f values/redis-values.yaml rediscart charts/redis
   helm install -f values/email-service-values.yaml emailservice charts/microservice
   helm install -f values/cart-service-values.yaml cartservice charts/microservice
   helm install -f values/currency-service-values.yaml currencyservice charts/microservice
   helm install -f values/payment-service-values.yaml paymentservice charts/microservice
   helm install -f values/recommendation-service-values.yaml recommendationservice charts/microservice
   helm install -f values/productcatalog-service-values.yaml productcatalogservice charts/microservice
   helm install -f values/shipping-service-values.yaml shippingservice charts/microservice
   helm install -f values/ad-service-values.yaml adservice charts/microservice
   helm install -f values/checkout-service-values.yaml checkoutservice charts/microservice
   helm install -f values/frontend-values.yaml frontendservice charts/microservice
   ```

2. **Verify Pods**:
   ```bash
   kubectl get pods
   ```

3. **Verify Helm Releases**:
   ```bash
   helm ls
   ```

4. **Uninstall Releases**:
   Run the `uninstall.sh` script to remove all releases:
   ```bash
   ./uninstall.sh
   ```
   Example output:
   ```bash
   release "rediscart" uninstalled
   release "emailservice" uninstalled
   ...
   ```

## Part 2: Deploy Microservices with Helmfile
### Steps

1. **Install Helmfile**:
   ```bash
   curl -Lo helmfile.tar.gz https://github.com/helmfile/helmfile/releases/download/v0.169.2/helmfile_0.169.2_linux_amd64.tar.gz
   tar -xvf helmfile.tar.gz
   sudo mv helmfile /usr/local/bin/
   ```

2. **Verify Helmfile Installation**:
   ```bash
   helmfile --version
   ```

3. **Initialize Helmfile**:
   ```bash
   helmfile init
   ```
   Ensure your Helm version meets the required minimum (e.g., `3.15.4`).

4. **Run Helmfile Sync**:
   Deploy all microservices using `helmfile sync`:
   ```bash
   helmfile sync
   ```
   This step builds dependencies and deploys all microservices defined in the `Helmfile` configuration.

5. **Verify Helm Releases and Pods**:
   - Check Helmfile releases:
     ```bash
     helmfile list
     ```
   - Check Kubernetes pods:
     ```bash
     kubectl get pods
     ```

6. **Access the Application**:
   Use the LoadBalancer URL to access the deployed microservices. You can find the URL using:
   ```bash
   kubectl get svc frontend
   ```

## Notes
- Ensure Kubernetes and Helm are installed and configured correctly before starting the deployment.
- Helmfile simplifies the management of multiple Helm releases and dependencies.
- Check for resource allocation and node capacity when deploying large numbers of microservices.

## Conclusion
This project illustrates a step-by-step approach to deploying microservices using Helm and Helmfile. These tools help manage Kubernetes applications efficiently, providing flexibility and scalability.
