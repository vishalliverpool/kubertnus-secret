# kubertnus-secretConnect to a Kubernetes Cluster
The first step is to ensure that you are connected to a Kubernetes cluster, either local or remote. The cluster setup and configuration used in this post can be found in this public repository.

You can verify the context of your cluster connection with the following command:


kubectl config current-context
Create a Secret Manifest File
Once your connection is established, proceed to create a manifest file for a Secret. The Secret will contain key-value pairs for a username and password.

You can base64-encode the values for your secret as follows:


echo -n 'jsmith' | base64
echo -n 'mysecretpassword' | base64
Note that the outputs from the previous commands need to be pasted into the YAML file in the next section.


kubectl create -f secret.yaml using YAML file in repo

Mount Secret Values with Volumes as you need to check env-pod.yaml

kubectl create -f env-pod.yaml 

Once the container is up , 

kubectl exec volume-pod -- ls /etc/config/secret
kubectl exec volume-pod -- cat /etc/config/secret/username

![image](https://user-images.githubusercontent.com/42957382/185826396-cf323b52-8731-4d3e-ade7-06f94b28b0c4.png)
