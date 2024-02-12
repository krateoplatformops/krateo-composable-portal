# Krateo Gateway Helm Chart

This is a [Helm Chart](https://helm.sh/docs/topics/charts/) for [Krateo Composable Portal](https://github.com/krateoplatformops/krateo-composable-portal).

## How to install

```sh
helm repo add krateo https://charts.krateo.io
helm repo update krateo
helm install krateo-composable-portal krateo/krateo-composable-portal
```

## Krateo Quickstart

This guide provides a step-by-step walkthrough of the bash script used for deploying the Krateo platform on a Kubernetes environment using Helm and kind.

## Prerequisites

- Linux OS
- [Helm](https://helm.sh/docs/intro/install/) CLI installed
- [Kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl) CLI installed
- [Kind](https://kind.sigs.k8s.io/docs/user/quick-start/#installation) CLI installed

## Steps

### Execute script

```sh
chmod +x kind.sh
./kind.sh
```

### This is what the script does

1. **Enable Script Debugging**
   - Activates bash debugging to output each command before it's executed, which aids in troubleshooting.

2. **Add Helm Repository**
   - Adds the Krateo Helm chart repository, making its charts available for deployment.

3. **Update Helm Repository**
   - Updates the local Helm chart repository cache to ensure the latest charts are fetched.

4. **Create Kubernetes Cluster with kind**
   - Uses `kind` to create a new Kubernetes cluster named `krateo-quickstart` with specific port mappings for Krateo services and a predefined API server port.

5. **Install Krateo Frontend**
   - Deploys the Krateo frontend service using Helm, setting it to be accessible on a NodePort and configuring various environment variables.

6. **Copy Kubernetes CA Certificates**
   - Copies the Kubernetes cluster's CA certificate and key from the control plane node to the local machine.

7. **Export CA Certificates as Environment Variables**
   - Encodes the CA certificate and key in base64 and stores them in environment variables.

8. **Create a Kubernetes Secret for Krateo Gateway**
   - Applies a Kubernetes manifest to create a secret containing the CA key for the Krateo Gateway service.

9. **Install Krateo Gateway**
   - Deploys the Krateo Gateway service with Helm, setting it to be accessible on a NodePort and configuring health checks and environment variables.

10. **Install AuthN Service**
    - Deploys an authentication service with Helm, configuring it for NodePort access and setting various environment variables related to Kubernetes and the AuthN service.

11. **Install Krateo BFF**
    - Deploys the Krateo Backend-for-Frontend (BFF) service with Helm, making it accessible on a NodePort and setting CORS policy.

12. **Configure Kubernetes Resources and Users**
    - Applies a series of Kubernetes manifests to set up namespaces, secrets, roles, role bindings, and custom resources for users, layouts, and widgets. This includes creating a demo-system namespace, configuring user access, and defining UI components and endpoints.

This script sets up a complete Krateo platform environment on a local Kubernetes cluster, ready for development or testing. It meticulously configures networking, security, and user access, providing a comprehensive setup for exploring the capabilities of the Krateo platform.
