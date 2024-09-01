# URL 의 구성

> https://test.com:8080/main-page/query?q1=v1

1. Protocol
   -> `https`

2. Host Name
   -> `test.com`

3. Port
   -> `8080`

4. Pathname
   -> `main-page`

## Host

- 위의 목록 중, Host Name 과 Port 번호를 합쳐 Host 라고 한다.
  - `test.com:8080`

## Origin(출처)

- Protocol 과 Host(Host Name, Port) 를 합쳐, Origin 이라고 한다.
  - `https://test.com:8080`

<br/>
<br/>
<br/>
<br/>

# SOP (Same Origin Policy)

- "동일 출처 원칙"
- 웹 브라우저 보안을 위해 Origin(출처)가 동일한 서버와의 데이터 통신만 허용하는 정책

## 배경

과거에는 서버에서 데이터 및 html 문서를 한번에 구성하여, 클라이언트로 전송했기 때문에 다른 출처로의 데이터 요청을 의심하고 제한했다.

# CORS (Cross Origin Resource Sharing)

- "Cross-Origin Resource Sharing"
- 다른 출처 간의 요청-응답이라도 미리 지정된 출처인 경우, 리소스 공유를 허용하는 정책

## CORS Error

- 출처에 대한 설정이 되지 않았기 때문에, SOP 제한이 있는 상황임을 알림.
- CORS 가 가능하도록 설정하라는 내용으로 구성.

<br/>
<br/>

# CORS Error 해결하기

1. `Access-Control-Allow-Origin` 헤더 설정

- server 에서 응답 헤더를 구성할 때, `Access-Control-Allow-Origin` 설정을 하면 된다.
- 구체적으로 데이터를 공유할 출처를 `Access-Control-Allow-Origin` 설정의 값으로 명시한다.

2. Proxy 서버 사용

- 클라이언트가 출처가 다른 서버와 직접 요청-응답을 주고받는 대신, 같은 출처를 공유하는 proxy 서버로 요청을 보낸 뒤, 응답 또한 proxy 를 통해 대신 전달받는다.
- CORS 에러는 브라우저에만 적용되는 정책이기 때문에, 클라이언트 측 출처를 갖는 프록시 서버와 그것과는 다른 출처의 실제 서버간의 통신은 허용된다.
