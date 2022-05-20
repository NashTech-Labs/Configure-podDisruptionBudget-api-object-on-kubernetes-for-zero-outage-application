# Configure-podDisruptionBudget-api-object-on-kubernetes-for-zero-outage-application

## Pod Disruption Budget
A Pod Disruption Budget is a Kubernetes resource that defines the budget of voluntary disruption telling our k8s cluster a minimum threshold in terms of available pods that the cluster must maintain every time to ensure a baseline availability or performance. An Application Owner can create a PDB object for each application. A PDB limits the number of pods of a replicated application that are down simultaneously from voluntary disruptions. And will not let the number go below-mentioned the threshold.

## Deployment.yml
We have here a simple nginx deployment file with replicas equal to 4. To deploy the .yaml file, we have command
```
kubectl apply -f deploy.yml
```

## Pdb.yml
While creating a disruption budget, few things to keep in mind are: First, we determine a threshold using minAvailbale or maxUnavilable parameters in the spec section. And second, is matchLabels which must match your pod labels through these labels only PDB will look for which pods to check for.
So we have here our yml file with minAvailable equals 2. Which will make sure our pods dont go below the mentioned threshold. Command for the following will be
```
kubectl apply -f pdb.yml
```
