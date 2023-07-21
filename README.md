## Project Description

This project is designed to create a 5 node Kubernetes cluster, create two different namespaces for groups with different authorizations, deploy the Wordpress application in both environments, store long-term data in persistent volumes, securely process sensitive information, and ensure that applications run securely and stably with various other configurations.

## Task

### Kubernetes Tasks

| No | Tasks Description                                                                                                            |
|----|-------------------------------------------------------------------------------------------------------------------------------|
| 1  | Create a Kubernetes cluster with 5 nodes: 1 Master + 4 Worker Nodes.                                                          |
| 2  | Create two namespaces named "test" and " production"                                                                         |
| 3  | Create a role that grants the "junior" group full permissions (read, list, create, etc.) in the "test" namespace and read and list permissions only in the "production" namespace. Similarly, create a role for the "senior" group that grants full permissions in both "production" and "test" namespaces and read and list permissions for other resources in the cluster. Associate these roles with their respective groups. |
| 4  | Install an "ingress controller" of your choice (e.g., nginx, traefik, haproxy).                                              |
| 5  | Configure 3 worker nodes to be dedicated for deployments in the "production" environment. Ensure that other pods are not scheduled on these nodes. |
| 6  | Deploy the WordPress application in both "test" and "production" namespaces using the "wordpress:latest" and "mysql:5.6" images.
| 7  | Expose the WordPress application deployed in the "test" namespace as "testblog.example.com" and the one in the "production" namespace as "companyblog.example.com" using Ingress. |
| 8  | In the "production" namespace, create a deployment with 5 replicas using the "ozgurozturknet/k8s:v1" image. Allow a rolling update strategy to update a maximum of 2 pods simultaneously. Define a "liveness probe" that queries the "/healthcheck" endpoint and a "readiness probe" that queries the "/ready" endpoint. |
| 9  | Make the deployment from the previous task accessible from outside the cluster using a "LoadBalancer" type service. |
| 10 | Scale down the deployment to 3 replicas, then scale it up to 10 replicas. After that, update the deployment to use the "ozgurozturknet/k8s:v2" image. |
| 11 | Deploy the "fluentd" application as a "DaemonSet" in the cluster.                                                              |
| 12 | Deploy a 2-node MongoDB cluster as a "StatefulSet" in the cluster and ensure that it is running correctly.                    |
| 13 | Create a "Service Account" with read and list permissions on all objects in the cluster. Create a pod that uses this service account and use "curl" to list all pods in the cluster. |
| 14 | Evacuate all pods from one of the worker nodes and then prevent new pods from being scheduled on that node.                  |

## Notes About Tasks

`For the Sixth Step`
- Use a "ClusterIP" type service to make MySQL accessible from within the cluster.
- Store long-term data for both applications using persistent volumes.
- Avoid storing sensitive information (e.g., passwords) in the application or yaml files.
- Schedule both applications on the same worker node.
- Define CPU and memory resource limits for both applications. |

## Thanks

- It was a great kubernetes tutorial. We crowned the final with this magnificent project. Here, I would like to thank my teacher @Özgür Öztürk for his efforts.

`https://www.udemy.com/course/kubernetes-temelleri/`
