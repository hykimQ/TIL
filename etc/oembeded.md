# oEmbeded

oEmbed는 다른 사이트의 URL을 내장된 표현을 가능하게 하는 Format 입니다.
유저가 Resource 에 해당하는 링크를 입력할 때, 웹사이트들이 Resource를 직접 파싱하지 않고, 내장된 컨텐츠(사진과 비디오같은)를 보여줄 수 있게 하는 간단한 API 입니다.

consumer( 위에서 언급했던 Facebook 과 같은 SNS 혹은 커뮤니티) 는 아래와 같은 HTTP Request를 생성

```
http://www.youtube.com/oembed?url=http%3A//youtube.com/watch%3Fv%3DM3r2XDceM6A&format=json
```

그때 Provider( Youtube ) 는 oEmbed response를 돌려준다.

```javascript
{
    "version": "1.0",
    "type": "video",
    "provider_name": "YouTube",
    "provider_url": "http://youtube.com/",
    "width": 425,
    "height": 344,
    "title": "Amazing Nintendo Facts",
    "author_name": "ZackScott",
    "author_url": "http://www.youtube.com/user/ZackScott",
    "html":
        "<object width=\"425\" height=\"344\">
            <param name=\"movie\" value=\"http://www.youtube.com/v/M3r2XDceM6A&fs=1\"></param>
            <param name=\"allowFullScreen\" value=\"true\"></param>
            <param name=\"allowscriptaccess\" value=\"always\"></param>
            <embed src=\"http://www.youtube.com/v/M3r2XDceM6A&fs=1\"
                type=\"application/x-shockwave-flash\" width=\"425\" height=\"344\"
                allowscriptaccess=\"always\" allowfullscreen=\"true\"></embed>
        </object>",
}
```

> https://meetup.toast.com/posts/81
