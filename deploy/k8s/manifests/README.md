# echo-server deploy to K8s

This is a python socket server that echos back any http request made to it.


## Deploy
```
  docker build -t echo-server:latest .
  docker tag echo-server:latest creatiwww/devops_test_faraway:amd64-latest
  docker push creatiwww/echo-server:amd64-latest
  # test
  ING_URL=$(kubectl get ingress ingress-resource -o jsonpath="{.status.loadBalancer.ingress[0].ip}" -n playground)
  curl -XPOST $ING_URL -d '{"Hello":"World!"}'
```