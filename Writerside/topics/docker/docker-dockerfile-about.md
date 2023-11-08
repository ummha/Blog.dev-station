# Dockerfile 작성하기

## Dockerfile 이란?

dockerfile은 도커 이미지를 생성하기 위한 스크립트 파일입니다.

여러 키워드를 사용하여 dockerfile을 작성하면 빌드를 보다 쉽게 수행 할 수 있습니다.

## Dockerfile Instruction

dockerfile에서 사용되는 주요 인트럭션(키워드)은 아래와 같습니다.

FROM
: From 키워드를 사용하여 base가 되는 image를 지정합니다. 주로 OS 이미지나 런타임 이미지를 지정합니다.

RUN
: 이미지를 빌드할 때 사용하는 커맨드를 설정할 때 사용합니다.

ADD
: 이미지에 호스트의 파일이나 폴더를 추가하기 위해 사용합니다. 만약 이미지에 복사하려는 디렉토리가 존재하지 않으면 docker가 자동으로 생성합니다.

COPY
: 
- 호스트 환경의 파일이나 폴더를 이미지 안으로 복사하기 위해 사용합니다. 
- `ADD`와 동일하게 동작하지만 가장 확실한 차이점은 URL을 지정하거나, 압축파일을 자동으로 풀지 않습니다.

EXPOSE
: 이미지가 통신에 필요한 포트를 지정할 때 사용합니다.

ENV
: 
- 환경 변수를 지정할 때 사용합니다. 여기서 설정한 변수는 `$name`, `${name}`의 형태로 사용할 수 있습니다. 
- 추가로 다음과 같은 문법을 사용하여 사용할 수도 있습니다. :
  
    e.i. `${name:-else}`: name 정의가 안되어 있다면 'else'가 사용된다는 설정입니다.

CMD
: 
- 도커 컨테이너가 실행될 때 실행할 커맨드를 지정합니다.
- `RUN`과 비슷하지만 `CMD`는 도커 이미지를 빌드할 때 실행되는 것이 아니라 컨테이너를 시작할 때 실행됩니다.

ENTRYPOINT
: 도커 이미지가 실행될 때 사용되는 기본 커맨드를 지정합니다. (강제)

WORKDIR
: 
- `RUN`, `CMD`, `ENTRYPOINT` 등을 사용한 커맨드를 실행하는 디렉토리를 지정합니다.
- `-w` 옵션으로 오버라이딩 할 수 있습니다.

VOLUME
: 
- 퍼시스턴스(persistent) 데이터를 저장할 경로를 지정할 때 사용힙니다.
- 이 설정을 통해서 호스트의 디렉토리를 도커 컨테이너에 연결할 수 있습니다.
- 주로 휘발성으로 사용되면 안되는 데이터를 저장할 때 사용합니다. (e.g. 데이터베이스)

기타 옵션
:
- SHELL
- LABEL
- USER
- ARG
- STOPSIGNAL
- HEALTHCHECK

## Docker Build

dockerfile을 실행하기 위해서는 `docker build` 커맨드를 사용합니다.

```Bash
docker build ${옵션} ${dockerfile 디렉토리}
```

{collapsible="true" default-state="collapsed"}
e.g.
: 
```Bash
docker build -t test .
```
여기서 `-t` 옵션은 빌드될 이미지 이름을 설정할 때 사용한다.

생성된 이미지를 컨테이너로 실행하기 위해서는 run 커맨드를 사용합니다.

```Bash
docker run --name ${컨테이너 이름} -p ${호스트 포트}:${도커 포트} ${이미지} 
```

{collapsible="true" default-state="collapsed"}
e.g.
:
```Bash
docker run --name test_app -p 80:80 test
```