# For simple setup of argo-cd on k8s
1. install microk8s on agent. It is available as action in marketplace and easier to install.
    addons - enable coreDNS, rbac
    - CoreDNS is a flexible, extensible DNS server that can serve as the Kubernetes cluster DNS. Like Kubernetes, the CoreDNS project is hosted by the CNCF.
    - RBAC uses a set of permissions to determine which actions users and workloads can perform on resources. Platform administrators create RBAC roles and bind them to authenticated users, such as service accounts or groups
    details - https://github.com/marketplace/actions/microk8s-action
2. As i cant be able to access URLs of argo cd, so using ngrok(bot recommened as it ll breach security n stuff, beeter to setup ur own cluster n work on it)
    get auth code from dashboard(just by login)
    details - https://ngrok.com/docs/guides/getting-started/