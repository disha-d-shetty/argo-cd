# Simple Setup of Argo CD and Image Updater on Kubernetes 😎

### Why Use Argo CD

1. **Integrated with Kubernetes**: No need to give other agents like kubectl or helm secrets to access Kubernetes/cloud platform.
2. **Visualization**: Visualize the status/health of components inside the cluster.
3. **One-Time Configuration**: Configure once for each environment, and it can be accessed by other clusters under the same environment.
4. **Automatic Deployment**: Detects changes to Kubernetes configuration files/source code every 3 minutes and deploys automatically. This can be leveraged to deploy on every commit (add automate sync attribute to enable this).
5. **Self-Healing**: Ensures that source code integrated with Argo CD overwrites any manual changes done on the cluster (add self-heal true to enable this feature).

## If You Cannot Have Any Clusters Locally
1. **Install MicroK8s on Agent**
    - MicroK8s is available as an action in the marketplace and is easier to install.
    - Enable the following addons:
        - **CoreDNS**: A flexible, extensible DNS server that can serve as the Kubernetes cluster DNS. [CoreDNS Project](https://coredns.io/)
        - **RBAC**: Uses a set of permissions to determine which actions users and workloads can perform on resources. [RBAC Documentation](https://kubernetes.io/docs/reference/access-authn-authz/rbac/)
        - **HostPath**: Mounts a file or directory from the host node’s file system into your pod. [HostPath Documentation](https://docs.openshift.com/container-platform/3.11/install_config/persistent_storage/using_hostpath.html#:~:text=A%20hostPath%20volume%20in%20an,should%20an%20application%20require%20it.)
    - More details: [MicroK8s Action](https://github.com/marketplace/actions/microk8s-action)
2. **Using Ngrok for Argo CD Access**
    - If you cannot access URLs of Argo CD, use Ngrok (Note: Ngrok may breach security; it's better to set up your own cluster).
    - Get the auth code from the dashboard (just by logging in).
    - More details: [Ngrok Documentation](https://ngrok.com/docs/guides/getting-started/)

## If You Can Use Kind/Minikube Locally

1. **Install Kind**
    ```sh
    choco install kind
    ```
2. **Create a Cluster**
    ```sh
    kind create cluster --name kind-2
    ```
3. **Get Clusters**
    ```sh
    kind get clusters
    ```
4. **Create Namespace for Argo CD**
    ```sh
    kubectl create namespace argocd
    ```
5. **Install Argo CD**
    ```sh
    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
    ```
6. **Get Initial Admin Password**
    ```sh
    kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
    ```
7. **Port Forward Argo CD Server**
    ```sh
    kubectl port-forward svc/argocd-server -n argocd 8080:443
    ```

## Argo CD Setup with Image Updater
### Installation Steps

For detailed installation steps, refer to the [Installation Documentation](https://github.com/disha-d-shetty/argo-cd/blob/feature/initial-setup/ARGOCD%20IMAGE%20UPDATER%20INSTALLATION%20STEPS.docx).
