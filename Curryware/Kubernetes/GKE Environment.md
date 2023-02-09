Run Terraform script
Deploy container - currently a manual process
Check with ```kubectl config view```
Set Secrets ```kubectl create secret generic datadog-secret --from-literal api-key=*** --from-literal app-key=***```
Install Datadog Agent ```helm install -f /Users/scot.curry/PycharmProjects/Datadog/Containers/values.yaml datadog datadog/datadog```

