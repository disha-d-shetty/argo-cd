# For simple setup of argo-cd on k8s
1. install microk8s on agent. It is available as action in marketplace and easier to install.
    addons - enable coreDNS,
    CoreDNS is a flexible, extensible DNS server that can serve as the Kubernetes cluster DNS. Like Kubernetes, the CoreDNS project is hosted by the CNCF.
    details - https://github.com/marketplace/actions/microk8s-action
2. As i cant be able to access URLs of argo cd, so using ngrok(bot recommened as it ll breach security n stuff, beeter to setup ur own cluster n work on it)
    get auth code from dashboard(just by login)
    details - https://ngrok.com/docs/guides/getting-started/