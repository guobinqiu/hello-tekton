# Tekton Practice

> https://tekton.dev/

构建方式:

```
  1. PipelineRun -> Pipeline -> Task -> Step
  2. TaskRun -> Task -> Step
  3. EventListener -> TriggerTemplate -> PipelineRun
  4. EventListener -> TriggerTemplate -> TaskRun
```

Tekton设计的粒度很细, 我们选择从TaskRun开始构建比从PiplineRun开始构建简单得多,另外我们手动执行测试用例也是不需要事件触发的, 所以采用方式2

为了打好基础, 我们不用`Tekton Catalog`, 纯手写`git`和`docker`操作

## Testcases

### git

[test1.yaml](git/test1.yaml) (Recomended)

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

[test1.yaml](docker/test1.yaml) (Recomended)

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
or
ssh-keyscan github.com | base64 | tr -d '\n'
```

.dockerconfigjson:

```
cat ~/.docker/config.json | base64 | tr -d '\n'
```
