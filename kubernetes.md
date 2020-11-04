# Kubernetes useful commands

## Pods

Get all pods for a workspace
`kubectl --context <context> get pods -n <namespace>`

## Logs

Get logs of a particular pod. You may need to see all of the pods to find out the pod name
`kubectl --context <context> logs <pod-name> -n <namespace>`

## Services

View all of the services in a namespace

`kubectl --context <context> get service -n <namespace>`

## Secrets

`kubectl --context <context> -n <namespace> get secrets`

`kubectl --context <context> -n <namespace> get secrets <secret-name>`

Get secrets and base64 decode the result with JQ

`kubectl --context <context> -n <namespace> get secrets <secret name> -o json | jq &#39;.data | map_values(@base64)&#39;`

## Config maps

`kubectl --context <context> get configmap <service name>`
`kubectl --context <context> get configmap <service name> -o yaml`
`kubectl --context <context> get configmap <service name> -o json`

## With caution

`kubectl --context <context> rollout restart deployment/<service name> -n <namespace>`

## Helm

### Secrets

`helm install <secret name> pmconnect/secret -n <namespace> --set SecretId=<aws secret namespace> --set type=tls --kube-context <context>`
`helm delete <secret name> pmconnect/secret -n <namespace> --kube-context <context>`

### Templates

`helm template <domain> pmconnect/domains -f <file> -n <namespace>`
