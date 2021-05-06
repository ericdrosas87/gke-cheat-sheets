# Rosas - Useful notes for working with GKE

Ensure you have created a project in the GKE console, then set the environment variable PROJECT_ID to your GKE project ID.

Set the project ID for the gcloud tool:

```
gcloud config set project $PROJECT_ID
```

## Working with deployment, config, and secret resources

Creating cluster:

```
kubectl apply -f deploy.yaml
```

Applying config update:

```
kubectl apply -f config.yaml
```

Creating secrets:

```
kubectl create -f secrets.yaml
```

Inspect secrets:

```
kubectl get secret top-secret -o yaml
```

Apply secrets to pods:

```
kubectl apply -f config-after-secrets.yaml
```

## Now to verify the secrets made it into the container...

1. List gcloud instances:

```
gcloud compute instances list
```

2. SSH into an instance:

```
gcloud compute ssh <instance name> --zone=<instance zone>
```

3. In the instance, list the running processes and their container IDs:

```
docker ps -a
```

4. Exec into container

```
docker exec -it <container ID> sh
```

5. Echo secret

```
echo $SECRET_USERNAME
```