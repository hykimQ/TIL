# Git cherry-pick

## 다른 브랜치의 일부 커밋만 반영하고 싶을 때

```shell
# git branch
 master
 next-release
```

- master는 운영중인 브랜치
- next-release는 다음 대규모 개편 때 반영될 코드

오타가 발견 -> 두 브랜치에 적용되야함

```shell
# git checkout master
# git commit -am "fixed: typo"
# git log --pretty=oneline
b14b975 fixed: typo
9f57292 ....
....
```

master에 반영

next-release에 반영하려면

```shell
# git checkout next-release
# git cherry-pick b14b975
# git log --pretty=oneline
23fa1e76 fixed: typo
dd0f27c ...
...
```

- feature/BTS-### 같은 브랜치를 따서 merge 하는 방식으로 운영하는 경우, 굳이 cherry-pick을 이용할 필요까지는 없음. single master branch 위에서 작업하는 방식으로 진행하는 경우에 유용
