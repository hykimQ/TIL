# 🎞animation

## Example

```css
<!doctype html>
<html lang="ko">
    <head>
        <meta charset="utf-8">
        <title>CSS</title>
        <style>
            @keyframes big {
                from {
                    width: 20px;
                    height: 20px;
                }
                to {
                    width: 200px;
                    height: 200px;
                }
            }
            div#jb {
                margin: 30px auto;
                width: 20px;
                height: 20px;
                background-color: orange;
                animation-name: big;
                animation-duration: 2s;
                animation-timing-function: linear;
                animation-delay: 2s;
                animation-iteration-count: 4;
                animation-direction: alternate;
                animation-fill-mode: none;
                animation-play-state: running;
            }
        </style>
    </head>
    <body>
        <div id="jb"></div>
    </body>
</html>
```

## @keyframes

- 어떤 모양에서 어떤 모양으로 바꿀지 결정
- 이름은 big으로 지음

## animation-name

- 어떤 @keyframes를 사용할지 정함
- 예제에서는 big을 사용

## animation-duration

- 애니메이션의 총 시간을 결정
- 예제에서는 2초 동안 애니메이션을 시작하고 끝냄

## animation-timing-function

- 애니메이션의 진행 속도를 결정
- 예제에서는 등속으로 진행

## animation-delay

- 애니메이션을 시작하기 전에 대기하는 시간
- 예제에서는 2초 대기 후 시작

## animation-iteration-count

- 애니메이션의 반복횟수
- 예제에서는 4회 반복

## animation-direction

- 애니메이션 진행 방향
- 예제에서는 예제에서는 정방향 → 역방향 → 정방향 → 역방향 → …으로 진행(alternative)

## animation-fill-mode

- 애니메이션을 마친 후 어떤 상태로 만들지 결정

## animation-play-state

- 애니메이션을 진행할 지 멈출지 결정
