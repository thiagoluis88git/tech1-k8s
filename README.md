# FastFood API - Description

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Description](#description)
- [AWS](#aws)
- [Kubernetes](#kubernetes)
  - [Secrets](#secrets)
  - [Update Kubeconfig](#update-kubeconfig)

## Description

The Tech Challenge 1 aims to do a solution for a Fast Food restaurant. With this software, the rastaurant can do a all the process of for a place
that makes all steps of a fast food dish order, as:

## How to use

To use all the endpoints in this API, we can follow these sequence to simulate a customer making an order in a restaurant.
We can separate in three moments.

## AWS ##

The Fast food project uses `AWS Cloud` to host its software components. To know more about the **AWS configuration**, read: [AWS Readme](infra/README.md)

## Kubernetes

This application has all the K8S YAMLs to be applied in any cluster. 
To read the specific documentation, read: [Kubernetes README](infra/k8s/README.md)

### Secrets

Some environments are secret and don't have to be in Github. So, to avoid exposing data
it need to apply some local secrets to be stored in cluster before the deployments settlement 

Run this command after all the Deployments applied
```
kubectl apply -k infra/k8s/secret/
```

### Update Kubeconfig

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
