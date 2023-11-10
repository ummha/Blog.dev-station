# Dockerfile Practice

간단하게 도커파일을 작성하여 정적파일을 웹서버 컨테이너에 실행하는 실습을 해봅니다.

요구사항은 다음과 같습니다.
1. 현재 블로그 소스를 압축 파일로 빌드합니다.
2. 압축 파일을 실습할 디렉토리로 옮겨 압축 파일을 풉니다.
3. 해당 디렉토리에 Dockerfile을 작성합니다.
4. Dockerfile에 Apache 웹 서버 도커 이미지를 지정합니다.
5. Apache 웹 서버가 실행될때 기본적으로 연결되는 htdocs 디렉토리에 정적 파일들을 옮깁니다.
6. 작성한 Dockerfile로 이미지를 빌드합니다.
7. 빌드된 이미지로 컨테이너를 생성하여 실행합니다.

{collapsible="false" default-state="expanded"}
Step 1. 블로그 소스 압축 파일로 빌드
:
- Writerside는 아래 이미지처럼 보다 쉽게 문서 작성 소스를 압축파일로 빌드할 수 있습니다.
![압축파일빌드 이미지](docker-dockerfile-practice-img-1.png)

Step 2. 압축 파일을 실습할 디렉토리로 옮겨 압축 파일 풀기
:
- 압축된 파일을 원하는 디렉토리로 옮기고 압축을 해제합니다.
![압축풀기 이미지](docker-dockerfile-practice-img-2.png)

Step 3. Dockerfile 작성
:
- FROM 구문에 아파치 이미지를 지정합니다.
- COPY 구문에 정적파일 전체를 아파치 디렉토리인 htdocs로 옮기는 설정을 작성합니다.
  ```Docker
  # ./Dockerfile
  FROM httpd
  
  COPY ./webHelpMI2-all/** /usr/local/apache2/htdocs/ 
  ```
  
Step 4. 작성한 Dockerfile로 이미지 빌드
:
- 아래와 같이 도커 이미지 빌드 명령어를 실행합니다.
  ```Bash
  docker build -t blog-template:1.0 .
  ```
- 명령어 설명:
  도커 이미지 이름(`-t`)은 `blog-template`이고 이미지 태그(`:`)는 버전을 의미하는 `1.0`으로 도커 이미지를 빌드하고, 명령어 실행 경로(`.`)에 있는 Dockerfile을 설정합니다.
- 명령어 실행 이미지
 ![이미지 빌드 명령어 실행 이미지](docker-dockerfile-practice-img-3.png) { thumbnail="true" }

Step 5. 도커 컨테이너 실행
:
- 아래와 같이 도커 컨테이너를 실행합니다.
  ```Bash
  docker run --name my-blog -p 80:80 -d blog-template:1.0
  ```
- 명령어 설명: 도커 컨테이너 이름(`--name`)은 `my-blog`로 지정하고 호스트의 `80`포트를 도커 컨테이너의 `80`포트와 매핑(`-p`) 또는 포워딩 합니다. 
  백그라운드에서 데몬(`-d`)으로 실행(`run`)하며 `blog-template:1.0` 이미지로부터 컨테이너를 생성합니다.
- 명령어 실행 이미지
 ![컨테이너 실행 명령어 실행 이미지](docker-dockerfile-practice-img-4.png) { thumbnail="true" }

Step 6. 확인
:
- http://localhost
![컨테이너 실행 명령어 실행 이미지](docker-dockerfile-practice-img-5.png) { thumbnail="true" }