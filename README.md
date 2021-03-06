# Computer-Network⚽
  경북대학교 22-S
  
***
 
  ## Network Layers
  ### 1. OSI 7 Layers
  ![image](https://user-images.githubusercontent.com/49769190/175812787-80954426-e7c3-4b9d-8b8f-c34ba06e731b.png)
  ### 2. Internet Protocol
  layer 5, 6, 7을 하나로 묶어서 이해하는 모델
![image](https://user-images.githubusercontent.com/49769190/175812819-1986d29d-ca22-42d9-b3c4-8fd418f70ebe.png)

![image](https://user-images.githubusercontent.com/49769190/175812828-f6072c47-8e45-4d2a-862b-22ba6eced53b.png)
  * transport layer는 logical connection 하고 있는 것으로 양단 사이의 devices은 이 연결을 몰라도 됨.
  * 논리적 연결이 아니라 물리적 연결이 필요(네트워크 layer)

  ## Network Layer service
   1. 패킷화(packetizing): 송신측에서 캡술화, 수신측에서 디캡술화(Header를 떼어내는 작업)
   * 송신측에서 네트워크 계층 패킷에 있는 페이로드(상위 계층에서 받은 데이터)를 캡슐화
     * 페이로드가 너무 크면 쪼갤 필요가 없음
   * 수신측에서 네트워크 계층 패킷의 페이로드를 꺼내는 것
     * 라우터나 송신지에서 패킷을 쪼개서 보내는 경우, 모든 조각들 도착할때까지 재조립하고 상위계층에 전달

   2. 라우팅(routing)
   * LAN과 WAN의 조합으로 물리적 계층이 구성되기 때문에 송신-수신 간 여러 경로가 있음
   * 여기서 가장 최선의 경로를 찾아가는 서비스 

   3. 포워딩(fowarding)
   * 라우터의 인풋을 적절한 아웃풋으로 패킷을 이동시키는 것
   * 포워딩 테이블을 이용(포워딩 벨류-아웃풋 인터페이스 맵핑), 최적의 경로를 찾아줌

   4. Error Control
   * 각 라우터에서 조각난 패킷들에 대한 에러 체크를 모두 확인하면 비효율적
   * 패킷에 체크필드만 헤더에 추가하여 corruption된 조각임을 알림
   
   5. Flow Control
   * 상위 계층에서 버퍼를 사용해서 데이터를 받기 때문에 흐름제어 해줌

   6. Congestion Control
   * 한 라우터에 데이터가 몰릴 경우, 자신에게 온 데이터를 모두 처리할 수 없게 이런 경우 호스트들은 또 다시 재전송을 하게되고 결국 혼잡만 가중시켜 오버플로우나 데이터 손신을 발생시킴.
   * 따라서 이러한 네트워크의 혼잡을 피하기 우해 송신측에서 보내는 데이터의 전송속도를 강제로 줄이게 되는데, 이러한 작업을 혼잡제어
   * 또한 네트워크 내에 패킷의 수가 과도하게 증가하는 현상을 혼잡
   * 흐름제어가 송신측과 수신측 사이의 전송속도를 다루는데 반해, 혼잡제어는 호스트와 라우터를포함한 보다 넓은 관점에서 전송 문제



  ### Packet switching🎸
  * 네트워크 계층에서만 사용
  * 상위 계층에서 오는 메세지를 관리 가능한 사이즈의 패킷으로 쪼개고 각 패킷을 네트워크를 통해 보냄
    1. datagram approach - 비연결 서비스
    2. virtual circuit approach(가상회선) - 연결 지향 서비스

  #### virtual circuit approach
   * 연결 지향 서비스
   * 가상 연결은 데이터그램을 보내기 전에 경로를 미리 준비해 둠 -> 미리 세팅한 경로가 가상 회선
   * 각 패킷은 패킷내부에 담겨있는(incoming) 라벨을 확인 -> 포워딩 테이블에 그 라벨에 해당되는 outgoing 라벨을 찾아 보냄
![image](https://user-images.githubusercontent.com/49769190/175812852-54a3da2d-0dad-491f-ae05-26181ff68900.png)
![image](https://user-images.githubusercontent.com/49769190/175812867-c75cf122-b661-49fd-946e-dad48984e0f4.png)


   #### Datagram approach
   * 비연결 서비스(패킷 간 관계 없음)
   * 각 패킷은 헤더에 있는 destination address 정보를 기반으로 라우팅 됨
   * 패킷헤더 -> 목적지 주소 확인 -> 포워딩 테이블에서 아웃풋 인터페이스로 패킷 전달🏅

 
 
  ### IP Address
    * IP 주소: TCP/IP 프로토콜의 IP layer에서 인터넷에 연결된 각 장치를 식별하기 위해 사용되는 식별자
    * IPv4 주소: 32bits, 전세게의 하나뿐인 유일한 주소이다. 약 40억개의 주소가 존재한다.
 
      원래 IP주소는 binary 형태의 32bits 숫자이다. 이를 byte 단위로 끊어서 10진법으로 표현하여 사용한다.

![image](https://user-images.githubusercontent.com/49769190/175812892-db1b359a-70b1-4c23-bef9-749d51371c58.png)


    ** 2진법을 10진법으로 
    128, 192, 224, 240은 알고 있자!
![image](https://user-images.githubusercontent.com/49769190/175812908-943ce4a9-1c30-4c1d-8ce3-df33ca005419.png)
    * IPv4는 4byte로 표현해야 함, 0 ~ 255 사이의 10진수 .으로 구분하여 나타냄, 0.0.0.0 ~ 255.255.255.255
    
    
  ### IPv6 주소
    IPv6에서 주소 길이를 128비트, 보통 16진수 8개를 쓰고 :로 구분한다
![image](https://user-images.githubusercontent.com/49769190/175812926-acb42cf0-c708-4978-b12a-978831e43a72.png)


  ### IP 주소의 클래스?
   IP주소에는 클래스가 있고 이 클래스의 개념을 알아야 어디까지가 네트워크 영역이고, 호스트 영역인지 알 수 있다. 즉, 하나의 IP주소에서 네트워크 영역과 호스트 영역을 나누는 방법이자 약속임
   IP 주소를 3개의 클래스로 나누는 이유는 네트워크 크기에 따른 구분이라고 생각하자!
   하나의 네트워크에서 몇 개의 호스트 IP까지 가질 수 있는 가에 따라 클래스를 나눌 수 있음.
  
![image](https://user-images.githubusercontent.com/49769190/175812935-5ef5d077-d884-4536-8764-7bbd99cf473d.png)
  IP주소 클래스는 총 5개로 구분된다. A클래스, B클래스, C클래스, D클래스, E클래스 등이 있다. 그러나 보통 A, B, C 3개 정도만 알고 있으면 됨.
  
  ### A클래스
  하나의 네트워크가 가질 수 있는 호스트 수가 제일 많음. IP주소를 32자리 2진수로 표현, 맨 앞자리 수가 항상 0인 경우임. 즉 **_0XXX XXXX. XXXX XXXX. XXXX XXXX. XXXX XXXX_**
  X는 0 또는 1로 이 범위를 10진수로 표현하면 0.0.0.0 ~ 127.255.255.255
  IP주소 중 1 ~ 126으로 시작하는 네트워크는 A클래스
 
  ### B클래스
  IP주소를 32자리 2진수로 표현했을 때, 맨 앞자리 수는 항상 10이여야 한다. 즉 10XX XXXX. XXXX XXXX. XXXX XXXX. XXXX XXXX
  
  IP 범위는 128.0.0.0 ~ 191.255.255.255
  네트워크 범위는 10XX XXXX. XXXX XXXX에서 X들이 가질 수 있는 경우의 수 ( 2^14개 )
  호스트 주소 범위는 XXXX XXXX. XXXX XXXX에서 X들의 경우의 수인 2^16 - 2개
  
  ### C클래스
  반드시 110으로 시작함. 2진수로 표현하면 110X XXXX. XXXX XXXX. XXXX XXXX. XXXX XXXX
  
  ![image](https://user-images.githubusercontent.com/49769190/175812948-b3e0a13d-84d7-4caf-8aa4-b6004fac0c6d.png)


## Delivery and Forwarding of IP packets
  ### Direct Delivery
  ![image](https://user-images.githubusercontent.com/49769190/175812970-a8d9f478-edaf-4ea4-93b2-23e00165e8dc.png)
  
  * 같은 link(Physical Network)에 연결된 노드로부터 패킷을 직접 전달받는 형태를 말함 / 패킷을 전달한 노드를 deliverer(전달자)
  * Link 내 통신에서 전달자는 다른 호스트가 될 것이고 외부 인터넷을 통해 유입된 패킷의 전달자는 해당 Link의 라우터가 될 것임
  * 패킷이 갖고 있는 목적지 IP주소의 Network 필드와 전달자의 주소의 Network 필드는 일치할 것임 -> 같은 물리네트워크 안의 노드임

  ### Direct Delivery
  ![image](https://user-images.githubusercontent.com/49769190/175812977-ee3bff02-33a0-4824-a6a5-aae0c1ed4718.png)
  
   * 소스와 목적지가 서로 다른 네트워크에 위치, 패킷은 다수의 네트워크를 경유하며 전송됨 / 목적지가 해당된 네트워크를 제외한 모든 경유지에서 전달되는 형태를 간접 전달이라고 함
   * 간접 전달 과정에서는 다른 네트워크의 스위치에 전송되지 않고, 라우터와 라우터 사이로 이동하게 됨

  ### Forwarding
   * 패킷을 목적지로 보내기 위한 경로를 설정하는 것
   * 라우팅 테이블을 어떻게 구상할 것인지
   * 목적지 주소에 기반하느냐, 레이블에 기반하느냐에 따라 목적지 주소 기반 포워딩, 레이블 기반 포워딩 두 가지 방법으로 나뉨
   
   #### Fowarding based on Destination Address
   목적지 주소 기반 포워딩에서 라우팅 테이블을 작게 만들어 처리 속도를 높이고 보안 문제를 해결하는 방법
   
   1. Next-Hop Method
   * 패킷 헤더의 목적지 IP 주소를 라우팅 테이블과 비교하여 Next-Hop 경로를 결정하는 방식
   * 전송 경로 상의 각각의 노드에서는 진행할 바로 다음 노드만 계산하여 전송함
   * 중간 경로의 노드에서 패킷의 전체 경로에 대한 주소를 모두 알아야 한다면, 주소 길이가 매우 길어질 위험도 있고, 다른 네트워크의 수정 내용을 모두 라우팅 테이블에 반영해야 하는 번거로움이 있음
   * 다음 경로만 생각함으로써, 목적지가 전송 경로상의 어떤 네트워크에 변화가 일어나 라우팅 테이블을 수정할 필요없음 / 처리 속도 또한 유지
   
   2. Next-Specific Routing Table
   ![image](https://user-images.githubusercontent.com/49769190/175813023-0de02bee-6f4b-4a1d-80a7-9aea1277734f.png)
   
   * 같은 네트위크에 연결된 모든 호스트에 대한 interface, NHA 주소 엔트리를 갖는 대신, 같은 네트워크에 연결된 모든 호스트를 하나의 엔트리로 간주하는 방식
   * 네트워크 지정 라우팅 테이블은 호스트 지정 라우팅 테이블보다 간결한 형태로 유지되어 처리속도에서 큰 차이가 남

   3. Host-Specific Routing Table
   * 네트워크에 연결된 모든 호스트에 대한 interface, NHA 주소를 모두 저장하는 방식임
   * 다른 특별한 이유로 인해 효율성을 희생하는 방식임
   
   4. Default Method
   ![image](https://user-images.githubusercontent.com/49769190/175813039-3c36f20a-7726-42c7-ab3e-648603f468ce.png)
   
   * 몇 가지 목적지에 대한 entry를 따로 정의하고 자주 보내지는 경로를 디폴트로 지정하는 방법
   * 디폴트 엔트리의 네트워크 주소와 마크는 0.0.0.0임
   * 네트워크 필드 추출은 마스크와 목적지 주소의 AND 연산을 통해 이루어짐, 다른 엔트리와 매칭되지 않은 목적지 주소가 0.0.0.0과의 AND 연산이 수행되면 그 결과 또한 0.0.0.0이 되어 엔트리의 네트워크 주소인 0.0.0.0과 매칭되는 원리 / 다른 엔트리와 매칭되지 않으면 무조건 디폴트 엔트리와 매칭될 수 밖에 없는 구조임
   
  
***
Example)
 그림을 참고하여 R1(라우터)에 대한 라우팅 테이블을 그리고 주어진 목적지 주소들의 포워딩 프로세스를 서술
  
 1. 180.70.65.140
 2. 201.4.22.35
 3. 18.24.32.78

![image](https://user-images.githubusercontent.com/49769190/175813051-49a79624-5562-4d9f-b020-bad9980779c8.png)
![image](https://user-images.githubusercontent.com/49769190/175813057-e835782c-246f-4487-9f26-470481846031.png)

 1) 180.70.65.140 = 180.70.65.10001100 -> (180.70.65.128)
 * 두 번째 엔트리의 네트워크 주소와 일치
 * 1번 패킷은 m0 인터페이스로 나가게 됨
 
 2) 201.4.22.35
 * 세 번째 엔트리의 네트워크 주소와 일치함을 확인할 수 있음
 * 2번 패킷은 m3 인터페이스로 나가게 됨

 3) 18.24.32.78
 * 라우팅 테이블의 어느 엔트리와도 일치하지 않음, default 엔트리와 매칭

***

 * 5가지 네트워크 주솟값이 존재하는 것으로 보아 총 5개 물리네트워크가 존재함
 * Interface 필드에 3가지 값(m0, m1, m2)이 존재하는 것으로 보아 R1의 인터페이스의 개수는 3개임을 알 수 있음.
 * NHA 필드에 direct값으로 지정된 3개의 네트워크 값들이 R1에 직접적으로 연결된 네트워크임을 알 수 있음. 
 * NHA 필드에 특정 주솟값이 3종류로 있는 것으로 보아 R1과 하나의 물리 네트워크를 사이에 둔 상태로 연결된 라우터는 3개임을 알 수 있음


### Hierarchical Routing

  * core Network(beakbone)의 라우터부터 local Network의 라우터까지 각 라우터마다의 라우팅 테이블에 계층적 구조를 적용한 모델
  * 각 각의 라우터에서는 하위 계층 네트워크의 세부사항을 고려하지 않음으로써, 라우팅 테이블의 엔트리 수를 줄여 처리 속도를 높임
  ![image](https://user-images.githubusercontent.com/49769190/175813072-ceb4ee49-5ec2-4317-9588-bf0abefe2b63.png)


  * regional ISP에서 small ISP의 Customer까지 이르는 계층적 라우팅 형태 도식
  * regional ISP는 120.14.64.0/18 주소 (2^14개 주소)를 할당받아 4개의 block으로 subnetting함(4개의 Block으로 Subnetting했으므로, 네트워크 필드에 2Bit가 추가)
  * Local ISP는 할당받은 주소를 다시 8개의 Block으로 Subnetting하여 Host(Customer)들에게 제공 (8개의 Block으로 Subnetting했으므로, 네트워크 필드에 3BBit가 추가)
  * Small ISP들의 라우팅 엔트리 개수 = 128개의 호스트 + Default Router = 129개의 엔트리
  * Local ISP1의 라우팅 엔트리 개수 = 8개의 Small ISP + Default Router = 9개의 엔트리
  * Local ISP2의 라우팅 엔트리 개수 = 4개의 대형 기관 + Default Router = 5개의 엔트리
  * Local ISP3의 라우팅 엔트리 개수 = 16개의 소형 기관 + Default Router = 17개의 엔트리
  * Regional ISP = 3개의 Local ISPs + Default Router = 4개의 엔트리 (사용되지 않는 주소는 고려하지 않음)
  * 수 단계의 계층을 거쳐도 라우팅 테이블의 엔트리 개수가 그리 많지 않음을 확인할 수 있음
  * 상위 계층의 라우터에서는 하위 계층의 네트워크의 많은 주소들을 하나로 간주하는 Aggregation을 수행하기 때문에 처리 속도를 높일 수 있음
  * 라우팅 테이블에서 패킷의 주솟값을 보고 적절한 라우팅 엔트리에 매칭시키는 대표적인 방법으로는 Longest Match Algorithm(가장 긴 부합 알고리즘)이 있음
  * 상위 계층의 라우터에서는 하위 계층의 네트워크의 많은 주소들을 하나로 간주하는 Aggregation을 수행하기 때문에 처리 속도를 높일 수 있음
  * 하지만, Longest Match Algorithm은 Mask를 기준으로 정렬되어 있는 엔트리를 Sequential Searching 하는데 평균적으로 n/2 시간이 걸려, 실행 시간 측면에서 불리함.
  * 실제 라우터의 라우팅 테이블에서 주소와 엔트리를 매칭시키는 알고리즘은 검색과 더불어 엔트리 삽입/삭제 연산에도 용이한 형태로 복잡하게 구현되어 있음(실제 라우팅 테이블은 엔트리 삽입/삭제에 용이하도록 Mask를 기준으로 정렬하지 않는다. 정렬을 해놓을 시, 삽입/삭제에 소요되는 시간이 커지기 때문)


### 라우터의 설계구조
![image](https://user-images.githubusercontent.com/49769190/175813081-22539048-7323-4a9f-a205-1ffbeeea915b.png)


### Internet Protocol Version4(IPv4)🔥
![image](https://user-images.githubusercontent.com/49769190/175813087-b3ed391f-4323-438f-abc4-1788cbf95741.png)

* L3에 속하는 프로토콜로, 현재 버전(IPv4)와 버전 6(IPv6)가 공존해있는 상황임
* L2로부터 전달받은 Frame을 라우팅 테이블을 참조하여 현재 Host 보내진 패킷이면 처리하여 L4로 올리고 다른 호스트를 목적지로 하는 패킷이면 적절한 인터페이스 주소와 NHA를 검색하여 패킷을 전달함
* NHA는 논리 주소 형태이므로 ARP를 통해 물리 주소로 변환되어 전송됨
* 물리 네트워크로 전송되기 전에 전송할 패킷이 해당 물리네트워크의 수용가능한 IP-Datagram의 최대 크기를 초과하면 Fragmentation을 진행함
* IP 프로토콜의 보조 프로토콜로 IGMP와 ICMP가 존재함
* IGMP(Internet Group Management Protocol): 멀티 캐스팅에 이용되는 프로토콜임. 멀티캐스팅이 가능하기 위해서는 클라이언트가 멀티 캐스트 그룹에 가입/탈퇴하는 기능(Join/Leave)이 필요하게 되는데, 그 기능을 관리하는 프로토콜임
* ICMP: destination에서 오류가 발생하면, 패킷을 폐기하고 소스에게 이 사실을 통보하는 역할을 하는 프로토콜임



### Datagrams (IP-Datagram Header Structure)
![image](https://user-images.githubusercontent.com/49769190/175813096-6a7272ee-0386-4741-8cf3-0d4fe4979fda.png)

* IP Datagram(L3 패킷)에서 헤더의 길이느 20 ~ 60Byte로 구성 (표준 헤더는 20Byte 크기임. 최대 40Byte가 추가됨)
* L3 패킷에서 데이터의 길이는 0 ~ 65515Byte로 구성
* L3 패킷의 최소 길이는 20Byte, 최대 2^16 - 1Byte로 구성

![image](https://user-images.githubusercontent.com/49769190/175813107-0fe51a09-a4c4-4b26-ad82-c22820d53ba9.png)
* 그림에서 하나의 Row는 4Byte 크기 / 흰색 바탕의 내용들은 표준 헤더를 구성하는 요소들(5 Rows를 구성하고 있으므로, 표준 헤더의 크기는 20Byte) 
* 회색 바탕의 내용은 옵션 헤더를 구성(옵션 헤더는 0 ~ 40Byte 사이의 크기)

<span style="color:rgb(245, 235, 13)">데이터그램은 헤더부분과 상위 계층으로부터 받아온 데이터 부분으로 나뉨. 데이터 부분은 상위 계층에서 내려보낸 그대로 사용, 헤더 부분만 네트워크 계층에서 만들어 데이터 부분과 합쳐줌으로써 데이터그램을 만듦.</span>

1. VER (Version): IP 프로토콜의 버전을 의미합니다. IP 프로토콜은 IPv4와 IPv6가 현재 사용되고 있으며, 4자리 비트로 이루어져 있기 때문에, IPv4의 경우 0100, IPv6의 경우에는 0110으로 표기
2. HLEN (Header Length): 헤더의 길이를 알려주는 부분으로, 4 비트로 표현됨. 헤더는 헤더의 가장 마지막에 포함되는 옵션의 길이에 따라 옵션이 없으면 20바이트, 옵션이 최대로 추가되면 60바이트가 됨.
3. Service Type: 해당 데이터그램의 지연, 우선순위, 신뢰성, 처리량 등의 정보를 담고 있는 필드입니다. 8 비트로 이루어져 있습니다.
4. Total Length: 헤더와 데이터 부분을 합한 데이터그램의 전체 길이를 뜻함. 이 전체 길이 필드가 16 비트로 이루어지기 때문에, 데이터그램의 최대 길이는 2^16 -1, 즉 65,535비트(64KB)를 넘지 못함.
5. Identification: 데이터그램은 상황에 따라 목적지에 도착하기 전에 여러 개로 나누어질 수 있음. 이렇게 데이터그램이 여러 개로 갈라졌을 때, 이 여러 개의 데이터그램들이 원래는 동일한 특정 데이터그램이었다는 식별자 정보를 이 곳에 저장함
  * 잘린 데이터그램들이 원래 같은 데이터그램이라는 것을 증명하기 위해 각각의 데이터그램들은 중복되지 않는 고유한 식별자들을 가지고 있음. 이를 위해 송신 측에서는 하나의 데이터그램을 보낼 때마다 카운터의 값을 1씩 증가시켜 고유한 식별자를 만들어냄.
6. Flag, Fragmentation Offset: 각각 3개, 13개의 비트로 이루어져 있음
  * 플래그 필드의 3개의 비트는 해당 데이터그램의 각각 다른 특징을 표현함. 가장 우측의 0번 비트는 항상 0이라는 값을 가지고, 그 옆의 1번 비트는 해당 데이터그램이 쪼개어질 수 있는지에 대한 여부에 따라 가능하다면 0, 그렇지 않다면 1을 가짐.   
7. TTL (Time to Live): TTL 필드는 쉽게 말해 수명을 알려주는 필드입니다. 데이터그램이 네트워크 상에서 다양한 이유로 목적지에 도착하지 못하고 네트워크를 떠도는 일이 생길 수 있음 이런 길을 잃은 데이터그램들이 늘어나면, 네트워크의 흐름을 방해할 수 있고, 상위 계층을 혼란시킬 수 있기 때문에 수명을 다한 데이터그램들은 자동으로 폐기됨 
8. Protocol: 네트워크 계층의 상위 계층인 전송 계층이 사용하는 프로토콜에 대한 정보를 담고 있음. 8 비트로 구성되며, 대표적으로 UDP는 17, TCP는 6, ICMP는 1을 사용함
9. Header Checksum: 헤더 체크섬은 헤더에 오류가 있는지를 확인하기 위한 16비트로 이루어진 필드임 데이터 링크 계층에서의 Error Control과 같은 역할을 한다고 볼 수 있음.
10. Source / Destination IP Address: 각각 32 비트로 이루어지며 송신과 수신자의 IP 주소가 기록되어 있음.


### Unicast
* 1:1 통신을 말하며 LAN 통신에서 송신자의 MAC과 수신자의 MAC 주소를 알 때 메시지를 전달함
* 유니캐스트 메세징은 개인적이거나 고유한 리소스가 필요한 모든 네트워크 프로세스에서 사용될 수 있음
* 한개의 목적지 MAC 주소를 사용하여 CPU 성능에는 문제를 주지 않음

       단점 : 대량으로 배포되는 특정 네트워크 응용 프로그램에서 유니캐스트로 데이터를 전송할 경우, 각 각의 네트워크 연결마다 호스트의 컴퓨터 리소스를 소비할 뿐만 아니라 각각 다른 네트워크 대역폭을 필요로 하기 때문에 전송비용이 매우 높음

### Broadcast
* 정보의 전달 과정에서 송신자는 누군지 확실히 아나 수신자를 특정하지 않았을 때, 네트워크에 있는 모든 서버에게 정보를 알려야 할 때, 라우터끼리 정보를 교환하거나 새로운 라우터를 찾을 때, 브로드캐스팅 방식을 사용함.
* 주소가 따로 정해져 있고, 수신 받는 목적지는 이 주소가 오면 패킷을 자신의 CPU로 전송해서 CPU가 패킷을 처리함. 네트워크에 있는 모든 목적지에 패킷이 전송되므로 트래픽이 증가, CPU 성능의 저하도 있음.
* 메시지 브로드 캐스팅은 호스트가 고유한 IP 주소로 식별되는 다른 단일 호스트에 데이터 그램을 보내는 유니캐스트 주소 지정과는 별개로, 해당 브로드캐스트 주소를 사용하여 해당 주소 범위에 있는 전체 호스트에 트래픽을 전달함.


### Multicast
* 한번의 송신으로 메세지나 정보를 목표한 여러 컴퓨터에 전송하는 것을 말함. 1:N 전송방법임.
* 수신자를 그룹화하여 해당 그룹에 해당하는 수신지만 유니캐스트 + 브로드 캐스트를 한다고 보면 되겠음.
* 멀티 캐스트는 보통 IP 멀티캐스트 형태로 구현, 이는 스트리밍을 위한 인터넷 프로토콜 응용 프로그램 및 인터넷 TV에서 많이 사용됨. IP 멀티 캐스트는 주로 IP 라우팅 단계에서 구현되며, 이 때 라우터는 데이터그램을 멀티캐스트 대상 주소로 보내기 위한 최적의 전송 경로를 생성함.
* IP 멀티 캐스트는 네트워크상의 IP 인프라를 통해 일대다 통신을 위한 기술, 멀티캐스트는 소스로부터 패킷을 한번만 전송하게 함으로써 네트워크 인프라를 효율적으로 사용하며, 이는 많은 수신자들에게 전송할 필요가 있을 때도 마찬가지임. 네트워크 상의 각 노드들은 필요한 경우에만 여러 수신자에 도달하는 패킷을 복제함.


       *요약*
       멀티캐스팅? 하나의 송신자와 특정 그룹에 속한 다수의 수신자와의 통신형태를 의미함. 각각의 주소 클래스는 유니캐스트은 A, B, C를 사용하고 D클래스는 멀티캐스트에서 사용하는 주소임. D클래스를 사용하는 멀티캐스트 주소에서는 유니캐스트의 주소를 받을 수도 있지만 멀티캐스트 주소를 부여받을 수 있음.
       
       1) 유니캐스팅 : 하나의 송신자, 하나의 수신자
       2) 브로드캐스팅 : 하나의 송신자, 송신자 제외 모두 수신자
       3) 멀티캐스팅 : 하나의 송신자, 특정 그룹에 속한 다수의 수신자



### 멀티플 유니캐스팅
멀티캐스팅과 유사한 개념으로 수신자가 10곳이라고 할 때 한명의 송신자가 유니캐스트 주소를 10개를 배정하여 패킷을 10곳 모두 보내는 방식으로 멀티캐스팅과 같은 효과임. 10,000곳, 100,000곳 점점 늘어나게 되면 처음 보낸 패킷과 마지막 패킷간의 지연시간이 발생하게 됨. 이외에도 1개만 보내도 되는 패킷을 만개 십만갰기 보내다보니 대역폭을 과대 소모하게 되는 단점!

![image](https://user-images.githubusercontent.com/49769190/176349543-31266eeb-09f8-421c-b332-70f411be9738.png)


#### 멀티캐스트 IP주소 체계

      224.0.0.0 ~ 239.255.255.255 범위를 갖는 class D IP 주소를 사용함.
![image](https://user-images.githubusercontent.com/49769190/176349642-08e104db-8772-4f75-bf3f-e2dba34773e6.png)

* 그림은 한명의 송신자와 다수의 수신자가 존재하는 것을 알 수 있음. 여기서 멀티캐스팅의 송신자는 1개의 패킷을 보내지만, 멀티플 유니캐스팅에서는 애초에 출발할때 여러개의 패킷이 출발한다는 것을 볼 수 있음.

***

* 224.0.0.1 : 현재 서브넷에 존재하는 멀티캐스트가 가능한 모든 호스트를 지칭함.
* 224.0.0.2 : 현재 서브넷에 존재하는 멀티캐스트가 가능한 모든 라우터를 지칭함.


#### 멀티캐스트 MAC주소 체계
멀티캐스트 MAC 주소는 앞에 0100.5E가 붙고 뒤에 주소들은 IP주소에 일부분을 참조하여 이루어진다. 예를 들어 227.35.189.34의 멀티캐스트 MAC주소는 0100.5E23.BD22가 됨.

    227.35.189.34를 이진수로 표현하면 아래와 같음
    11100011.0
    0100011.10111101.00100010
    -> 멀티캐스트 MAC 기본 주소 앞부분(0100.5E)을 제외하고 나머지는 위 파란색 부분과 매치
    
    00000001-00000000-01011110-0
    0100011-10111101-00100010
    -> 16진수: 01-00-5E-23-BD-22
    
#### 멀티캐스트 프로토콜
어떤 장비와 멀티캐스트 정보를 교환하느냐에 따라 세 가지 프로토콜로 나눌 수 있음.

* IGMP: 호스트와 라우터 간 멀티캐스트 정보를 교환하는 프로토콜
* CGMP, IGMP snooping: 라우터와 스위치 간 멀티캐스트 정보를 교환하는 프로토콜
* Multicasting Routing Protocol: 라우터와 라우터 간 멀티캐스트 정보를 교환하는 프로토콜


![image](https://user-images.githubusercontent.com/49769190/176349684-de98c63b-1fe7-4d3c-8633-341d0384057b.png)

* 멀티캐스트 그룹에 가입을 요청하는 메세지인 Membership Report, 탈퇴는 Leave Report 그리고 관리상 질의응답을 요청하는 경우에 사용하는 Query가 있다. Query의 종류는 General과 Special로 나뉨.

<span style="color:green"></span>
1) 멀티캐스트 라우터
 * 네트워크에서 멀티캐스트를 관리하는 라우터를 멀티캐스트 라우터라고 부름. 멀티캐스트 라우터는 네트워크에 있는 컴퓨터 중 어떤 것이 특정 멀티캐스트 크룹에 속하는지 목록을 가지고 있게 되고 그 목록에 따라 패킷을 송신 여부를 결정하게 됨.

2) 그룹가입
* 호스트는 그룹에 가입하기 위해 가입요청 메시지를 멀티캐스트 라우터에게 보내게 됨.
* 예를 들어 화상회의를 한다고 가정해보자. 나는 화상회의를 위해 어플리케이션을 깔고 해당 어플리케이션을 더블클릭하여 실행하게 된다. 여기서 실행하기 위해서는 해당 화상회의의 패킷을 받아야 하는데 멀티캐스트 라우터에게 "나 화상회의 같이하려고 하니까 해당 패킷을 나에게 보내줘"라고 요청하여 받게 된다. 이 요청이 Membership Report가 되고 Membership Report 안에는 가입하고자 하는 특정 그룹의 주소를 함께보내게 된다.

3) 그룹 탈퇴
* 호스트는 탈퇴 요청 메시지를 멀티캐스트 라우터에게 송신하게 됨.
* 여기서 탈퇴 요청을 받은 멀티캐스트 라우터는 해당 네트워크의 다른 호스트가 아직 그룹에 가입해 있는지를 확인한 후 없다면 그룹을 삭제하게 됨.

      * 요약 *
      (1) 호스트는 멀티캐스트 라우터에게 Leave Report 송신
      (2) 라우터는 네트워크에 있는 모튼 컴퓨터에게 Special query를 보내 확인
      (속해있는 호스트가 있을 때)
      (3) 속해있는 호스트는 Membership Report를 보내 아직 가입해 있다는 것을 라우터에게 알린다
      (속해있는 호스트가 없을 때)
      (3) 아무도 응답을 안하게 되고
      (4) 멀티캐스트 라우터는 해당 그룹을 삭제하게 된다.
 
4) 그룹 모니터링
* 만약, 정전이나 다른 이유에 의해서 컴퓨터가 다운됐을 경우에는 어떻게 될까? Leave Report를 보내지도 않았는데 갑자기 끊어지게 되면 멀티캐스트 라우터 입장에서는 아무도 쓰지 않는 그룹인데 계속해서 멀티캐스트 패킷을 보낼 수도 있다. 이럴 경우를 대비해서 멀티캐스트 라우터는 일반질의 메시지(General query)를 주기적으로 보내 그룹가입자를 모니터링 하게된다. 이때 이 메시지를 받은 모튼 시스템은 해당 그룹에 대한 가입상황을 보고해야하고 보고되지 않은 시스템들은 모두 삭제한다.


#### 멀리캐스팅 라우팅
* 유니캐스트 라우팅의 경우 라우터가 하나의 목적지에 대한 하나의 최적경로를 가지게 됨. 
* 하지만, 멀티캐스트 라우팅은 라우터가 그룹에 대한 하나의 최적경로를 가지게 됨. 여기서 n개의 그룹이 있다면 n개의 최적경로가 필요하게 됨. 
* 또한 해당 그룹에는 여러개의 네트워크가 있을 수 있으며, 이는 트리 구성하여 멀티캐스트 패킷을 전달하게 됨.

1) 송신자 기반 트리(Source-Based trees)
* 모든 멀티캐스트 라우터들이 각 그룹에 대해 멀티캐스팅 라우터 테이블을 모두 작성하는 것으로 각 라우터는 그룹별로 하나의 최적경로를 구성함.
* 프로토콜: DVMRP(멀티캐스팅 라우팅 프로토콜로 RIP와 같이 거리 벡터 라우팅 방식을 사용), MOSPF(OSPF와 같이 링크상태 라우팅 방식), PIM-DM

2) 그룹 공유 트리(Group-shared trees)
* 동일한 트리를 각 그룹이 하나씩 가지고 이를 공유함
* 각 라우터가 그룹별로 최적경로를 구성하는 것이 아니라 센터코어 라우터만 그룹에 대한 최적경로를 구성하게 됨.
* 프로토콜: CBT, PIM-DM


Example) An IP packet has arrived with the first 8bits as shown: 01000010
receiver discards the packet why?

- there is an error in this packet. the 4 left-most bits(0100) show the version, which is correct. the next 4 bits(0010) show the wrong header length(2X4= 8). The minimum number of bytes in the header must be 20. the packet has been corrupted in transmission.

***


### ICMP (IPv4)
Internet Control Message Protocol
L3의 Support Protocol 중 하나로, 패킷 송수신 중 오류가 발생되어 폐기되었음을 Source에게 알리는데 사용되는 프로토콜임.
![image](https://user-images.githubusercontent.com/49769190/176350216-7d5f1729-cf23-4e5a-bf33-478afcd9976a.png)
* ICMP 프로토콜 밑에 IP 프로토콜이 위치해있는데, 이는 ICMP메세지가 Frame(L2패킷)으로 구성될 때, IP프로토콜을 필히 거치게 됨을 의미함
* IGMP는 Multi-Cating을 보조하기 위한 프로토콜임
* ARP는 패킷의 NHA 주소에 해당되는 물리 주소로 변환되는 프로토콜임
* IP프로토콜은 패킷 송수신 과정 중 문제가 발생했을 때, 오류를 보고 / 보정하는 기능을 제공하지 않음

![image](https://user-images.githubusercontent.com/49769190/176350315-76105f5b-c3ba-4e31-8ec0-694070566ca4.png)
* ICMP 메세지가 frame으로 구성될 때, IP 프로토콜에 의해 IP-datagram으로 재구성됨.

#### ICMPv4 Message
 ICMPv4 메세지는 Error-Reporting Message(오류 보고 메세지), Query Message로 구성됨.
![image](https://user-images.githubusercontent.com/49769190/176350352-c0894162-9ecc-4c88-b265-a4b257dbee95.png)
 * ICMP 메세지의 헤더는 총 8byte임.

 1. Type Field
  오류의 종류 혹은 이유를 구분짓는 필드임
 2. Code Field
  Type 필드에서 구분지은 종류를 더욱 세분화할 필요가 있을 시에 사용하는 필드임
 3. checksum Field
  * Rest of the header Field
      * type에 따라 여러 내용이 쓰여지는 필드임
      * 필요에 따라 rest of the header 일부 혹은 전체가 사용됨
  * Data section
      * 오류 보고 / 질의에 따라 들어가는 내용이 다름

![image](https://user-images.githubusercontent.com/49769190/176350383-ff545567-5e30-43ff-bec6-090fad5b3003.png)
 * 오류 보고 메시지일 경우, Data Section에는 페기된 패킷의 IP-Header와 메시지의 초반 8byte(TCP/UDP 헤더)값이 첨부됨.
 * Source는 Data section의 내용을 보고 자신에게 발생한 문제를 진단함.

![image](https://user-images.githubusercontent.com/49769190/176350439-54ec9d26-9581-4fbd-8a1e-9a88866858d0.png)
 * Error-Reporting Message(오류 보고 메시지): ICMP메시지가 오류보고메시지로 사용된다면 항상 Original Source에게만 전송됨

#### Type3: Destination Unreachable
![image](https://user-images.githubusercontent.com/49769190/176350492-554822f5-8f46-467a-b520-952e4bbcb1bb.png)
* 패킷이 목적지의 프로세스에 도달하지 못하여 패킷이 폐기된 상황임
* Code: 0에서 15 사이의 값을 갖는다. 16가지 문제를 분류할 수 있음 (code 2, 3은 목적지 노드와 연관된 문제, 나머지 code는 라우터와 연관된 문제임)
* Code2: Unreachable Protocol 목적지의 IP의 상위 프로토콜에 문제가 발생한 상황
* Code3: Unreachable Port L4의 프로토콜 (TCP/UDP)필드의 목적지 포트 번호에 해당되는 프로세스에 문제가 발생한 상황임.
* Data Section : 폐기된 패킷의 IP의 헤더와 메시지의 초반 8byte가 첨부됨
* Host Unreachable : 목적지 노드의 전원이 꺼져있어 발생하는 형태임
*  Port Unreachable : 목적지 노드의 해당 프로세스에 문제가 발생한 형태이다. (Code 2 or 3)


#### Type4: Source Quench
![image](https://user-images.githubusercontent.com/49769190/176350517-222cea7e-020e-461b-aa4c-0aa1a514eadd.png)
* 중간 경로의 라우터에서 버터 오버플로우가 발생한 상황 혹은 source와 Destination간의 통신 속도 차이로 인한 목적지 호스트에서의 버퍼 오버플로우(Flow problem)가 발생하여 패킷이 폐기된 상황임
* Data Section: 폐기된 패킷의 IP헤더와 메시지의 초반 8byte가 첨부됨
* 버퍼 오버플로우가 발생하면, 다수의 패킷이 누락되는데, 누락된 패킷 하나하나에 대한 quench 메시지가 source에게 전송됨
* source quench 메시지를 받은 source는 quench 메시지를 받지 않을 때까지 패킷 전송 속도를 낮추게 됨
* L4의 TCP 프로토콜에서 congestion과 flow control를 제공하기 때문에, source quench는 ICMPv6에서 사라짐.


#### Type11: Time Exceeded
![image](https://user-images.githubusercontent.com/49769190/176350552-671aa4b7-64b0-479b-9b9f-41b597a5abe2.png)
* TTL값이 0이된 패킷을 라우터가 폐기된 상황(Code0)이거나, Fragmentation된 패킷들 전체가 정해진 시간 내에 목적지 호스트에 도착하지 못해 패킷이 폐기된 상황(code1)
* Data Section: 폐기된 패킷의 IP 헤더와 메시지의 초반 8byte가 첨부됨

#### Type12: Parameter Problem
![image](https://user-images.githubusercontent.com/49769190/176350969-e0a386e5-acb0-469e-bc78-f3448d8aff48.png)
* 패킷의 특정 필드에 문제가 생긴 상황(code0)이거나, IP 헤더의 프로토콜 필드를 해석할 수 없는 상황(Unknwon Protocol, code1)
* pointer: 문제가 생긴 필드를 지목함
* ICMP 메시지에 문제가 생긴 헤더부분을 알리는 정보가 첨부
* Data Section : 폐기된 패킷의 IP 헤더와 메시지의 초반 8byte가 첨부됨

#### Type5: Redirection
![image](https://user-images.githubusercontent.com/49769190/176351023-1ffae0a6-ef5c-4893-a9ea-a2da5cc598a0.png)
* 네트워크 상에 더욱 빠른 경로가 검색된 상황
* code0: network-specific route(목적지 노드가 해당되는 네트워크로 메시지를 보내는 모든 경우, 타겟 라우터로 전송할 것을 지시)
* Code 1 : Host-Specific Route (목적지 노드로 메시지를 보낼 경우, 타겟 라우터로 전송할 것을 지시)
* Rest of the header : 더욱 빠른 경로에 해당되는 라우터의 주소(타겟 라우터)
* Data Section : 기전송된 패킷의 IP 헤더와 메시지의 초반 8Byte가 첨부
* Redirection 상황에서 패킷은 폐기되지 않고 정상적으로 Relaying(전송)
    * 일반적인 Host의 라우팅 테이블은 그 크기가 작고 수정이 거의 일어나지 않는다. 이 때문에 네트워크 상의 신설 라우터 정보들을 실시간으로 반영하지 못하는데, 이러한 제약을 인근의 라우터가 Redirection 메세지를 통해 Host에게 알리는 메커니즘이다.
    * Redirection은 본질적으로 오류가 아니므로, ICMPv6에서Redirection은 Informational Message로 재분류된다.
    * Redirection Message는 Source가 속한 네트워크의 라우터만이 보낼 수 있다.

#### Type8 or Type 0: Echo Request or Reply
![image](https://user-images.githubusercontent.com/49769190/176351050-724a6ec3-b9d0-4839-b526-ca55ee78307e.png)
* source가 destination에게 보낸 메시지를 destination이 다시 그대로 source에게 보내는 메시지임(echo-back)
* echo reply 메시지에는 request 메시지의 identifier와 sequence number, optional data값이 그대로 복사됨
* 네트워크 관리자가 IP 프로토콜이 정상적으로 동작하는지를 확인하기 위해 사용하는 메시지 형태임
* timestamp 메시지와 더불어 echo 메시지를 통해서도 클라이언트가 RTT를 측정할 수 있음
* 네트워크 관리 프로그램인 ping에서 source와 destination 사이의 네트워크가 원활히 동작하는가를 파악하기 위해 주로 이용되는 메시지 형태임

#### Type13 or Type14 : Timestamp Request or Reply
![image](https://user-images.githubusercontent.com/49769190/176351077-c4d77a78-6da7-45ca-8d53-404d039f8a33.png)
* source와 destination의 시간을 동기화하기 위해 사용하는 메시지 형태임
* timestamp reply 메시지에는 Request 메세지의 Identifier와 Sequence number 값이 그대로 복사
* timestamp 메시지를 주고 받으며, 클라이언트는 RTT를 측정할 수 있으며, 서버의 시간과 동기화할 수 있음
* timestamp Request or Reply 메시지는 ICMPv6에서 없어짐.
* RTT(Round Trip Time) : 전송된 패킷을 되돌려받기까지 소요되는 시간이다. 타임 서버에서의 처리 시간은 포함되지 않


### Mobile IP
stationary Device를 인터넷에 연결시키는 IP 프로토콜을 이동통신 창치까지 확장시킨 개념

Mobile IP는 두가지 addresses를 가지고 있음

1. Home Network
* Mobile Host(MH)의 베이스가 되는 네트워크를 의미
* MH는 홈 네트워크의 Home Agent(홈 에이전트)로부터 Home Address(홈 주소, IMH)를 부여받아 인터넷과 통신
* Home Agent는 Home Router에 위치하는 네트워크 S/W
* 홈 주소는 다른 네트워크로 이동해도 수정/삭제 되지 않는 고유한 주솟값
* Home Agent는 이동하는 MH를 Tracing한다. (즉, MH의 홈 주소와 현재 위치하고 있는 Foreign Network의 의탁 주소를 실시간으로 파악)

2. Foreign Network(외지 네트워크)
* 홈 네트워크 이외의 모바일 IP를 지원하는 네트워크를 의미
* MH가 외지 네트워크에 들어오게 되면, 해당 외지 네트워크의 Foreign Agent(외지 에이전트)가 제공하는 Care-of Address(의탁 주소, ICoA)를 부여받아 인터넷과 통신
* 의탁 주소를 부여받은 MH는 의탁 주소 정보를 Home Agnet에 저장시켜 Home Router가 지속적으로 MH를 Tracing 가능
* Foreign Agent는 Foreign Route* 혹은 MH**에 위치한 네트워크 S/W(외지 라우터가 MH에 부여한 의탁 주소와 MH가 자체적으로 부여한 의탁 주소에는 차이가 있으나, 기본적으로 Net-ID에는 외지 네트워크의 네트워크 주소가 부여)

![image](https://user-images.githubusercontent.com/49769190/176351111-7697d603-ccba-48c6-82d8-b86905a39822.png)


#### Phases of Packet Relaying in Mobile Network as IPv4 (IPv4 모바일 네트워크에서 패킷이 전달되는 세 가지 단계)

![image](https://user-images.githubusercontent.com/49769190/176351142-aa9b604e-61dd-4847-aa30-b0de259a8881.png)

1. Phase 1. Agent Discovery

* 모바일 IP를 지원하는 Router는 주기적으로 해당 네트워크에 라우터 광고 메시지를 전송한다.
* MH는 광고 메시지를 통해 해당 네트워크의 네트워크 주소를 알 수 있다.
* 외지 네트워크에서는 의탁 주소를 광고 메시지를 통해 전달받게 된다.

      Router Advertisement Message(라우터 광고 메시지)
      - Agent Advertisement Message(에이전트 광고 메시지)가 포함되어있다. 에이전트 광고 메시지속에는 해당 네트워크의 의탁 주소가 포함되어 있다.
      - 해당 네트워크의 Net-ID가 포함되어 있다. (이를 통해, 현재 속한 네트워크를 구분할 수 있다.)
      - 라우터에 의해 주기적으로 해당 네트워크에 뿌려지는 ICMP 메시지이다.

      Router Solicitation Message(라우터 요청 메시지)
      - MH가 라우터에게 보내는 메시지로, 자신이 속한 네트워크를 파악하기 위해 전송하는 ICMP 메시지이다.
      - Router가 주기적으로 광고 메시지를 전송하고 있으므로, 오랫동안 광고 메시지를 수신하지 못한 경우에 요청 메시지를 전송하게 된다.
      - Agent Solicitation Message(에이전트 요청 메시지)가 포함되어 있다.


2. Phase 2. Registration
* Foreign 네트워크에서 할당받은 의탁 주소를 Home Agent에 등록하는 절차이다.
![image](https://user-images.githubusercontent.com/49769190/176366044-f74c3a8d-4ca0-4037-b09b-753fb78eadd2.png)
* Registration Request format

![image](https://user-images.githubusercontent.com/49769190/176366096-c00bd178-4a93-46d9-b2b0-e70ead2bc5ea.png)
* Registration Reply format

*  Homa agent address : Home Router에 설치된 Agent의 주소
*  Identification : Registration Reply 메시지에 그대로 Copy되어 돌아오게 됨

3. Phase 3. Data Transfer
![image](https://user-images.githubusercontent.com/49769190/176366151-3e97e419-e0a5-4df5-a1a7-9e0fed3efd29.png)
* 패킷을 실질적으로 전달하는 절차
* Home Agent는 DB에 등록된 정보를 통해 MH가 홈 네트워크에 있는지, 외지 네트워크에 있는지를 판별함. 홈 네트워크에 있을 경우, 홈 네트워크로 곧장 보내고, 외지 네트워크에 있을 경우, IP Tunneling을 수행함.
* 패킷이 Home Agent에서 Foreign Agent로 향할 때, IP 헤더가 추가적으로 붙게 됨 (IP in IP, IP Tunneling, 그림의 2번 과정)
* IPv4에서 IP Tunneling은 Home Agent부터 Foreign Router에 있는 Foreign Agent까지 이어짐. Foreign Router는 도착한 패킷을 MH까지 Relaying함.
* 구조적으로, Remote 호스트는 모바일 호스트에 직접 패킷을 송신할 수 없다. (성능 저하의 주요한 원인이나, 다른 인터넷의 노드들이 가변하는 MH의 주소를 몰라도 된다는 장점 )
* 모바일 호스트는 Remote 호스트에 직접 패킷을 송신할 있음.

#### Agent Advertisement Format
![image](https://user-images.githubusercontent.com/49769190/176366240-38b77596-0a68-489b-be10-96c884f44cd4.png)


#### Ineffciency in Moblie IP
1. Double Crossing
![image](https://user-images.githubusercontent.com/49769190/176366268-04028402-2a4d-498b-832f-6b90a7b3a493.png)
* Mobile Host와 Remote Host가 같은 Foreign Network에 위치하는 경우 (Worst Case)
* 같은 네트워크에 위치함에도 불구하고, Home Agent를 거쳐 패킷을 송수신
* 네트워크에 위치함에도 불구하고, Home Agent를 거쳐 패킷을 송수신함.
* 갔던 길을 그대로 되돌아 온다는 점에서 Double Crossing이라는 이름으로 불림.

2. Triangle Routing (삼각 라우팅)

![image](https://user-images.githubusercontent.com/49769190/176366315-c4a2fae2-d657-4742-b84e-69eadecd529e.png)
* Remote Host와 Mobile Host가 서로 다른 Foreign Network에 위치한 경우 (가장 일반적인 경우)
* Remote Host가 그림의 Could-be path와 같이 최단 송신 경로가 있음에도 불구하고 Home Agent를 거쳐서 송신

       solution
       - 삼각 라우팅을 최소화하는 방법이다.
       - Home Router가 RH에게 MH의 위치를 지속적으로 알리는(Update) 방식이다.
       - MH의 위치를 모르는 Remote Host(RH)는 어쩔 수 없이 처음 메시지를 보낼 때에는 Home Agent에게 송신하게 된다. (통신 초반에는 불가피한 Triangle Routing)
       - MH에게 메시지를 보내고자 하는 RH의 존재를 알게 된 Home Agent는 MH의 위치를 알리는 Update 메시지를 RH에게 보내어 RH가 MH에게 직접 메시지를 보낼 수 있게 한다.
       - MH가 다른 Foreign Network로 이동하게 될 경우, 이동하기 전 네트워크의 Foreign Agent가 Home Agent에게 MH가 이동함을 알리고, Home Agent는 RH에게 이를 알려 다시금 RH가 MH에게 직접 메시지를 보낼 수 있게 Update 메시지를 새로 보낸다.



### ARP Protocol
![image](https://user-images.githubusercontent.com/49769190/176366350-95dfb6df-e3e9-489a-926b-465b692657e1.png)


* Address Resolution Protocol(ARP)
* IP 주소(L3 주소, 논리주소)를 받아 link주소(L2 주소, 물리주소)를 알아내는 프로토콜임
* 호스트나 라우터로 패킷을 전달하기 위해서, 해당 패킷에 논리 주소와 물리 주소가 모두 저장되어 있어야 함
* 논리 주소를 물리 주소로 물리 주소를 논리 주소로 변환하는 작업이 필요
* ARP는 Dynamic Mapping을 수행하기 위한 프로토콜임

 #### 논리 주소 (Logical Address)
  * s/w 구현된 주소, 전세계의 네트워크에서 한 호스트의 논리 주소는 유일함
  * TCP/IP 프로토콜에서의 논리 주소를 IP address라 함
  

 #### 물리 주소 (Physical Address)
  * H/W 구현된 주소, 물리 주소는 해당 Local Network내에서만 유효한 Local Address임
  * 물리 주소 중 하나로, 이더넷이나 Token Ring에서의 48bit MAC Address 있음
  
  
  #### Static Mapping(정적 변환)
  * 정적 변환 방법에서는 논리 주소와 물리 주소가 Mapping되어 있는 Table을 이용하여 변환 / 이러한 Table은 Network Device들에 저장되어 있음

※ Restrictions
- Network Device의 NIC(Network Interface Card)를 교체하여 새 물리 주소가 생기는 경우
- LocalTalk과 같은 LAN에서와 같이 컴퓨터가 부팅될 때 마다 물리 주소가 변경되는 경우
- Mobile 컴퓨터와 같이 네트워크를 이동하면서 물리 주소가 계속 변경되는 경우
- 위와 같은 한계에 대응하여, Table을 주기적으로 Update해야하는데,
  이러한 Update는 네트워크에 매우 큰 Overhead로 작용하게 된다.
  
 #### Dynamic Mapping(동적 변환)
 * 한 호스트가 다른 Device의 논리 주소만 알고 있는 경우, 해당 논리 주소를 통해 물리 주소를 알아내는 방식임
 * ARP는 논리 주소를 물리 주소로 Dynamic Mapping하는 프로토콜이고, RARP는 물리 주소를 논리 주소로 Dynamic Mapping하는 프로토콜
 * 현재 RARP는 DHCP로 대치되어 사용되지 않는 추세

        ARP가 필요한 경우
          - Case 1. 한 호스트가 같은 Physical Network상의 다른 호스트에게 메시지를 전송하고자 하는 경우
              * 두 호스트는 같은 물리 네트워크상에 있기 때문에 Receiver Host의 논리주소는 이미 알고 있는 상태
              * 즉, Receiver의 물리 주소만 상황이므로, ARP 프로토콜을 사용해야 함
             
![image](https://user-images.githubusercontent.com/49769190/176366401-2f156d36-7bad-4f3a-9042-06786fbf98f7.png)


        - Case 2. 한 호스트가 다른 Physical Network상의 호스트에게 메시지를 전송하고자 하는 경우
            * Sender는 자신의 Routing Table(Static Routing Table)을 참조하여 인접한 Router로의 NHA 주소(=인접한 라우터의 논리 주소)를 알아내어 이를 ARP를 통해 물리 주소로 변환
            * Sender에게 Routing Table이 없다면, Default Router의 논리 주소를 ARP를 이용하여 물리 주소로 변환
            * 즉, Case 2에서는 인접한 Router의 논리 주소가 ARP를 통해 물리 주소로 변환됨

![image](https://user-images.githubusercontent.com/49769190/176366441-252dcd22-1ea8-4de6-80e5-04ea54880df9.png)

        - Case 3. 한 Router가 다른 Router에게로 메시지를 전송하는 경우
              * 즉, 메시지가 네트워크 상의 중간경로에 위치한 경우
              * 이러한 경우, Sender Router는 Routing Table(Dynamic Routing Table)을 참고하여 Receiver Router로의 NHA(=Receiver Router의 논리 주소)를 알아내고, 이 NHA를 ARP를 이용하여 물리 주소로 변환
  
![image](https://user-images.githubusercontent.com/49769190/176366464-4bf80118-81c8-489d-9ea9-3bac2a4a5feb.png)

      
  
        - Case 4. 한 Router가 자신의 관활내에 있는 호스트에게로 메시지를 송신할 경우
              * 메시지가 다수의 물리 네트워크를 거쳐 Receiver에게로 도착하는 경우
              * 이 경우, Receiver의 논리 주소가 ARP를 통해 물리 주소로 변환

![image](https://user-images.githubusercontent.com/49769190/176366498-a1c7cfc2-7008-4545-acd3-671ce6f96a8e.png)


### ARP Operation
* ARP Protocol에서는 Sender측에서 Receiver측의 MAC 주소를 알기위해 행하는 ARP Request와 Receiver측에서 Sender측에게 요청한 MAC 주소를 알려주는 ARP Reply를 정의

### ARP request
* Receiver의 IP는 알고 있으나, Link 주소는 모르기 때문에(애초에 Link주소를 구하는 과정이다) / Question Symbol('?')로 패킷을 채움(사실, Question Symbol은 32Bit Field가 모두 0으로 채워서 표현)
* Link 주소를 모르기 때문에, Broadcast 방식(모든 Host에게 신호를 전송)으로 신호를 전송
* ARP Cahce*를 통해 ARP Request 과정이 생략

      ARP Cache
       - 기존에 통신했던 Host의 Link 주소를 저장하는 메모리
       - ARP 캐쉬에는 값을 저장하는 데에 유효시간이 존재하기 때문에 시간이 만료되면 다시 ARP Request 과정을 행해야 함.

      ARP Reply
       - ARP Reply는 ARP Request와 달리, Unicast(목적지 Host에게만 신호를 전송)방식으로 신호를 전송
       - Receiver는 Sender의 네트워크 주소와 물리주소 모두를 알고 있기 때문 (굳이 Broadcasting하여 Network에 부담을 줄 필요가 없음)
*** 
Example. A가 B와의 통신을 위해 ARP Request를 수행하는 예시
![image](https://user-images.githubusercontent.com/49769190/176366539-7bab1e03-c320-477d-b448-ef20580bdce9.png)
* System A는 System B의 Link Address를 모르기 때문에, 같은 Physical Network 상에 있는 모든 Host가 수신할 수 있도록 ARP Request를 Broadcasting
* 위 그림에서 검은색 실선은 Physical Path이고, 하늘색 실선은 Logical Path
* Ni는 i번째 시스템의 네트워크 주소(IP주소)를 의미하고, Li는 i번째 시스템의 링크 주소를 의미


### ARP Packet
![image](https://user-images.githubusercontent.com/49769190/176366584-fda04ae4-3664-493e-94b8-73b2edca0167.png)


 * Hardware Type (16Bit)
    * ARP가 수행되고 있는 네트워크의 유형을 정의하는 필드
    * 예를 들어, Ethernet의 경우, H/W Type 값은 1임
    * ARP는 어떠한 Physical Network에서도 사용될 수 있음

 * Protocol Type (16Bit)
    * 프로토콜을 정의하는 필드
    * 예를 들어, IPv4의 Protocol Type은 0x0800
    * ARP는 어떠한 상위 Layer Protocol과도 호환이 가능

 * Hardware Length (8Bit)
   * 물리 주소의 길이를 바이트 단위로 정의하여 저장하는 필드
   * 예를 들어, Dotted-Decimal 주소 체계(6Byte)를 사용하는 Ethernet의 경우, H/W Length값은 6임

 * Protocol Length (8Bit)
   * 논리 주소의 길이를 바이트 단위로 정의하여 저장하는 필드
   * 예를 들어, IPv4의 Protocol Length는 4

 * Operation (16Bit)
   * ARP Request Packet의 경우, Operation 필드에는 1이 저장되고, ARP Reply Packet의 경우, Operation 필드에는 2가 저장

 * Source Hardware Address (Variable Length)
   * 송신자의 물리 주소가 저장되는 가변길이 필드
   * 예를 들어, Ethernet에서 이 필드는 6Byte

 * Source Protocol Address (Variable Length)
   * 송신자의 논리 주소가 저장되는 가변길이 필드
   * 예를 들어, IPv4 주소를 사용하는 경우, 이 필드는 4Byte

 * Destination Hardware Adderss (Variable Length)
   * 수신자의 물리 주소가 저장되는 필드이지만, ARP는 이 수신자의 물리 주소를 알아내는 프로토콜이므로, ARP Request Packet의 경우, 이 필드는 모두 0으로 채워짐.
   * Source H/W Address와 마찬가지로, Ethernet에서 이 필드는 6Byte

 * Destination Protocol Address (Variable Length)
   * 수신자의 논리 주소가 저장되는 가변길이 필드
   * 예를 들어, 수신자의 주소가 IPv4 주소인 경우, 이 필드는 4Byte



## Unicast Routing Protocol🍅🍅

  * Unicast Communication상에서 최적의 비용을 갖는 통신 경로를 찾아내는 프로토콜
  * 라우터들은 라우팅 프로토콜을 이용하여 인터넷의 수정사항을 서로에게 알려 최적의 통신 경로를 갱신해나감.

![image](https://user-images.githubusercontent.com/49769190/176885164-839410a0-732f-4532-a5e3-8a9914410650.png)

  
        유니캐스트 통신: 하나의 sender와 하나의 receiver간의 통신을 의미, one-to-one 통신이라고 함.
        
* 인터넷은 AS(Autonomous System)의 관리 단위로, 자율 시스템은 단일 관리 기관 하에 있는 라우터와 네트워크 그룹을 의미
* 대규모의 인터넷을 AS로 나누어 divide and conquer 방식으로 다루기 위한 개념
* 각각의 AS끼리는 서로의 네트워크 구조를 공유하며, 외부의 네트워크 상황을 알게됨.

### Static Routing Table - Dynamic Routing Table(정적 라우팅 테이블 - 동적 라우팅 테이블)

  1. 정적 라우팅 테이블
    * 호스트가 갖고 있는 라우팅 테이블을 의미
    * ICMP Redirection 메시지를 받지 않는 한 거의 변하지 않음
    * 네트워크 변경 사항이 즉각 갱신되지 않고 테이블 크기가 크지 않음

   2. 동적 라우팅 테이블
    * 주로 라우터가 갖고 있는 라우팅 테이블
    * 네트워크의 변경 사항이 즉각 갱신, 테이블의 크기가 큰 편에 속함.


### Intradomain - interdonmain(도메인 내 라우팅 - 도메인 간 라우팅)
![image](https://user-images.githubusercontent.com/49769190/176885232-fe7e3bc2-dad5-4d72-9a69-9569fed1f32b.png)


1. Intradomain(도메인 내 라우팅)
* 자율 시스템 내에서의 라우팅
* 각 자율 시스템은 하나 이상의 intradomain 라우팅 프로토콜을 사용
* distance vector routing 알고리즘 기반의 RIP 라우팅 프로토콜
* Link state routing 알고리즘 기반의 OSPF 라우팅 프로토콜

2. Interdomain(도메인 간 라우팅)
* 자율 시스템 간의 라우팅
* 자율 시스템 간 라우팅을 처리하기 위해 interdomain 라우팅 프로토콜 사용
* path vector routing 기반의 BGP 라우팅 프로토콜

### Bellman-Ford Aigorithm(벨만 포트 알고리즘)
* 그래프 상, 임의의 노드 간의 최단거리 경로를 찾아내는 알고리즘
* 거리 벡터 라우팅 알고리즘의 기초가 되는 알고리즘


![image](https://user-images.githubusercontent.com/49769190/176885273-e4feeb6a-7d6f-4705-bf14-a479350bdc4c.png)

![image](https://user-images.githubusercontent.com/49769190/176885342-f907c799-14a0-4026-8fa7-703c55feac47.png)


### RIP (Routing Information Protocol)
* Distance Vector Routing Algorithm 기반의 라우팅 프로토콜이다.
* Intra Domain(Interior) 라우팅 프로토콜 중 하나이다.
* 고안된지 오래된 라우팅 프로토콜로, 오늘날 널리 쓰이는 Intra Domain 라우팅 프로토콜로는 OSPF가 있다.
* RIP은 UDP의 Well-Known Port 520에서 제공하는 서비스(즉, RIP 요청/업데이트 메시지는 User-Datagram 이다.)

<img width="771" alt="image" src="https://user-images.githubusercontent.com/49769190/176881985-b2f15ab3-b6dd-4d21-ade0-c5745f8dd11b.png">


### RIP Message Format

<img width="816" alt="image" src="https://user-images.githubusercontent.com/49769190/176882178-87e109b2-e2a9-4036-aa7b-e04a894a8385.png">
* RIP 프로토콜 하에서, 라우터들끼리 라우팅 정보를 주고받을 때 사용하는 메시지의 형식이다.
* Command : Request(요청)일 경우 1, Update(응답)일 경우 2로 설정된다. 응답메시지가 라우팅 정보를 담고있는 것이 일반적이다.
* Version : 본 포스트에서 설명하는 RIP의 버전은 1이다.
* Repeated 되는 필드(회색부분)에 Destination과 Cost에 해당되는 정보들이 입력된다.
* Family : TCP/IP의 경우, Family 값은 2로 고정된다.
* Network Address : Destination 정보에 해당된다.
* Distance : Cost 정보에 해당된다.

### RIP Request Message
<img width="817" alt="image" src="https://user-images.githubusercontent.com/49769190/176882351-4b6569e2-e78a-4991-bcb2-7feadb2ffe19.png">
* RIP 요청 메시지의 경우, Command 값이 1로 설정된다.
* RIP 요청 메시지의 경우, 아래와 같이 두 가지 형태로 존재하게 된다.

1. Request for some
* 지정한 네트워크에 대한 Cost를 요청하는 형태이다.
* Network Address에 알고자하는 네트워크의 주소를 입력하여 전송
* 다수의 네트워크에 대한 Cost를 알고자 하는 경우, 요청 메시지를 Repeat(반복; 연장)하여 전송한다.

2. Request for all
* 요청 메시지를 받게될 라우터가 알고있는 모든 라우팅 정보를 보내줄 것을 요청하는 형태이다.
* Network Address에 0.0.0.0(All 0s)을 입력하여 전송한다.
* 요청 메시지를 반복(연장)할 필요가 없다.

* RIP은 UDP에서 제공되는 서비스이므로, RIP 요청/업데이트 메시지는 User-Datagram임.


### Link State Routing Algorithm (링크 상태 라우팅 알고리즘)
<img width="510" alt="image" src="https://user-images.githubusercontent.com/49769190/176882741-7fc8f395-3d11-4699-9766-d4c143b38e76.png">
- OSPF 프로토콜은 링크 상태 라우팅 알고리즘을 기반으로 한 대표적인 알고리즘
- Link State란, 라우터 자신에게 연결된 Edge 정보(특정 노드와의 연결 여부와 Cost 등)를 의미한다.
- 링크 상태 라우팅 알고리즘은, 각 라우터들이 자신의 LSP(Link State Packet)*를 Flooding(플러딩)**하는 방식으로 동작한다.
- 결과적으로, 모든 라우터들이 Link State(Edge 정보)를 다 알게 되며, 모두가 Complete Network Topology를 파악한 상태가 된다.
- 각각의 라우터들은 LSP를 인접한 노드에게 주기적으로 전송하며, Link의 변화가 감지되면 그 즉시 LSP를 인접한 노드에게 전송하는 식으로 Update한다.
- 각각의 라우터 혹은 물리 네트워크 노드에서는 Shortest Path Algorithm을 이용하여 특정 노드로의 최단 경로를 계산한다. (대표적으로 Dijkstra Algorithm을 이용한다.) 

* LSP (Link State Packet; 링크 상태 패킷)
- 라우터 자신의 Link State를 저장한 패킷이다.

** Flooding(플러딩)
- 다른 라우터들에게 효과적이며 안전한 방법으로 LSP(Link State Packet)를 전송하는 방법이다.
- 인접한 라우터에 LSP를 전달하고, 이를 수신한 라우터가 다른 라우터에게도 전송하는 방식이다.

※ 실제 링크 상태 라우팅 알고리즘에서 노드는 라우터와 네트워크로 구성된다. (라우터만이 노드가 아니다.) 위 그림은 각 Link(Edge)마다 존재하는 하나 이상의 Network 노드가 생략된 형태이다.



### Link State Routing Algorithm의 수행과정 (4-Phase)
1. 모든 라우터들의 LSP의 생성

2. Flooding Dissemination of LSP to every other nodes
- 플러딩을 통한 모든 노드로의 LSP 보급

3. Dijkstra's Algorithm Formation of shortest path tree

4. Calculation of routing table

### OSPF (Open Shortest Path First)
<img width="817" alt="image" src="https://user-images.githubusercontent.com/49769190/176883101-172c5080-905d-4534-bdf9-15639fb85399.png">
1. Area
- AS내에 포함되는 호스트, 라우터, 네트워크의 집합이다.

2. Backbone Area
- 모든 Area들의 기본이 되는 Area를 의미한다.

3. Area Border Router
- 각 Area를 상호 연결하는 라우터이다.
- 양쪽 Area에 서로의 네트워크 정보에 대한 Summary를 공유하게 한다.

4. AS Boundary Router
- 각 AS를 상호 연결하는 라우터로, Backbone Area에 위치한다.


- 각 라우터들은 자신이 속한 Area의 Complete Network Topology를 바탕으로 라우팅 테이블을 생성한다.
- 즉, Area내에 위치하는 라우터들은 자신이 속한 Area의 Complete Topology를 알게 되고, 외부 Area의 Topology Summary를 알게 된다.
- Link State Routing Algorithm에 기반한 프로토콜이다.
- 각 라우터들이 링크 정보를 주고받음으로써, 네트워크 전체에 대한 Topology를 알게 되고, 전체 네트워크에 대한 최단경로를 주로 다익스트라 알고리즘을 통해 계산한다.
- Intra Domain(Interior) 라우팅 프로토콜 중 하나이다.
- RIP 프로토콜의 단점*을 개선했다.

* RIP은 대규모 네트워크에 적용할 수 없고, 하나의 Metric, 하나의 패킷 전송 경로만 생성할 수 있다는 단점이 있다. (자세한 내용은 본 블로그의 포스트 참조)



### OSPF Packet (OSPF 패킷)
<img width="817" alt="image" src="https://user-images.githubusercontent.com/49769190/176883455-58d42ebd-066d-4462-80f7-538ef1d54ad7.png">
- OSPF 패킷은 IP-Datagram(L3) 패킷 위에서 Encapsulation된다.
- OSPF 패킷은 크게 다섯 가지 종류로 구분된다.

1. Hello Packet
- 라우터가 Power-On되었을 때, 주변 라우터에게 보내는 메시지이다.

2. Database Description Packet (DB Description Packet)
- Hello 패킷을 수신한 라우터가 보내는 메시지이다.
- 라우팅 테이블에 대한 윤곽(개요)을 전송한다. (라우팅 테이블 전체를 전송하는 것이 아니다.)

3. Link State Request Packet
- DB Description 패킷을 수신한 후에도 추가적인 정보를 원할 때 보내는 요청 메시지이다.

4. Link State Update Packet
- Link State 요청 메시지를 수신한 라우터가 보내는 메시지이다.
- 5가지 종류의 링크*로 구성된다.

5. Link State Acknowledgment (Link State ACK)
- Link State Update 패킷에 대한 ACK 메시지이다.

### Path Vector Routing Algorithm (경로 벡터 라우팅 알고리즘)
<img width="633" alt="image" src="https://user-images.githubusercontent.com/49769190/176883794-4de38337-76e7-4db8-b633-92dbe90c2ab4.png">
- AS1~AS3의 각각의 Exterior 라우터(대표 라우터; R1~R3)들 간에 사용되는 라우팅 프로토콜이 Interdomain 라우팅 프로토콜이다.
- 각 Exterior 라우터는 자신의 Reachability(도달 가능성)를 다른 Exterior 라우터에게 알린다.
- Intradomain에서는 송신 경로를 NHA로써 표현하고, Interdomain에서는 송신 경로를 Path*로써 표현한다.

* Path : AS들의 Collection이다.

<img width="629" alt="image" src="https://user-images.githubusercontent.com/49769190/176883891-f3c380e2-3eba-4b40-9864-85b44e9571a2.png">
* 각 Exterior 라우터들의 라우팅 테이블을 표현한 

<img width="718" alt="image" src="https://user-images.githubusercontent.com/49769190/176883942-f430f2ac-81d1-4997-8397-233370124927.png">
* 위 그림은 Address Aggregation을 통해 간소화 한 라우팅 테이블을 표현한 것이다..
* 3가지의 경로들을 하나의 엔트리로 나타내기 위해 수퍼네팅을 수행한다.
* 경로가 3가지이므로, 2bit를 필요로 한다. 따라서 Net-Id가 2bit 줄어들게 된다.

* Path Vector 라우팅 알고리즘을 통한 Anycast 구현 방식
  * Anycast : 1 to Any Communication 형태로, 중복된 목적지 중 가장 최적의 경로로 연결하는 통신 형태이다. 
  * 다수의 목적지로부터 Source에게 Path가 전송되고, Source는 수신한 Path 중 거치는 Exterior 라우터의 수가 가장 적은 Path를 택하게 된다.

### BGP (Border Gateway Protocol)

- 1989년에 처음 도입되어 4번의 버전이 갱신되었다.
- 가장 많이 쓰이는 Interdomain 라우팅 프로토콜이다.
- BGP는 TCP의 Well-Known Port 179에서 제공하는 서비스이다.(즉, BGP 메시지는 Segment)

<img width="721" alt="image" src="https://user-images.githubusercontent.com/49769190/176884141-5b106b49-53c0-4944-a880-4f243d8b557a.png">
1. External BGP Session (E-BGP Session)
* 각 AS의 Exterior 라우터들이 서로 연결되는 절차이다.
* 각 Exterior 라우터들은 서로의 Reachability를 공유하게 된다.

2. Internal BGP Session (I-BGP Session)
* 각 AS의 Exterior 라우터(A1, B1)들은 자신의 AS의 Reachability를 파악하기 위한 절차이다.

### BGP Message🍎
<img width="589" alt="image" src="https://user-images.githubusercontent.com/49769190/176884320-05957bdc-e7d3-47c0-a1a6-25f78ab6f108.png">
* BGP 메시지의 Common Header(공통 헤더)의 형태임.
* Type 필드를 통해 아래 BGP 메시지 형태를 구분

<img width="768" alt="image" src="https://user-images.githubusercontent.com/49769190/176884397-548086f7-171c-4b0e-a06c-024714ada280.png">
1. Open Message
<img width="538" alt="image" src="https://user-images.githubusercontent.com/49769190/176884544-1963b258-48d4-47cc-ac77-93eb8361dff6.png">
* Exterior 라우터가 Power-on되고, 이웃의 Exterior와 E-BGP Session을 생성하기 위해 송신하는 메시지이다.

2. Update Message
<img width="653" alt="image" src="https://user-images.githubusercontent.com/49769190/176884586-77f751e6-a635-4009-9a6f-c555a999919f.png">
* Path Vector에 대한 정보를 담은 메시지이다.
* Withdrawn Routes : 무효화 된 경로를 의미한다. (다수의 네트워크가 저장될 수 있다.)
* Path Attributes :  Path Vector를 의미한다.
* Network Layer Reachability Information : 액세스 가능한 네트워크 주소를 의미한다.

* 즉, Path Attributes와 Network Layer Reachability Information가 Key 역할이다.

3. Keep-alive Message
<img width="628" alt="image" src="https://user-images.githubusercontent.com/49769190/176884664-27c56c3b-4232-4151-8b77-5d43722aa091.png">
* Open 메시지에 대한 ACK 메시지이다. (헤더만 존재한다.)
* 각 AS의 Exterior 라우터들은 서로 주기적으로 Keep-alive 메시지를 주고 받으며, 연결 여부를 지속적으로 파악한다.

4. Notification Message
<img width="619" alt="image" src="https://user-images.githubusercontent.com/49769190/176884776-f1ddddb7-4c54-499c-955a-1dd188776586.png">
* 오류가 발생했을 때, 오류에 관한 내용을 송신하는 메시지


### UDP(User Datagram Protocol)

      UDP는 손실 발생, 순서 보장하지 않는 단점이 있는데 왜 UDP를 사용하는지 의문이 들 수 있다. UDP는 연결을 하지 않기 때문에 연결에서 발생하는 지연이 없으며, 간단하며, 작은 세그먼트 헤더를 갖는다 -> 주로 멀티미디어 애플리케이션을 스트리밍 하는 경우에 사용된다. 손실이 발생해도 크게 상관이 없으며, 혼잡 제어, 복구 등이 없어 빠른 장점
* 구조가 가장 간단함.
* 비연결 서비스제공
* 헤더오 전송 데이터에 대한 체크섬 기능 제공


    32bits 길이를 가진다. 헤더에는 4개의 필드만이 존재하는데, 각각 16bit씩 가진다.
    
1. Source / Destination Port
* 송수신 프로세스의 할당된 네트워크 포트 번호
 
2.Length
* 프로토콜 헤더를 포함한 UDP 데이터그램의 전체 크기
 
3. Checksum
* 오류 검출

<img width="810" alt="image" src="https://user-images.githubusercontent.com/49769190/177028002-ef24237f-5439-4a3b-a3ef-30485348a404.png">


### TCP(Transmission Control Protocol)
<img width="653" alt="image" src="https://user-images.githubusercontent.com/49769190/177028949-500a04e1-e901-4890-ac3d-2dba5c6e5086.png">
* TCP는 애플리케이션 계층과 네트워크 계층 사이에 있으며 애플리케이션 프로그램과 네트워크 운영 사이의 중개자 역할을 함.
* 인터넷 통신에 있어서 중요한 역할함.

#### IP 주소와 포트번호
* IP주소는 source to destination을 위해 필요한 주소이며 Network Layer의 IP 헤더에 들어감.
* Port번호는 시스템이 1024번 이후 번호로 임의 지정해 주는 주소이며 Transport Layer에서 관여함.

#### Stream Delivery
<img width="698" alt="image" src="https://user-images.githubusercontent.com/49769190/177029223-47209664-6601-4756-b012-1738bdfe5ffc.png">
* byte 연속으로 데이터 전달
* Application에서 생성한 boundary 유지되는 경우 -> UDP의 데이터 전송 방식임.

* TCP의 경우, 비서는 강 사장이 전달한 사탕의 포장을 분해한 뒤 본인이 임의대로 재포장해 상대에게 보냄 -> boundary가 무너진 것임, TCP에서는 데이터가 바이트의 연속(낱개)으로 전송되며 이를 stream delivery 방식임.

#### Sending and Recieving Buffers
<img width="698" alt="image" src="https://user-images.githubusercontent.com/49769190/177029212-f34ad680-8c04-4a78-9a05-2f2d8fb8885f.png">
* TCP는 양방향으로 데이터를 전송
* 송신 버퍼의 Sent는 이미 보낸 data이며 상대방이 해당 데이터를 정상적으로 수신하지 못했을 때 재전송 할 목적으로 보관하고 있는, data의 copy본들이 저장되어 있다. 
* Not sent는 applicartion에게 받아 아직 보내지 않은 데이터이며 아무런 표시가 되어 있지 않은 empty 부분은 applicartion에게 받을 데이터를 보관할 빈 공간이다. 
* 수신 버퍼의 Not read에는 아직 읽지 않은 수신데이터가 보관되어 있다. 
* 버퍼에서는 누락된 데이터를 제외하고 제대로 도착한 데이터만 위로 올려보내준다. 
* 누락된 건은 상대방 Transport Layer와 Process - to - process로 연락을 주고 받아 재전송 받고, 데이터의 신뢰성을 확인한 후 상위계층(application)으로 전송함.

#### TCP Segments
* TCP는 데이터를 패킷으로 만들어 상대방에게 보내주며, 해당 패킷은 Transport Layer에서 segment라 함.
* 패킷 하나당 약 1024byte임
* 전송되는 패킷의 크기가 결정됨

#### Numbering System
* TCP는 패킷 누락에 책임이 있으며 누락 확인을 위해 각 패킷마다 번호를 부여
* 이 번호는 임의의 번호로 시작함.

***
Example) TCP 연결이 5,000바이트의 파일을 전송한다고 가정해 보자. 첫 번째 바이트는 10,001로 번호가 매겨졌다(랜덤). 데이터가 각각 1,000바이트를 운반하는 5개의 세그먼트로 전송될 경우 각 세그먼트의 시퀀스 번호는?
* 패킷에 있는 data의 첫번째 byte = 그 패킷의 sequence number
<img width="929" alt="image" src="https://user-images.githubusercontent.com/49769190/177029480-e37abbc2-d05d-4ab4-92b3-c8532411635e.png">

ACK(Acknowledgment, 확인 응답) : 패킷을 받았을 때 응답
<img width="648" alt="image" src="https://user-images.githubusercontent.com/49769190/177029525-dee7c7a3-8ff8-424b-8d5e-f2f3e6298957.png">

1. Selective ACK
* UDP 방식
* 받은 데이터의 byte 번호

2. Cumulative ACK
* TCP 방식
* 다음 번에 받고 싶은 데이터의 byte 번호


#### Segments
<img width="748" alt="image" src="https://user-images.githubusercontent.com/49769190/177029851-958541c2-700a-4bad-8278-c71539265bad.png">

* TCP의 헤더 크기는 기본 20byte ~ 60byte이다.
* 헤더의 크기가 유동적이기 때문에 헤더 안에 어디까지가 헤더이고 어디부터 data인지 표시

1. HLEN
* 4bits 
* 헤더의 길이를 나타냄.
* 4bits로는 1111(2) 즉, 10진수로 15까지 표현할 수 있는데, 헤더의 길이는 최대 60byte까지 나타날 수 있기 때문에 이진수로 60을 나타내려면 111100(2) 총 6bits가 필요
* 따라서 4bits로 60을 나타내기 위해 해당 수에 ÷4를 한다

***
Example) HLEN = 60(10) = 111100(2)

*  111100(2) ÷ 4 = 15(10) = 1111 ☞ 15로 60을 표현할 수 있다. 

Example) HLEN = 20(10) = 10100(2)

*  10100(2) ÷ 4 = 5(10) = 0101 ☞ 5로 20을 표현할 수 있음

* 헤더의 길이가 20바이트라면 ÷4를 해서 5를 보내고, 60바이트라면 ÷4를 해서 15를 보낸다.
* 받는 쪽에서는 ×4를 해서 헤더의 길이를 인식

***

#### Checksum
* 16bits
* 데이터의 오류 체크
* 헤더의 모든 내용 16bits씩 끊어와서 다 더함

#### Control Field
<img width="944" alt="image" src="https://user-images.githubusercontent.com/49769190/177030028-7981aaf8-5a7e-4d47-8ae9-3e0ed2658f0c.png">

* 각 필드는 각각 1bit.
* ACK: 1-번호를 보내니 반드시 보라고 상대에게 알려줌 / 0-상대는 헤더의 acknowledgment number 필드(16bits)에 쓰인 데이터를 쓰레기 취급함 
* SYN: 연결 요청 패킷
* FIN: 종료 요청 패킷

#### Pseudoheader added to the TCP segment
<img width="913" alt="image" src="https://user-images.githubusercontent.com/49769190/177030076-b7c9d2f7-213d-43e3-96c5-5300b2c7b73c.png">
* IP헤더로부터 Source IP주소, destination IP주소, 프로토콜 종류를 가져오고, TCP 헤더로부터 TCP 길이를 가져온다.
* 확실한 체크 위해 해당 정보를 붙여서 checksum을 구한다.
* 만약 checksum을 통해 비트오류를 발견한다면 해당 패킷을 통째로 버린다.(어떤 비트가 오류인지 모름)
* 전송 시에는 슈도헤더를 떼고 헤더만 보냄.

***
Example) checksum calculation at the sender
<img width="1043" alt="image" src="https://user-images.githubusercontent.com/49769190/177030164-4774280d-f6e1-4018-9a2e-821fd3b81c3c.png">
* 32bits IP헤더의 데이터를 16bits씩 끊어와서 모두 더한 뒤에 보수를 취한 뒤 checksum field에 저장.
* UDP의 checksum은 선택이지만 TCP의 checksum은 필수이다.

#### TCP Encapsulation
 <img width="606" alt="image" src="https://user-images.githubusercontent.com/49769190/177029776-78b8f7a2-324e-450a-a76e-b2d0d55108d9.png">
 
 <img width="865" alt="image" src="https://user-images.githubusercontent.com/49769190/177030440-12f12423-97bb-49e7-aa20-89b29cd01127.png">


### TCP Connection

#### Connection establishment using three-way handshake
<img width="813" alt="image" src="https://user-images.githubusercontent.com/49769190/177031281-f8c8e364-1a38-475c-8f40-f10ab2e4d9d5.png">
* data 전송 전 연결 setup 과정.
* 해당 과정이 끝나야 버퍼가 생성되고 data 전송이 가능하다.
* 서버는 클라이언트보다 먼저 실행해서 클라이언트의 연결 요청을 대기하고 있어야 함.

<순서>
1. 클라이언트는 Control field의 SYN에 1을 셋팅해 연결요청 패킷임을 명시한 뒤 해당 패킷을 서버에게 보내 연결을 요청한다. (seq: 8000- 랜덤 번호. SYN 패킷이 잘 도착했는지 확인하는 역할)
2. 서버는 ACK을 클라이언트에게 전송해 연결요청을 허가(SYN에 대한 응답)한다. 동시에 SYN을 클라이언트에게 보내 서버도 연결요청을 한다.(seq: 15000- 랜덤 번호 / ack: 8001- 8000번까지 패킷을 받았고 8001번을 보내달라는 응답)
3. 클라이언트는 서버가 보낸 SYN에 ACK을 보내 응답한다. (ack: 15001- 15000번까지 패킷을 받았고 15001번을 보내달라는 응답)
4. 연결 완료

#### Data transfer
<img width="574" alt="image" src="https://user-images.githubusercontent.com/49769190/177031340-f9bc47aa-3a6f-48a6-90a2-bcf5838b4c3c.png">
* 연결이 끝나고 데이터를 주고 받는 과정

#### Connection termination using three-way handshake
<img width="799" alt="image" src="https://user-images.githubusercontent.com/49769190/177031423-9dcfed53-2d15-4d38-b302-ae74b6fe9d4d.png">
* data 전송이 끝난 뒤 연결 종료 과정

<순서>
순서
1. 클라이언트는 Control field의 FIN에 1을 셋팅해 종료요청 패킷임을 명시한 뒤 해당 패킷을 서버에게 보내 연결 종료를 요청한다.
2. 서버는 ACK을 클라이언트에게 전송해 종료요청을 허가(SYN에 대한 응답)한다. 동시에 SYN을 클라이언트에게 보내 서버도 종료요청을 한다. 클라이언트 sending 버퍼 삭제.
3. 클라이언트는 서버가 보낸 SYN에 ACK을 보내 응답한다. 
4. 연결 종료 및 버퍼 삭제


#### Half-Close 반만 종료
<img width="690" alt="image" src="https://user-images.githubusercontent.com/49769190/177031467-3d8c7c03-0096-44eb-ad4e-c85a61b56772.png">
1. 클라이언트가 서버에게 FIN 요청을 보낸다.
2. 서버가 ACK을 보내 연결 종료 요청에 응답했다. 이때 클라이언트의 sending buffer가 소멸되지만 recieving buffer는 남아있으므로 서버가 보낸 데이터를 읽을 수는 있다. 
3. 클라이언트의 close 요청 수락 후에도 서버가 보낼 데이터 있으면 계속 보낸다. 서버는 클라이언트에게 보낼 데이터를 다 보내고 FIN을 보내 연결 종료를 요청한다. 
4. 클라이언트는 ACK을 보내 연결 종료 요청에 응답한다.(sending buffer가 삭제된 상태이므로 다른 말은 못하고 응답만 할 수 있음)
5. 연결 종료
 

#### Error Control
* TCP는 신뢰할 수 있는 transport layer 프로토콜이다.
* TCP로 데이터 스트림을 전송하는 응용 프로그램은 TCP에 의존해 전체 스트림을 반대쪽 끝에 있는 응용 프로그램에 오류 없이 순서대로 전달할 수 있다.
* TCP의 Error Control(오류 제어)는 checksum, acknowledgment, and time-out의 세 가지 tool 사용


* ACK에 대한 ACK은 존재하지 않는다. 즉, 내가 보낸 ACK을 상대방이 잘 받았는지 확인하는 ACK은 존재하지 않는다.
* 데이터는 순서가 잘못된 상태로 도착하여 receiving TCP에 의해 일시적으로 저장될 수 있지만, TCP는 순서가 잘못된 데이터가 프로세스에 전달되지 않도록 보장한다. → TCP는 receiving buffer에서 application으로 데이터를 전송할 시 제대로 된 데이터만 올려보낸다(신뢰성 보장). 
* 순서 바뀐 것은 아예 process로 전달되지 않음

#### Normal Operation
* 일반적인 데이터 전송 과정.
* sender가 data를 보내면 receiver는 보낸 data를 잘 받았고 다음 패킷을 보내달라는 의미로 ACK을 전송
* 이때 상대에게 전송하는 ACK의 갯수를 줄이기 위한 Rule 1, 2, 3이 존재

<img width="867" alt="image" src="https://user-images.githubusercontent.com/49769190/177032038-56e015da-d939-47b2-984b-e9815582600f.png">

1. Rule 1
* 데이터를 받았을 때 ACK을 보내야 하는데 ACK을 바로 보내는 게 아니라 Buffer에 보낼 데이터가 있는지 확인하고 보낼 데이터가 있으면 같이 보냄(= ACK가는 김에 데이터도 같이 가자)
 
2. Rule 2
* Sender는 패킷을 송신하고 나면 별도로 정의된 Timer(ACK-delaying timer)를 켜놓고 정해진 시간 동안 대기한다. 위의 그림에서는 지연 시간을 50ms로 설정하였다. 50ms까지 기다려도 Buffer에 보낼 데이터가 없을 시 데이터 없이 ACK만 전송한다.
 
3. Rule 3
* timer를 켜놓고 기다리는 중에 패킷이 하나 더 도착하면 더 이상 안 기다리고 바로 ACK을 전송한다.(=데이터가 없는 상황에 패킷 2개 들어오면 2개당 ACK 하나는 보내자)

### Congestion Control

#### Slow start, exponential increase
<img width="654" alt="image" src="https://user-images.githubusercontent.com/49769190/177033638-4c8c1ae7-2177-4698-a022-9d5c486a991d.png">
* Slow start 방식은 미리 정해진 값(Threshold)까지 패킷 양을 이전에 전송한 양의 2배씩 늘리고
* 미리 정해진 값에 도달하면 이후부터는 +1씩 보수적으로 전송량을 늘리는(Congestion avoidance) 방식 
* exponential increase: 전송량을 두 배씩 늘리는 방식

* 혼잡제어를 고려하지 않았을 때의 데이터 전송방식을 생각해 보자.(flow control) -> 왜 slow start이라고 부를까?
*만약 Receiver의 수신버퍼 크기가 6500byte라면 Sender는 초기에 수신 버퍼를 가득 채울 만큼의 패킷을 전부 전송한다. 이는 전송량을 1에서부터 시작하여 2배씩 늘려가는 slow start 방식보다는 훨씬 빨리 데이터를 전송할 수 있는 방법이다.
* 따라서 flow control보다 훨씬 느린 데이터 전송 방식


#### congestion avoidance, additive increase
* 데이터 혼잡을 피하기 위해서 tcp에서는 데이터 전송량을 결정
* 전송할 데이터의 크기, 즉 window size는 rwnd와 cwnd의 최솟값으로 정해짐.


<img width="817" alt="image" src="https://user-images.githubusercontent.com/49769190/177033527-59f9d02d-47c5-43a6-a0dd-40f29d261970.png">
* TCP에는 중앙에서 네트워크의 상태에 따라 각 connection의 데이터 전송량을 관리해 줄 관리자가 존재하지 않는다. 
* 따라서 각 connection에서는 자율적으로 데이터 전송량을 조절한다.
* 각 connection은 혼잡이 감지되지 않는 한 계속해서 데이터 전송량을 늘리는 방식으로 데이터를 전송함.
* Sender는 보낸 패킷에 대한 응답(Ack)이 무사히 도착했다면(packet loss가 발생하지 않았다면), 네트워크에 혼잡이 없었다고 생각한다.
* Congestion avoidance방식은 데이터에 혼잡이 발생하지 않는 한 이전 전송량에서 데이터를 하나씩 더 늘려 전송하는 방식이다.
* additive increase는 데이터를 하나씩 보수적으로 증가하는 방식이다. 
* 만약 packet loss가 발생한다면, 혼잡이 발생했다고 파악하고 해당 네트워크를 사용 중인 모든 connection은 데이터 전송량을 반으로 줄인다. 



* RTT(Round Trip Time, 왕복시간)
* 연결 setup 과정이 완료된 상태라고 가정.
* 이 그림에서 rwnd는 고려하지 않는다. 즉, rwnd는 충분히 크기 때문에 전송량에 영향을 미치지 않는다고 가정한다.



### 🍋참고🍋
* https://seungyooon.tistory.com/187
* https://velog.io/@hidaehyunlee/IP-address%EB%9E%80
* https://limkydev.tistory.com/168
* https://velog.io/@anjaekk/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-%EB%A9%80%ED%8B%B0%EC%BA%90%EC%8A%A4%ED%8C%85
* https://florescene.tistory.com/m/category/Computer%20Science/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC
