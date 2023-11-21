# Docker Compose 작성하기

Dockerfile에 이어 docker-compose YAML 파일의 작성 양식을 살펴보고 각 설정 키워드의 의미와 명령어를 정리하겠습니다.

## Docker Compose 란? {id="docker-compose-description"}

Docker Compose 파일은 도커 애플리케이션 서비스, 네트워크, 볼륨 등의 설정을 YAML 형식으로 작성하는 파일입니다.

아래는 공식 문서에서 소개한 간단한 작성 양식입니다.
- [@See :: docker docs - illustrative example](https://docs.docker.com/compose/compose-file/02-model/#illustrative-example)

```yaml
services:
  frontend:
    image: example/webapp
    ports:
      - "443:8043"
    networks:
      - front-tier
      - back-tier
    configs:
      - httpd-config
    secrets:
      - server-certificate

  backend:
    image: example/database
    volumes:
      - db-data:/etc/data
    networks:
      - back-tier

volumes:
  db-data:
    driver: flocker
    driver_opts:
      size: "10GiB"

configs:
  httpd-config:
    external: true

secrets:
  server-certificate:
    external: true

networks:
  # The presence of these objects is sufficient to define them
  front-tier: {}
  back-tier: {}
```

크게 구성 요소는 다음과 같습니다.
- services
- network
- volume
- config
- secret

## services

`services`는 여러 컨테이너를 정의하는데 사용됩니다.

e.g. 아래와 같이 파일을 작성한다면, `frontend`와 `backend`는 각 컨테이너를 정의하게 되며, 각 컨테이너의 이름이 됩니다.
```yaml
services:
  frontend:
    image: example/webapp
  
  backend:
    image: example/database
```

### 컨테이너 설정 키워드

| keyword          | description                                                    |
|------------------|:---------------------------------------------------------------|
| `image`          | 컨테이너의 이미지를 정의                                                  |
| `build`          | 위 `image`를 활용하는 방식이 아닌 도커파일의 경로로 지정해 빌드하여 사용하는 방법              |
| `dockerfile`     | 빌드할 도커파일의 이름이 `Dockerfile`이 아닌 경우 이름을 지정하기 위해 사용               |
| `ports`          | 호스트와 컨테이너의 포트 바인딩 설정에 사용됨                                      |
| `volumes`        | 호스트의 지정된 경로로 컨테이너의 볼륨을 마운트 하도록 설정                              |
| `container_name` | 컨테이너 이름을 설정                                                    |
| `command`        | 컨테이너가 실행된 후 컨테이너의 쉘에서 실행시킬 쉘 명령어 설정                            |
| `environment`    | 환경변수를 설정                                                       |
| `env_file`       | `environment`와 동일한 기능을 수행하지만 이 키워드를 사용하면 env 파일을 이용해서 적용할 수 있음 |
| `depends_on`     | 다른 컨테이너와 의존관계를 설정                                              |
| `restart`        | 컨테이너의 재시작과 관련하여 설정                                             |


## Docker Compose 파일 실행 {id="docker-compose-run"}

작성된 `docker-compose.yml` 파일을 실행하기 위해서는 아래와 같은 커맨드를 사용합니다.

```Bash
docker-compose up
```

추가로 아래와 같은 옵션들을 사용할 수 있습니다.

-f 옵션
: 
- docker-compose는 기본적으로 `docker-compose.yml` 또는 `docker-compose.yaml`의 이름을 사용합니다.
- 만약 다른 이름으로 파일을 관리하고 사용한다면 아래와 같이 입력합니다.
```Bash
docker-compose -f docker-compose-custom.yml up
```

-d 옵션
:
- 백그라운드에서 `docker-compose`를 실행하기 위해 사용됩니다.
```Bash
docker-compose up -d 
```