# echo-server deploy to K8s

This is a python socket server that echos back any http request made to it.


## Deploy
```
  docker build -t echo-server:latest .
  docker tag echo-server:latest creatiwww/devops_test_faraway:amd64-latest
  docker push creatiwww/echo-server:latest
```