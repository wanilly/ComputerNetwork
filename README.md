# Computer-Network⚽
  경북대학교 22-S
  
***
 
  ## Network Layers
  ### 1. OSI 7 Layers
![image.png](https://boostnote.io/api/teams/KyrG5EEUe/files/c797d11fd5b98b9403071c7427db3c45c52e1de693f716653c23d42c287f6bfe-image.png)
  ### 2. Internet Protocol
  layer 5, 6, 7을 하나로 묶어서 이해하는 모델
![image.png](https://boostnote.io/api/teams/KyrG5EEUe/files/4051e464414839151978b2f6aec4600b7d061be4a3e09722b72151a6f9c94bbe-image.png)

![image.png](https://boostnote.io/api/teams/KyrG5EEUe/files/c8564b16e0d3d7770c8a0fb8f3b410eb4b9ca5bc6a288cfefc64f3d88079c562-image.png)
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
![image.png](https://boostnote.io/api/teams/KyrG5EEUe/files/d6f7eefdebc53bb30c884c4c57cf3cf8f5b06f3c88b21ff86007b57a7d1acb14-image.png)  
![image.png](https://boostnote.io/api/teams/KyrG5EEUe/files/1e1bbbeff1d3daa61a681c26412de15408ef8037c53000e05d52da76dab2564e-image.png)


   #### Datagram approach
   * 비연결 서비스(패킷 간 관계 없음)
   * 각 패킷은 헤더에 있는 destination address 정보를 기반으로 라우팅 됨
   * 패킷헤더 -> 목적지 주소 확인 -> 포워딩 테이블에서 아웃풋 인터페이스로 패킷 전달🏅

 
 
  ### IP Address
    * IP 주소: TCP/IP 프로토콜의 IP layer에서 인터넷에 연결된 각 장치를 식별하기 위해 사용되는 식별자
    * IPv4 주소: 32bits, 전세게의 하나뿐인 유일한 주소이다. 약 40억개의 주소가 존재한다.
 
      원래 IP주소는 binary 형태의 32bits 숫자이다. 이를 byte 단위로 끊어서 10진법으로 표현하여 사용한다.
      
  ![image.png](https://boostnote.io/api/teams/KyrG5EEUe/files/f7e56b93ee70eb2ac336666a9e2766f245e8d40ccef264d7991cf6e758033ed2-image.png)

    ** 2진법을 10진법으로 
    128, 192, 224, 240은 알고 있자!
![image.png](https://boostnote.io/api/teams/KyrG5EEUe/files/d11d329713928c86a5c94776859eb816615a72cf0666ae6ad6145907c435d12d-image.png)
    * IPv4는 4byte로 표현해야 함, 0 ~ 255 사이의 10진수 .으로 구분하여 나타냄, 0.0.0.0 ~ 255.255.255.255
    
    
  ### IPv6 주소
    IPv6에서 주소 길이를 128비트, 보통 16진수 8개를 쓰고 :로 구분한다
![image.png](https://boostnote.io/api/teams/KyrG5EEUe/files/898de27caf5b185e070fdb67e7b1d5adcf36f0cc9ce01dc178a11e21f5e3f059-image.png)


  ### IP 주소의 클래스?
   IP주소에는 클래스가 있고 이 클래스의 개념을 알아야 어디까지가 네트워크 영역이고, 호스트 영역인지 알 수 있다. 즉, 하나의 IP주소에서 네트워크 영역과 호스트 영역을 나누는 방법이자 약속임
   IP 주소를 3개의 클래스로 나누는 이유는 네트워크 크기에 따른 구분이라고 생각하자!
   하나의 네트워크에서 몇 개의 호스트 IP까지 가질 수 있는 가에 따라 클래스를 나눌 수 있음.
  
  ![image.png](https://boostnote.io/api/teams/KyrG5EEUe/files/9084e58339c5ed9c0e02608dbe0f1a4f77e1c8580f20ad631fb0125845cb2cd1-image.png)
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
  
  
![image.png](https://boostnote.io/api/teams/KyrG5EEUe/files/8ade52f9f7f37b50081a6384c1628aa4526899300c64d887b98291fcbd86c679-image.png)



## Delivery and Forwarding of IP packets
  ### Direct Delivery
  ![image.png](https://boostnote.io/api/teams/KyrG5EEUe/files/238bfe7e5f8ac696419e10d649caf43ab9ee3a8da5d1115e16c2cb517b2e1d73-image.png)
  
  * 같은 link(Physical Network)에 연결된 노드로부터 패킷을 직접 전달받는 형태를 말함 / 패킷을 전달한 노드를 deliverer(전달자)
  * Link 내 통신에서 전달자는 다른 호스트가 될 것이고 외부 인터넷을 통해 유입된 패킷의 전달자는 해당 Link의 라우터가 될 것임
  * 패킷이 갖고 있는 목적지 IP주소의 Network 필드와 전달자의 주소의 Network 필드는 일치할 것임 -> 같은 물리네트워크 안의 노드임

  ### Direct Delivery
  ![image.png](https://boostnote.io/api/teams/KyrG5EEUe/files/4ab2fc7bde839a6eb5687b9592b6b3942c099fd8daa39636bf09010371cd36d1-image.png)
  
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
   ![image.png](https://boostnote.io/api/teams/KyrG5EEUe/files/cb442d5db2fe315cec6832fe5591bd54801a598fc29f21ab141f77822268b996-image.png)
   
   * 같은 네트위크에 연결된 모든 호스트에 대한 interface, NHA 주소 엔트리를 갖는 대신, 같은 네트워크에 연결된 모든 호스트를 하나의 엔트리로 간주하는 방식
   * 네트워크 지정 라우팅 테이블은 호스트 지정 라우팅 테이블보다 간결한 형태로 유지되어 처리속도에서 큰 차이가 남

   3. Host-Specific Routing Table
   * 네트워크에 연결된 모든 호스트에 대한 interface, NHA 주소를 모두 저장하는 방식임
   * 다른 특별한 이유로 인해 효율성을 희생하는 방식임
   
   4. Default Method
   ![image.png](https://boostnote.io/api/teams/KyrG5EEUe/files/d15e114a660b076f9af65c8f14d48c9a7b040684b5efa7f7d3af983f092e5268-image.png)
   
   * 몇 가지 목적지에 대한 entry를 따로 정의하고 자주 보내지는 경로를 디폴트로 지정하는 방법
   * 디폴트 엔트리의 네트워크 주소와 마크는 0.0.0.0임
   * 네트워크 필드 추출은 마스크와 목적지 주소의 AND 연산을 통해 이루어짐, 다른 엔트리와 매칭되지 않은 목적지 주소가 0.0.0.0과의 AND 연산이 수행되면 그 결과 또한 0.0.0.0이 되어 엔트리의 네트워크 주소인 0.0.0.0과 매칭되는 원리 / 다른 엔트리와 매칭되지 않으면 무조건 디폴트 엔트리와 매칭될 수 밖에 없는 구조임
   
  
***
Example)
 그림을 참고하여 R1(라우터)에 대한 라우팅 테이블을 그리고 주어진 목적지 주소들의 포워딩 프로세스를 서술
  
 1. 180.70.65.140
 2. 201.4.22.35
 3. 18.24.32.78

![image.png](https://boostnote.io/api/teams/KyrG5EEUe/files/3423283b53628f6c341faefdeebff7624cdbee5f80237bbcc01187f1066292ef-image.png)

![image.png](https://boostnote.io/api/teams/KyrG5EEUe/files/6b0f3798ca29c6f8d8ac0e7e2fc389a981f45d17af75902911044591ce1fb093-image.png)

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
  
     
![image.png](https://boostnote.io/api/teams/KyrG5EEUe/files/aed43e1b73e6c8dc663082cc14a03a3fa294b4d45c6a5329413e9a86951d61e2-image.png)

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
![image.png](https://boostnote.io/api/teams/KyrG5EEUe/files/604276d1b8b3a3261dd9e8ec38bd4538714f0efe13f3115846b08eb38ba6d579-image.png)



### Internet Protocol Version4(IPv4)🔥
![image.png](https://boostnote.io/api/teams/KyrG5EEUe/files/16829eb3725dd3c9102ebcd6484d6f5cf4a5e8917b7ef4d1452f8cba71775561-image.png)

* L3에 속하는 프로토콜로, 현재 버전(IPv4)와 버전 6(IPv6)가 공존해있는 상황임
* L2로부터 전달받은 Frame을 라우팅 테이블을 참조하여 현재 Host 보내진 패킷이면 처리하여 L4로 올리고 다른 호스트를 목적지로 하는 패킷이면 적절한 인터페이스 주소와 NHA를 검색하여 패킷을 전달함
* NHA는 논리 주소 형태이므로 ARP를 통해 물리 주소로 변환되어 전송됨
* 물리 네트워크로 전송되기 전에 전송할 패킷이 해당 물리네트워크의 수용가능한 IP-Datagram의 최대 크기를 초과하면 Fragmentation을 진행함
* IP 프로토콜의 보조 프로토콜로 IGMP와 ICMP가 존재함
* IGMP(Internet Group Management Protocol): 멀티 캐스팅에 이용되는 프로토콜임. 멀티캐스팅이 가능하기 위해서는 클라이언트가 멀티 캐스트 그룹에 가입/탈퇴하는 기능(Join/Leave)이 필요하게 되는데, 그 기능을 관리하는 프로토콜임
* ICMP: destination에서 오류가 발생하면, 패킷을 폐기하고 소스에게 이 사실을 통보하는 역할을 하는 프로토콜임



### Datagrams (IP-Datagram Header Structure)
![image.png](https://boostnote.io/api/teams/KyrG5EEUe/files/7b9437375453da42a73865ab29d1a93c7316ff8c88c186a80025d55d67ddeecf-image.png)

* IP Datagram(L3 패킷)에서 헤더의 길이느 20 ~ 60Byte로 구성 (표준 헤더는 20Byte 크기임. 최대 40Byte가 추가됨)
* L3 패킷에서 데이터의 길이는 0 ~ 65515Byte로 구성
* L3 패킷의 최소 길이는 20Byte, 최대 2^16 - 1Byte로 구성


![image.png](https://boostnote.io/api/teams/KyrG5EEUe/files/45720cbe26ec86a814365f55826e2631a02931161578142bc525a5380c47eaa9-image.png)
* 그림에서 하나의 Row는 4Byte 크기 / 흰색 바탕의 내용들은 표준 헤더를 구성하는 요소들(5 Rows를 구성하고 있으므로, 표준 헤더의 크기는 20Byte) 
* 회색 바탕의 내용은 옵션 헤더를 구성(옵션 헤더는 0 ~ 40Byte 사이의 크기)

<span style="color:rgb(245, 235, 13)">데이터그램은 헤더부분과 상위 계층으로부터 받아온 데이터 부분으로 나뉨. 데이터 부분은 상위 계층에서 내려보낸 그대로 사용, 헤더 부분만 네트워크 계층에서 만들어 데이터 부분과 합쳐줌으로써 데이터그램을 만듦.</span>

`1. VER (Version): IP 프로토콜의 버전을 의미합니다. IP 프로토콜은 IPv4와 IPv6가 현재 사용되고 있으며, 4자리 비트로 이루어져 있기 때문에, IPv4의 경우 0100, IPv6의 경우에는 0110으로 표기됨
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
10. Source / Destination IP Address: 각각 32 비트로 이루어지며 송신과 수신자의 IP 주소가 기록되어 있음`


