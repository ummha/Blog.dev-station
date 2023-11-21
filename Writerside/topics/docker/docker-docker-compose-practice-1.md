# Practice 1. Spring Boot Multi Module

이전에 정리한 [Docker Compose 작성하기](docker-docker-compose-about.md) 내용을 바탕으로 Docker Compose를 작성하는 실습을 해보겠습니다.

실습할 프로젝트는 자바17, 스프링 부트 3.1.5 버전과 gradle 8.4 버전을 사용하였고 기본적으로 멀티 모듈로 구성하였습니다.

## 1. 스프링 부트 프로젝트 멀티 모듈 구성하기

멀티 모듈 구성과 관리는 ['buildSrc' 방식](https://docs.gradle.org/current/userguide/declaring_dependencies_between_subprojects.html)
으로 빌드 스크립트 컨벤션을 작성하여 모듈을 구성했습니다.

```text
{project}
├── buildSrc
│   ├── src
│   │   └── main
│   │       └── java
│   │           └── base.java-conventions.gradle
│   └── build.gradle
├── api-delivery [module]
│   ├── src
│   │   └──...
│   └── build.gradle
├── api-market   [module]
│   ├── src
│   │   └──...
│   └── build.gradle
└── settings.gradle
```

자세한 구조는 [깃허브 저장소](https://github.com/ummha/Practice.Docker/tree/main)에서 확인할 수 있습니다.

## 2. Dockerfile 작성하기

## 3. docker-compose 작성하기