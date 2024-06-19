# Switch

## 라우터란 무엇인가?

스위치는 신호가 들어오면 허브와 달리 모두에게 신호를 전달하지는 않고, 내부에 전달된 신호를 알맞은 주소로 전달하기위해 찾는다

라우터는 외부/내부 접근에대한 구분이 가능한 장치이다, 네트워크 - 네트워크간의 통신이 가능하기 때문에 외부 네트워크와의 통신을 원한다면 라우터를 사용해야한다

L2는 MAC 주소 -> L2 장비는 스위치

L3 는 IP 주소 -> L3 장비는 라우터

## 라우터를 쓸까, 스위치를 쓸까?

스위치는 대부분의 설정, 기능등이 자동이다. 관리와 사용이 쉬운 반면 라우터는 하나하나 설정해줘야한다. QOS처럼 네트워크 관리기능을 제공하는것은 라우터여서 라우터가 필요한데, 관리, 사용이 불편하고 가격또한 비싸서 요즘은 스위치 + 라우터를 합친기능이 많이 쓰인다.

요즘 신식 스위치는 외부 네트워크 통신도 가능하고 QOS도 가능하다

## 스위치의 구분

스위치는 어떤 주소로 스위칭을 하느냐에 따라 L2, L3, L4 스위치로 구분이 된다.

L2는 MAC 주소 ,L3는 IP주소, L3는 세션프로토콜을 이요하여 스위칭을 한다.

장점

* 이중화 구성이 가능하다
* 여러노드에서 동시 통신을 할 때 속도 저하가 없고, 성능이 향상된다

### L1(허브, 더미허브, L1 스위치)

OSI Layer 1계층에서 작동하는 스위치 = L1 스위치

스위치의 상위계층 (L7 이 가장상위)은 하위계층의 기능을 모두 포함하는것이다

### L2(스위칭 허브)

MAC 주소를 찾아서 전달해주는 스위치이다. 허브처럼 모두에게 다보내는것이 아니고 내부에서 특정한 MAC 주소에 해당하는 정보를 전달해준다.

패킷의 맥주소를 읽어 스위칭을 한다, MAC 주소는 OSI 계층의 2층에 해당하기 떄문에 L2 스위치이다

* 장점 : 구조가 간단하며 신뢰성이 높다
* 단점 : 패킷에 의한 성능 저하가 발생한다 - 라우팅이 불가능하다

### L3 스위치

순수 라우터 네트워크 패킷을 연결해주는 통로 역할로, 대역폭 확장이 주 기능이다

L3 스위치는 L2 스위치에서 L3 라우팅기능 (MAC 주소 + IP 주소)이 같이 있는 스위치를 말한다.

집에서 사용하는 공유기도 L3기능이 있다. (L3기능 + WIFI기능) 이장치를 AP 장치라고 부른다.

### L4 스위치

외부에서 들어오는 모든 요청은 서버가 아닌 L4 스위치를 거친다. L4 스위치가 먼저 받아서 서버에 적절하게 나누어주는 개념이다. L4의 주요 역할은 부하 분산이다.

* 사용이유
  * 서버가 한대가있고 그서버의 사용량이 증가되어 서버를 증설할 때. 증설한서버에 IP를 할당해야하고 트레픽 또한 관리해야하는데 이럴때 사용하는것이 부하분산이다.
  * 일일히 서버에게 요청을 전달, 사용자에게 요청할 필요 없이 L4 스위치를 통해 부하분산을 처리한다
  * 부하분산 기능 외에도, 서비스가 중단되는 경우를 대비하기위해 한 서버가 죽으면 다른 서버로 넘기는 서버이중화 기능을 가능하게 하기도 한다.

### L7 스위치

어플리케이션의 영역이다.

L4와 L7 모두 서버의 로드벨런싱을 위해 사용되는데 둘은 차이가 있다.

* L4
  * OSI 네트워크 계층과 전송계층에 속하는 IP주소 및 TCP/UDP 포트 정보를 보고 스위칭한다
  * TCP/UPD 포트 정보만을 이용하여 부하를 분산한다,
* L7
  * OSI 네트워크 계층과 전송계층에 속하는 IP주소 및 TCP/UDP 포트정보 및 패킷 내용까지 모두 보고 스위칭을한다
  * HTTP의 Url, FTP 쿠키 정보 및 바이러스 패턴을 분석하여 보안에 더 유리하고 정교한 로드 벨런싱이 가능하다.
  * 보안 스위치라고한다. 데이터 분석을 통해 DDos 공격방어, 감염 패킷 필터링 등의 기능을 제공한다.
* 공통점
  * 스위치로 들어온 패킷을 적절한 서버로 전송해주는 것이지만, L4 스위치와 L7 스위치는 근본적으론 다르다