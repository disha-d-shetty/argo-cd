# For simple setup of argo-cd and image updater on k8s:😎

**if you cannot have any clusters on local, then:**
    1. install microk8s on agent. It is available as action in marketplace and easier to install.
        addons - enable coreDNS, rbac, hostpath,
            - CoreDNS is a flexible, extensible DNS server that can serve as the Kubernetes cluster DNS. Like Kubernetes, the CoreDNS project is hosted by the CNCF.
            - RBAC uses a set of permissions to determine which actions users and workloads can perform on resources. Platform administrators create RBAC roles and bind them to authenticated users, such as service accounts or groups
            - A hostPath volume in an OpenShift Container Platform cluster mounts a file or directory from the host node’s file system into your pod. Most pods do not need a hostPath volume, but it does offer a quick option for testing should an application require it.
            details - https://docs.openshift.com/container-platform/3.11/install_config/persistent_storage/using_hostpath.html#:~:text=A%20hostPath%20volume%20in%20an,should%20an%20application%20require%20it.
        details - https://github.com/marketplace/actions/microk8s-action
    2. As i cant be able to access URLs of argo cd, so using ngrok(bot recommened as it ll breach security n stuff, beeter to setup ur own cluster n work on it)
        get auth code from dashboard(just by login)
        details - https://ngrok.com/docs/guides/getting-started/

**if you can have kind/minikube on local. Then, ignore the top steps:**
    1. choco install kind
    2. kind create cluster --name kind-2
    3. kind get clusters
    4. kubectl create namespace argocd
    5. kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
    6. kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
    7. kubectl port-forward svc/argocd-server -n argocd 8080:443

**argoCD-setup with image updater**
# argo-cd for k8s
Why argocd:
    1. Its installed on k8s cluster, so no need to give other agents like kubectl or helm secrets to access k8s/cloud platform.
    2. Visualise the status/health of components inside cluster>
    3. One time configuration, for each env, and can be accessed by other clusters under the same env.
    4. Every change made to k8s configuration files/source code is detected every 3 mins, and deployed automatically. This can be leveraged to everytime a commit is made.(add automate sync attribute to able it)
    5. Makes sure that source code, that is integrated with argo, overwrites any manual changes done on cluster. (add self heal true to avail this feature)

**Installation steps documented**: https://github.com/disha-d-shetty/argo-cd/blob/feature/initial-setup/ARGOCD%20IMAGE%20UPDATER%20INSTALLATION%20STEPS.docx 
