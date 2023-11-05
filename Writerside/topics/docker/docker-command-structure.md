# 도커 명령어 구조

도커의 모든 명령은 <shortcut>docker</shortcut>로 시작하며 어떤 대상에게 명령어를 실행할 것인지 구분하며 작성하면 쉽습니다.

명령어 구조
: docker \[대상\] \[커맨드\] \[옵션\] \[인자\]

## 대상

container
: 
```Shell
docker image
```

image
: 
```Shell
docker image
```

volume
: 
```Shell
docker volume
```

network
: 
```Shell
docker network
```

## 커맨드

도커에서 사용할 수 있는 커맨드 목록은 아래와 같이 확인 할 수 있습니다.

```Shell
docker [대상] --help
```

위와 같은 방법으로 커맨드 수준을 높이고 뒤에 `--help`를 입력하여 커맨드 목록을 확인 할 수 있습니다.
