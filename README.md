# Tekton TaskRuns

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
- /etc/hosts

[test2.yaml](kube/test2.yaml)

- common auth
- No /etc/hosts

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

## Trigger

```
kustomize build ./trigger | kubectl apply -f -
curl -H 'content-Type: application/json' -d '{"username": "Tekton"}' http://hello-listener.example.com
```
<img width="1496" alt="Snipaste_2024-03-05_13-30-58" src="https://github.com/guobinqiu/hello-tekton/assets/5800822/6f7f741b-a1ab-4283-b289-9bbea345067e">
