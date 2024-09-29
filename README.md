# FastFood API - Kubernetes resources

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Description](#description)
- [How to use](#how-to-use)
- [AWS](#aws)
- [Kubernetes](#kubernetes)
  - [Secrets (Locally)](#secrets-locally)
  - [Update Kubeconfig (Locally)](#update-kubeconfig-locally)

## Description

The Tech Challenge 1 aims to do a solution for a Fast Food restaurant. This project is part of the entire solution. Here we have all the files to push the **Fast Food API image** to the `AWS EKS Cluster`.

## How to use

To push the API imag to the **EKS Cluster** just update the `deployment_fastfood_app.yml` file with the new version of the API. Then, just make a `Pull request` from `develop` to `main`. With the approval, the `CD pipeline` will do the job to deploy within the cluster.

## AWS

The Fast food project uses `AWS Cloud` to host its software components. To know more about the **AWS configuration**, read: [AWS Readme](infra/README.md)

## Kubernetes

This application has all the K8S YAMLs to be applied in any cluster. 
To read the specific documentation, read: [Kubernetes README](infra/k8s/README.md)

### Secrets (Locally)

Some environments are secret and don't have to be in Github. So, to avoid exposing data
it need to apply some local secrets to be stored in cluster before the deployments settlement 

Run this command after all the Deployments applied
```
kubectl apply -k infra/k8s/secret/
```

### Update Kubeconfig (Locally)

To add a new appointment to the EKS Cluster, we need to export some environment:

```
export AWS_ACCESS_KEY_ID="<KEY>"
export AWS_SECRET_ACCESS_KEY="<SECRET>"
export AWS_SESSION_TOKEN="<TOKEN>"
```

After that, we can run this command:
```
aws eks update-kubeconfig --region us-east-1 --name fastfood-cluster
```
