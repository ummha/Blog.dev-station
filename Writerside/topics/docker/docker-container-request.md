# 도커 컨테이너와 통신하기

도커 컨테이너는 기본적으로 독립적인 환경에서 실행되기 때문에 컨테이너 밖에서 접근할 수 없습니다.

따라서, 컨테이너와 통신하기 위해서는 컨테이너를 가동시키면서 `p` 옵션을 사용하여 도커 컨테이너의 포트 포워딩 설정을 해줘야 합니다.

```Shell
-p ${호스트 포트}:${컨테이너 포트}
```
```Shell
# e.g. Apache 이미지인 httpd 이미지로 컨테이너를 생성하고 호스트 포트 8080을 컨테이너 포트 80에 매핑 
docker run --name web-container -d -p 8080:80 httpd
```
{collapsible="true" default-state="collapsed"}

이 설정을 사용하기 위해서는 호스트(서버 또는 PC)에서 사용 중인 포트가 겹치치 않는지 확인하여 여분의 포트를 사용하여 컨테이너의 포트를 설정해야 합니다.

![docker container request](docker-container-request.jpg)


> **포트 포워딩이란?**
> 
> 포트포워딩(port forwarding)은 컴퓨터 네트워크 상에서 패킷이 방화벽이나 라우터 같은 네트워크 게이트를 지날 때 IP 주소와 포트 번호 결합의 통신 요청을 
> 다른 곳으로 넘겨주는 네트워크 주소 변환의 응용이라고 볼 수 있습니다. 
> 
> 쉽게 말해서, 포트포워딩(Port forwarding)은 간단히 말해서 포트(Port)를 전달(Forwarding)해 주는 거라고 생각하시면 됩니다. 
> 특정한 포트로 들어오는 데이터 패킷을 다른 포트로 바꿔서 다시 전송해주는 작업인 것이죠.