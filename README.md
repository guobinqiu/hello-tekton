# Tekton Pratice

方式:
  1. PipelineRun -> Pipeline -> Task -> steps
  2. TaskRun -> Task -> steps
  3. EventListener -> TriggerTemplate -> PipelineRun
  4. EventListener -> TriggerTemplate -> TaskRun
   

基于方式2, 不使用tekton catalog资源库, 手写git和docker, 测试私有库(因公有库无需认证)

## Testcases

### git

git1.yaml

- ssh auth
- with sa

git2.yaml

- ssh auth without known_hosts
- with sa

git3.yaml

- ssh auth
- without sa

git4.yaml

- basic auth
- with sa

git5.yaml

- basic auth
- without sa

git6.yaml

- without ssh auth
- without basic auth 
- without sa

### docker

docker1.yaml

- ssh auth
- with sa

docker2.yaml

- ssh auth
- without sa

docker3.yaml

- basic auth
- with sa

docker4.yaml

- basic auth
- without sa

docker5.yaml

- without ssh auth
- without basic auth
- without sa
    
### Get auth string

ssh-privatekey:

```
cat ~/.ssh/id_rsa | base64 | tr -d '\n'
```

known_host:

```
cat ~/.ssh/known_hosts | base64 | tr -d '\n'
```
or
```
ssh-keyscan github.com | base64 | tr -d '\n'
```

.dockerconfigjson:

```
cat ~/.docker/config.json | base64 | tr -d '\n'
```
