# Tekton Practice

> https://tekton.dev/

Ways of building:

```
  1. PipelineRun -> Pipeline -> Task -> Step
  2. TaskRun -> Task -> Step (this was picked up for testcases)
  3. EventListener -> TriggerTemplate -> PipelineRun
  4. EventListener -> TriggerTemplate -> TaskRun
```

We don't use `Tekton Catalog`, simply get `github` and `dockerhub` working on private repositories manually

## Testcases

### git

[test1.yaml](git/test1.yaml) (Recommended)

- ssh auth
- with sa

[test2.yaml](git/test2.yaml)

- ssh auth without known_hosts
- with sa

[test3.yaml](git/test3.yaml)

- ssh auth
- without sa

[test4.yaml](git/test4.yaml)

- basic auth
- with sa

[test5.yaml](git/test5.yaml)

- basic auth
- without sa

[git6.yaml](git/test6.yaml)

- without ssh auth
- without basic auth 
- without sa

### docker

[test1.yaml](docker/test1.yaml) (Recommended)

- dockerconfigjson auth
- with sa

[test2.yaml](docker/test2.yaml)

- dockerconfigjson auth
- without sa

[test3.yaml](docker/test3.yaml)

- basic auth
- with sa

[test4.yaml](docker/test4.yaml)

- basic auth
- without sa

[test5.yaml](docker/test5.yaml)

- without dockerconfigjson auth
- without basic auth
- without sa

### kube

[test1.yaml](kube/test1.yaml)

- common auth
- with DNS

[test2.yaml](kube/test2.yaml)

- common auth
- without DNS

## Get auth string

### git

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

### docker

.dockerconfigjson:

```
cat ~/.docker/config.json | base64 | tr -d '\n'
```

### kube

config:

```
cat ~/.kube/config | base64 | tr -d '\n'
```
