A Helm Chart is a packaged Kubernetes deployment.  Datadog (the company) has created a Helm chart that correctly deploys the agent.  

The Datadog Helm chart is completely seperate from the application that the customer is building.  They may at some point put their application in a Helm chart, but it should be considered just a package manager for Kubernetes like apt, yum and homebrew are package managers for OS's.

Secrets need to be created for the API keys:
`kubectl create secret generic datadog-secret --from-literal api-key="***" --from-literal app-key="***" -n default`


**Commands**

helm repo add datadog https://helm.datadoghq.com  --the name is not fixed, it can be anything
helm repo list  --show any added repositories
helm template datadog/datadog -f values.yaml > values.txt | will list what the k8s manifest will look like.