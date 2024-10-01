## 🧐 Additional Information

#### 인터넷 프로토콜 스위트 (internet protocol suite)

- 인터넷에서 컴퓨터들이 서로 정보를 주고받는 데 쓰이는 프로토콜 집합
- TCP/IP 4계층 모델 혹은 OSI 7계층 모델로 설명하기도 함.
- 각 계층들은 특정 계층이 변경됐을 때 다른 계층이 영향을 받지 않도록 설계

<p align="center">
<img width="70%" src="https://github.com/user-attachments/assets/875ec11c-36c5-46f4-9b44-ea133f822086" />
</p>

<br />
<br />

###### Transmission Control Protocol / Internet Protocol

#### TCP/IP

- 네트워크에서 사용되는 통신 프로토콜의 집합
- 계층들은 프로토콜의 네트워킹 범위에 따라 네 개의 추상화 계층으로 구성

<p align="center">
<img width="50%" src="https://github.com/user-attachments/assets/b4f9d2be-9d3b-4cf5-b1f6-3c408c9e3a69" />
</p>

<br />
<br />

#### transfer layer (전송 계층)

- 송신자와 수신자를 연결하는 통신 서비스 제공
- 애플리케이션과 인터넷 계층 사이의 데이터가 전달될 때 중계 역할
- 대표적으로 TCP, UDP

<br />
<br />

#### TCP

- 패킷 사이의 순서를 보장
- 연결지향 프로토콜을 사용해 연결
- 신뢰성을 구축해 수신 여부를 확인
- 신뢰성 확보를 위해 3-way handshake 라는 작업을 진행
- 가상회선 패킷 교환 방식 사용

<br />

###### 가상회선 패킷 교환 방식

- 각 패킷에는 가상회선 식별자가 포함됨
- 모든 패킷을 전송하면 가상회선이 해제됨
- 패킷들은 전송된 순서대로 도착하는 방식

<br />

###### 3-way handshake

클라이언트와 서버가 통신할 때 세 단계의 과정을 거치는 것

- SYN 단계
- SYN + ACK 단계
- ACK 단계

<br />
<br />

#### UDP

- 패킷 사이의 순서를 보장 X
- 수신 여부 확인 X
- 단순히 데이터만 주는 데이터그램 패킷 교환 방식 사용

<br />

###### 데이터그램 패킷 교환 방식

- 패킷이 독립적으로 이동하며 최적의 경로를 선택해 이동
- 하나의 메세지에서 분할된 여러 패킷들은 서로 다른 경로로 전송될 수 있음
- 도착한 순서가 다를 수 있는 방식

<br />
