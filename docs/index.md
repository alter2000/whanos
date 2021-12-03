# Whanos

Re: Requirements: read the pdf

Almost all technical choices have been made to favor convenience over long-term
stability, some for developer convenience (lack of devops time) and some for
end user convenience (github integration), or both (using existing deployment
tools and recipes to bootstrap most of infrastructure). Where it was possible
and feasible, user convenience/accordance to the requirements PDF has been
sought after if there is an already existing guide for said feature (there
generally is, although possibly out of date).

## Setup

### Kubernetes

Set up AKS credentials (<https://portal.azure.com>), create resource group,
create k8s cluster on cheapest possible plan (3 + 1 usable node, nevermind the
pdf since costs aren't guaranteed to be covered by epitech).

Deploy on Azure Kubernetes Service, set up container registry following
<https://docs.microsoft.com/en-us/azure/container-registry/container-registry-get-started-azure-cli>.
Using k8s v1.22.4, Helm v3.7.1.

**NOTE:** some secrets stored in git for ease of use, whole project
requirements seem to be patched together from the Azure doc site (somehow
only need 2-3 guides to deploy whole project, all found within the Azure
documentation portal).

### Jenkins

- Follow <https://www.jenkins.io/doc/book/installing/kubernetes/> (using
  mainline `jenkinsci/jenkins`, not LTS)
- Ensure that there is:
  - Pipeline support: <https://www.jenkins.io/doc/book/pipeline/>
  - K8s-cd: <https://plugins.jenkins.io/kubernetes-cd/>
  - Github connectivity: <https://plugins.jenkins.io/github/>
- Helm install file (`../jenkins/values.yml`) + Config-as-Code should handle
  the rest
- Link github repos to jenkins.
