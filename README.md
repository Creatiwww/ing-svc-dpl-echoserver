# echo-server deploy to K8s
This is a python socket server that echos back any http request made to it.

## Prerequisits

## Build Docker
```
  docker build -t echo-server:latest .
  docker tag echo-server:latest creatiwww/devops_test_faraway:amd64-latest
  docker push creatiwww/echo-server:amd64-latest
```

## Deploy to K8s
```
  kubectl apply -f deploy/k8s/manifests -n playground
```

## Test result
```
ING_URL=$(kubectl get ingress ingress-resource -o jsonpath="{.status.loadBalancer.ingress[0].ip}" -n playground)
curl -XPOST $ING_URL/echo-server -d '{"Hello":"World!"}'
```