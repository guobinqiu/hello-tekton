# Tekton Practice

> https://tekton.dev/

Ways of building:

```
  1. PipelineRun -> Pipeline -> Task -> Step
  2. TaskRun -> Task -> Step (this is what I picked up for testcases)
  3. EventListener -> TriggerTemplate -> PipelineRun
  4. EventListener -> TriggerTemplate -> TaskRun
```

We don't use `Tekton Catalog`, simply write `git` and `docker` manually

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

- ssh auth
- with sa

[test2.yaml](docker/test2.yaml)

- ssh auth
- without sa

[test3.yaml](docker/test3.yaml)

- basic auth
- with sa

[test4.yaml](docker/test4.yaml)

- basic auth
- without sa

[test5.yaml](docker/test5.yaml)

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
