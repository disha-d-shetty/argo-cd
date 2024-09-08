# For simple setup of argo-cd on k8s
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