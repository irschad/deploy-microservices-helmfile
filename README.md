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
   Install script contents:
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
   Run install script
     ```bash
     ./install.sh
   
      NAME: rediscart
      LAST DEPLOYED: Wed Dec 25 13:45:14 2024
      NAMESPACE: default
      STATUS: deployed
      REVISION: 1
      TEST SUITE: None
      NAME: emailservice
      LAST DEPLOYED: Wed Dec 25 13:45:15 2024
      NAMESPACE: default
      STATUS: deployed
      REVISION: 1
      TEST SUITE: None
      NAME: cartservice
      LAST DEPLOYED: Wed Dec 25 13:45:16 2024
      NAMESPACE: default
      STATUS: deployed
      REVISION: 1
      TEST SUITE: None
      NAME: currencyservice
      LAST DEPLOYED: Wed Dec 25 13:45:17 2024
      NAMESPACE: default
      STATUS: deployed
      REVISION: 1
      TEST SUITE: None
      NAME: paymentservice
      LAST DEPLOYED: Wed Dec 25 13:45:18 2024
      NAMESPACE: default
      STATUS: deployed
      REVISION: 1
      TEST SUITE: None
      NAME: recommendationservice
      LAST DEPLOYED: Wed Dec 25 13:45:18 2024
      NAMESPACE: default
      STATUS: deployed
      REVISION: 1
      TEST SUITE: None
      NAME: productcatalogservice
      LAST DEPLOYED: Wed Dec 25 13:45:19 2024
      NAMESPACE: default
      STATUS: deployed
      REVISION: 1
      TEST SUITE: None
      NAME: shippingservice
      LAST DEPLOYED: Wed Dec 25 13:45:20 2024
      NAMESPACE: default
      STATUS: deployed
      REVISION: 1
      TEST SUITE: None
      NAME: adservice
      LAST DEPLOYED: Wed Dec 25 13:45:21 2024
      NAMESPACE: default
      STATUS: deployed
      REVISION: 1
      TEST SUITE: None
      NAME: checkoutservice
      LAST DEPLOYED: Wed Dec 25 13:45:21 2024
      NAMESPACE: default
      STATUS: deployed
      REVISION: 1
      TEST SUITE: None
      NAME: frontendservice
      LAST DEPLOYED: Wed Dec 25 13:45:22 2024
      NAMESPACE: default
      STATUS: deployed
      REVISION: 1
      TEST SUITE: None
     ```

3. **Verify Pods**:
   ```bash
   kubectl get pods
   
   NAME                                     READY   STATUS    RESTARTS   AGE
   adservice-d7ff4646b-7v6w6                1/1     Running   0          31s
   adservice-d7ff4646b-qmfsq                1/1     Running   0          31s
   cartservice-7496fc6c9b-lsf9p             1/1     Running   0          36s
   cartservice-7496fc6c9b-wwhkf             1/1     Running   0          36s
   checkoutservice-564cdbcbc5-6lchv         1/1     Running   0          30s
   checkoutservice-564cdbcbc5-qr25d         1/1     Running   0          30s
   currencyservice-69c577d9f8-4pj25         1/1     Running   0          35s
   currencyservice-69c577d9f8-dbr4z         1/1     Running   0          35s
   emailservice-c6b75bdfc-597s5             1/1     Running   0          37s
   emailservice-c6b75bdfc-cwpvd             1/1     Running   0          37s
   frontend-7b5c58f8c-4m7r4                 1/1     Running   0          30s
   frontend-7b5c58f8c-fdwv9                 1/1     Running   0          30s
   paymentservice-5d6865d4c-jgbl8           1/1     Running   0          34s
   paymentservice-5d6865d4c-k6hsv           1/1     Running   0          34s
   productcatalogservice-fbfc699d9-bwmm8    1/1     Running   0          33s
   productcatalogservice-fbfc699d9-h2mzv    1/1     Running   0          33s
   recommendationservice-6c4fdb4f46-6nztz   1/1     Running   0          34s
   recommendationservice-6c4fdb4f46-d7z2n   1/1     Running   0          34s
   redis-cart-574b7cb494-9z6rc              1/1     Running   0          38s
   redis-cart-574b7cb494-kzkt2              1/1     Running   0          38s
   shippingservice-79bc74547c-fhjdj         1/1     Running   0          32s
   shippingservice-79bc74547c-rcpkz         1/1     Running   0          32s

   ```

4. **Verify Helm Releases**:
   ```bash
   helm ls
   
   NAME                    NAMESPACE       REVISION        UPDATED                                 STATUS          CHART                   APP VERSION
   adservice               default         1               2024-12-25 13:45:21.107530934 +0000 UTC deployed        microservice-0.1.0      1.16.0     
   cartservice             default         1               2024-12-25 13:45:16.205338049 +0000 UTC deployed        microservice-0.1.0      1.16.0     
   checkoutservice         default         1               2024-12-25 13:45:21.877660347 +0000 UTC deployed        microservice-0.1.0      1.16.0     
   currencyservice         default         1               2024-12-25 13:45:17.243966516 +0000 UTC deployed        microservice-0.1.0      1.16.0     
   emailservice            default         1               2024-12-25 13:45:15.426499712 +0000 UTC deployed        microservice-0.1.0      1.16.0     
   frontendservice         default         1               2024-12-25 13:45:22.656211545 +0000 UTC deployed        microservice-0.1.0      1.16.0     
   paymentservice          default         1               2024-12-25 13:45:18.019757777 +0000 UTC deployed        microservice-0.1.0      1.16.0     
   productcatalogservice   default         1               2024-12-25 13:45:19.571588266 +0000 UTC deployed        microservice-0.1.0      1.16.0     
   recommendationservice   default         1               2024-12-25 13:45:18.790548951 +0000 UTC deployed        microservice-0.1.0      1.16.0     
   rediscart               default         1               2024-12-25 13:45:14.626512509 +0000 UTC deployed        redis-0.1.0             1.16.0     
   shippingservice         default         1               2024-12-25 13:45:20.345913785 +0000 UTC deployed        microservice-0.1.0      1.16.0     
   
   ```

5. **Uninstall Releases**:
   Run the `uninstall.sh` script to remove all releases:
   ```bash
   ./uninstall.sh
   
   release "rediscart" uninstalled
   release "emailservice" uninstalled
   release "cartservice" uninstalled
   release "currencyservice" uninstalled
   release "paymentservice" uninstalled
   release "recommendationservice" uninstalled
   release "productcatalogservice" uninstalled
   release "shippingservice" uninstalled
   release "adservice" uninstalled
   release "checkoutservice" uninstalled
   release "frontendservice" uninstalled
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
   
   helm version is too low, the current version is 3.13.0+g825e86f, the required version is 3.15.4
   use: 'https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3' [y/n]: y
   Helm v3.16.3 is available. Changing from version v3.13.0.
   Downloading https://get.helm.sh/helm-v3.16.3-linux-amd64.tar.gz
   Verifying checksum... Done.
   Preparing to install helm into /usr/local/bin
   helm installed into /usr/local/bin/helm
   ```
 
4. **Run Helmfile Sync**:
   Deploy all microservices using `helmfile sync`:
   ```bash
   helmfile sync
   
   Building dependency release=rediscart, chart=charts/redis
   Building dependency release=emailservice, chart=charts/microservice
   Building dependency release=cartservice, chart=charts/microservice
   Building dependency release=currencyservice, chart=charts/microservice
   Building dependency release=paymentservice, chart=charts/microservice
   Building dependency release=recommendationservice, chart=charts/microservice
   Building dependency release=productcatalogservice, chart=charts/microservice
   Building dependency release=shippingservice, chart=charts/microservice
   Building dependency release=adservice, chart=charts/microservice
   Building dependency release=checkoutservice, chart=charts/microservice
   Building dependency release=frontendservice, chart=charts/microservice
   Upgrading release=rediscart, chart=charts/redis, namespace=
   Upgrading release=emailservice, chart=charts/microservice, namespace=
   Upgrading release=cartservice, chart=charts/microservice, namespace=
   Upgrading release=currencyservice, chart=charts/microservice, namespace=
   Upgrading release=paymentservice, chart=charts/microservice, namespace=
   Upgrading release=recommendationservice, chart=charts/microservice, namespace=
   Upgrading release=productcatalogservice, chart=charts/microservice, namespace=
   Upgrading release=shippingservice, chart=charts/microservice, namespace=
   Upgrading release=adservice, chart=charts/microservice, namespace=
   Upgrading release=checkoutservice, chart=charts/microservice, namespace=
   Upgrading release=frontendservice, chart=charts/microservice, namespace=
   Release "checkoutservice" does not exist. Installing it now.
   NAME: checkoutservice
   LAST DEPLOYED: Wed Dec 25 17:54:59 2024
   NAMESPACE: default
   STATUS: deployed
   REVISION: 1
   TEST SUITE: None
   
   Listing releases matching ^checkoutservice$
   Release "rediscart" does not exist. Installing it now.
   NAME: rediscart
   LAST DEPLOYED: Wed Dec 25 17:54:59 2024
   NAMESPACE: default
   STATUS: deployed
   REVISION: 1
   TEST SUITE: None
   
   Listing releases matching ^rediscart$
   Release "recommendationservice" does not exist. Installing it now.
   NAME: recommendationservice
   LAST DEPLOYED: Wed Dec 25 17:54:59 2024
   NAMESPACE: default
   STATUS: deployed
   REVISION: 1
   TEST SUITE: None
   
   Listing releases matching ^recommendationservice$
   Release "frontendservice" does not exist. Installing it now.
   NAME: frontendservice
   LAST DEPLOYED: Wed Dec 25 17:54:59 2024
   NAMESPACE: default
   STATUS: deployed
   REVISION: 1
   TEST SUITE: None
   
   Listing releases matching ^frontendservice$
   Release "paymentservice" does not exist. Installing it now.
   NAME: paymentservice
   LAST DEPLOYED: Wed Dec 25 17:54:59 2024
   NAMESPACE: default
   STATUS: deployed
   REVISION: 1
   TEST SUITE: None
   
   Listing releases matching ^paymentservice$
   Release "adservice" does not exist. Installing it now.
   NAME: adservice
   LAST DEPLOYED: Wed Dec 25 17:54:59 2024
   NAMESPACE: default
   STATUS: deployed
   REVISION: 1
   TEST SUITE: None
   
   Listing releases matching ^adservice$
   Release "productcatalogservice" does not exist. Installing it now.
   NAME: productcatalogservice
   LAST DEPLOYED: Wed Dec 25 17:54:59 2024
   NAMESPACE: default
   STATUS: deployed
   REVISION: 1
   TEST SUITE: None
   
   Listing releases matching ^productcatalogservice$
   Release "emailservice" does not exist. Installing it now.
   NAME: emailservice
   LAST DEPLOYED: Wed Dec 25 17:54:59 2024
   NAMESPACE: default
   STATUS: deployed
   REVISION: 1
   TEST SUITE: None
   
   Listing releases matching ^emailservice$
   Release "currencyservice" does not exist. Installing it now.
   NAME: currencyservice
   LAST DEPLOYED: Wed Dec 25 17:54:59 2024
   NAMESPACE: default
   STATUS: deployed
   REVISION: 1
   TEST SUITE: None
   
   Listing releases matching ^currencyservice$
   Release "shippingservice" does not exist. Installing it now.
   NAME: shippingservice
   LAST DEPLOYED: Wed Dec 25 17:54:59 2024
   NAMESPACE: default
   STATUS: deployed
   REVISION: 1
   TEST SUITE: None
   
   Listing releases matching ^shippingservice$
   Release "cartservice" does not exist. Installing it now.
   NAME: cartservice
   LAST DEPLOYED: Wed Dec 25 17:54:59 2024
   NAMESPACE: default
   STATUS: deployed
   REVISION: 1
   TEST SUITE: None
   
   Listing releases matching ^cartservice$
   rediscart       default         1               2024-12-25 17:54:59.83794862 +0000 UTC  deployed        redis-0.1.0     1.16.0     
   
   productcatalogservice   default         1               2024-12-25 17:54:59.876799025 +0000 UTC deployed        microservice-0.1.0      1.16.0     
   
   currencyservice default         1               2024-12-25 17:54:59.875466737 +0000 UTC deployed        microservice-0.1.0      1.16.0     
   
   shippingservice default         1               2024-12-25 17:54:59.884697457 +0000 UTC deployed        microservice-0.1.0      1.16.0     
   
   emailservice    default         1               2024-12-25 17:54:59.848248191 +0000 UTC deployed        microservice-0.1.0      1.16.0     
   
   paymentservice  default         1               2024-12-25 17:54:59.864740169 +0000 UTC deployed        microservice-0.1.0      1.16.0     
   
   frontendservice default         1               2024-12-25 17:54:59.855709571 +0000 UTC deployed        microservice-0.1.0      1.16.0     
   
   adservice       default         1               2024-12-25 17:54:59.810961795 +0000 UTC deployed        microservice-0.1.0      1.16.0     
   
   checkoutservice default         1               2024-12-25 17:54:59.932554692 +0000 UTC deployed        microservice-0.1.0      1.16.0     
   
   cartservice     default         1               2024-12-25 17:54:59.836893821 +0000 UTC deployed        microservice-0.1.0      1.16.0     
   
   recommendationservice   default         1               2024-12-25 17:54:59.852502837 +0000 UTC deployed        microservice-0.1.0      1.16.0     
   
   
   UPDATED RELEASES:
   NAME                    NAMESPACE   CHART                 VERSION   DURATION
   checkoutservice                     charts/microservice   0.1.0          19s
   rediscart                           charts/redis          0.1.0          19s
   recommendationservice               charts/microservice   0.1.0          19s
   frontendservice                     charts/microservice   0.1.0          19s
   paymentservice                      charts/microservice   0.1.0          19s
   adservice                           charts/microservice   0.1.0          19s
   productcatalogservice               charts/microservice   0.1.0          19s
   emailservice                        charts/microservice   0.1.0          19s
   currencyservice                     charts/microservice   0.1.0          19s
   shippingservice                     charts/microservice   0.1.0          19s
   cartservice                         charts/microservice   0.1.0          19s

   ```

   This step builds dependencies and deploys all microservices defined in the `Helmfile` configuration.

5. **Verify Helm Releases and Pods**:
   - Check Helmfile releases:
     ```bash
     helmfile list
     
      NAME                    NAMESPACE       ENABLED INSTALLED       LABELS  CHART                   VERSION
      rediscart                               true    true                    charts/redis                   
      emailservice                            true    true                    charts/microservice            
      cartservice                             true    true                    charts/microservice            
      currencyservice                         true    true                    charts/microservice            
      paymentservice                          true    true                    charts/microservice            
      recommendationservice                   true    true                    charts/microservice            
      productcatalogservice                   true    true                    charts/microservice            
      shippingservice                         true    true                    charts/microservice            
      adservice                               true    true                    charts/microservice            
      checkoutservice                         true    true                    charts/microservice            
      frontendservice                         true    true                    charts/microservice 
   
     ```
   - Check Kubernetes pods:
     ```bash
     kubectl get pods
 
      NAME                                     READY   STATUS    RESTARTS   AGE
      adservice-d7ff4646b-9vt68                1/1     Running   0          2m28s
      adservice-d7ff4646b-qgxfc                1/1     Running   0          2m28s
      cartservice-7496fc6c9b-2cvkc             1/1     Running   0          2m28s
      cartservice-7496fc6c9b-qncd4             1/1     Running   0          2m28s
      checkoutservice-564cdbcbc5-bqbqs         1/1     Running   0          2m28s
      checkoutservice-564cdbcbc5-mqfcv         1/1     Running   0          2m28s
      currencyservice-69c577d9f8-t8scp         1/1     Running   0          2m27s
      currencyservice-69c577d9f8-tnvbw         1/1     Running   0          2m27s
      emailservice-c6b75bdfc-h62wh             1/1     Running   0          2m28s
      emailservice-c6b75bdfc-wwdlx             1/1     Running   0          2m28s
      frontend-7b5c58f8c-bnv4w                 1/1     Running   0          2m28s
      frontend-7b5c58f8c-n5dl9                 1/1     Running   0          2m28s
      paymentservice-5d6865d4c-kmdl2           1/1     Running   0          2m28s
      paymentservice-5d6865d4c-wvw4g           1/1     Running   0          2m28s
      productcatalogservice-fbfc699d9-cpc4j    1/1     Running   0          2m28s
      productcatalogservice-fbfc699d9-zpvpc    1/1     Running   0          2m28s
      recommendationservice-6c4fdb4f46-gt6th   1/1     Running   0          2m28s
      recommendationservice-6c4fdb4f46-pnz4g   1/1     Running   0          2m28s
      redis-cart-86dd5f47f4-95jbn              1/1     Running   0          2m28s
      shippingservice-79bc74547c-dt4jw         1/1     Running   0          2m28s
      shippingservice-79bc74547c-th6t5         1/1     Running   0          2m28s
     ```

6. **Access the Application**:
   Use the LoadBalancer URL to access the deployed microservices. You can find the URL using:
   ```bash
   kubectl get svc frontend
   
   NAME       TYPE           CLUSTER-IP     EXTERNAL-IP                                                               PORT(S)        AGE
   frontend   LoadBalancer   10.100.2.219   a318d4fc73cb743718aeacbd30660aeb-1184559924.us-east-1.elb.amazonaws.com   80:32086/TCP   3m50s
   ```
   View the application in web browser. 

7. **Cleanup**:
   To uninstall all the releases, run the following command:
   ```bash
   helmfile destroy
   
   Building dependency release=frontendservice, chart=charts/microservice
   Building dependency release=shippingservice, chart=charts/microservice
   Building dependency release=productcatalogservice, chart=charts/microservice
   Building dependency release=recommendationservice, chart=charts/microservice
   Building dependency release=paymentservice, chart=charts/microservice
   Building dependency release=currencyservice, chart=charts/microservice
   Building dependency release=cartservice, chart=charts/microservice
   Building dependency release=emailservice, chart=charts/microservice
   Building dependency release=rediscart, chart=charts/redis
   Building dependency release=checkoutservice, chart=charts/microservice
   Building dependency release=adservice, chart=charts/microservice
   Deleting frontendservice
   Deleting checkoutservice
   Deleting rediscart
   Deleting adservice
   Deleting shippingservice
   Deleting productcatalogservice
   Deleting recommendationservice
   Deleting paymentservice
   Deleting currencyservice
   Deleting cartservice
   Deleting emailservice
   release "cartservice" uninstalled
   release "checkoutservice" uninstalled
   release "adservice" uninstalled
   release "frontendservice" uninstalled
   release "emailservice" uninstalled
   release "currencyservice" uninstalled
   release "rediscart" uninstalled
   release "recommendationservice" uninstalled
   release "paymentservice" uninstalled
   release "shippingservice" uninstalled
   release "productcatalogservice" uninstalled
   ```

   Verify that all pods are terminated:
   ```bash
   kubectl get pods
   ```

## Notes
- Ensure Kubernetes and Helm are installed and configured correctly before starting the deployment.
- Helmfile simplifies the management of multiple Helm releases and dependencies.
- Check for resource allocation and node capacity when deploying large numbers of microservices.

## Conclusion
This project illustrates a step-by-step approach to deploying microservices using Helm and Helmfile. These tools help manage Kubernetes applications efficiently, providing flexibility and scalability.
