#

## Prerequisites
 1. Identify the [MAX model](https://developer.ibm.com/code/exchanges/models/) that you want to deploy on this Kubernetes instance.
 2. In the model's GitHub repository (e.g. `https://github.com/IBM/MAX-Object-Detector`) locate the Kubernetes configuration file, which has a `.yaml` extension (e.g. `max-object-detector.yaml`).
 3. Open the configuration file in GitHub and switch the the **raw** view.
 4. Copy the content of the file (e.g. `https://raw.githubusercontent.com/IBM/MAX-Object-Detector/master/max-object-detector.yaml`) into a text editor. You'll need it in a later step when you deploy the model's Docker image.

## Deploy the MAX model Docker image to Kubernetes using the IBM Cloud web console

 1. Open the [Container resource page in the IBM Cloud Web Console](https://console.bluemix.net/containers-kubernetes/clusters) 
 2. Locate the cluster in the resource list if you already have access to a cluster. Otherwise create a new cluster. 
 2. Open the cluster's console page. 
 
### Identify the public IP address of your Kubernetes worker node(s) 
 1. Select the **Worker Nodes** tab.
 2. Note the **Public IP** address of each listed worker node. (There is only one if you are connected to a free cluster.)
 
### Deploy the MAX model Docker image

 1. Open the **Kubernetes Dashboard**.
 2. Click **+CREATE**.
 3. In the **CREATE FROM TEXT INPUT** tab paste the raw content of the Kubernetes configuration file. 
 
 The Kubernetes objects for the chosen model are created.
 
 ### Verify the deployment
 During a typical MAX model deployment three objects are created: a pod, a service and a deployment. These objects follow a simple naming scheme:
  * The pod is named `max-<model-id>-<hash>`, e.g. `max-object-detector-83B429...`.
  * The service is named `max-<model-id>`, e.g. `max-object-detector`.
  * The deployment is named `max-<model-id>` , e.g. `max-object-detector` (same as the service).
  
 To verify the deployment:
  1. In the Kubernetes dashboard locate the **Deployments** section. 
  2. Verify that a *Deployment* matching the expected name is listed. 
  3. Verify that a *Service* matching the expected name is listed. 
  4. Verify that a *Pod* matching the expected name is listed. The pod status should be listed as *Running*.
 
 ## Access the deployed MAX model
