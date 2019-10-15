# Reset

돌아 가려는 커밋으로 리파지토리는 재설정되고, 해당 커밋 이후의 이력은 사라진다.

```shell
git reset <옵션> <돌아가고싶은 커밋>
```

## hard

돌아가려는 이력이후의 모든 내용을 지워 버립니다.

## soft

돌아가려 했던 이력으로 되돌아 갔지만, 이후의 내용이 지워지지 않고, 해당 내용의 인덱스(또는 스테이지)도 그대로 있습니다. 바로 다시 커밋할 수 있는 상태로 남아있는 것입니다.

## mixed (default)

역시 이력은 되돌려집니다. 이후에 변경된 내용에 대해서는 남아있지만, 인덱스는 초기화 됩니다. 커밋을 하려면 다시 변경된 내용은 추가해야 하는 상태입니다.

> https://git-scm.com/book/ko/v2/Git-%EB%8F%84%EA%B5%AC-Reset-%EB%AA%85%ED%99%95%ED%9E%88-%EC%95%8C%EA%B3%A0-%EA%B0%80%EA%B8%B0

> http://www.devpools.kr/2017/02/05/%EC%B4%88%EB%B3%B4%EC%9A%A9-git-%EB%90%98%EB%8F%8C%EB%A6%AC%EA%B8%B0-reset-revert/
