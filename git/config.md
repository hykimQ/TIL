# 🧵config

## git pull login 정보 기억

```shell
$ git config credential.helper store
```

## config 확인

```shell
$ git config --list

push.default=simple
user.name=YourName
user.email=YourEMail
core.repositoryformatversion=0
core.filemode=false
core.bare=false
core.logallrefupdates=true
core.symlinks=false
core.ignorecase=true
remote.origin.url=RepositoryURL
remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
branch.master.remote=origin
branch.master.merge=refs/heads/master
branch.develop.remote=origin
branch.develop.merge=refs/heads/develop
```

## config 설정

```shell
$ git config --global user.name "홍길동"

$ git config --global user.email "support@webisfree.com"
```
