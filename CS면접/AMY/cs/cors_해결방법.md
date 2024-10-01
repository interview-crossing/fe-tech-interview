## 🧐 Additional Information

### CORS?

- Cross Origin Resource Sharing 의 약자로 교차 출처 리소스 공유란 의미
- 한 도메인이 다른 도메인의 리소스에 엑세스할 수 있게 해주는 보안 메커니즘
- 다른 출처 간의 요청-응답이라도 미리 지정된 출처인 경우, 리소스 공유를 허용하는 정책
- 최신 브라우저에서 구현된 동일 출처 정책 때문에 등장

<br />

#### same origin policy (SOP)

동일한 출처에 대한 정책

SOP 정책은 '동일한 출처에서만 리소스를 공유할 수 있다.'라는 법률을 가지고 있다.

자바스크립트에서의 요청은 기본적으로 서로 다른 도메인에 대한 요청을 보안상 제한한다.
브라우저는 기본으로 하나의 서버 연결만 허용되도록 설정되어 있기 때문이다.

즉, 동일 출처(Same-Origin) 서버에 있는 리소스는 자유로이 가져올수 있지만,
다른 출처(Cross-Origin) 서버에 있는 이미지나 유튜브 영상 같은 리소스는 상호작용이 불가능하다는 말이다.

##### 왜 이런 정책이 필요할까?

사실 출처가 다른 두 어플리케이션이 자유로이 소통할 수 있는 환경은 꽤 위험한 환경이다.

만일 제약이 없다면, 해커가 CSRF(Cross-Site Request Forgery)나 XSS(Cross-Site Scripting) 등의 방법을 이용해서
우리가 만든 어플리케이션에서 해커가 심어놓은 코드가 실행하여 개인 정보를 가로챌 수 있다.

따라서 이러한 악의적인 경우를 방지하기 위해,
SOP 정책으로 동일하지 않는 다른 출처의 스크립트가 실행되지 않도록 브라우저에서 사전에 방지하는 것이다.

<br />

#### Origin (출처)

**origin = protocol + host + port**

출처는 프로토콜(http/https), 사이트 도메인과 포트 번호를 합친 URL을 말한다. <br />
이 세 가지의 값이 동일하다면 브라우저는 동일 출처라고 판단한다.<br />
반대로 프로토콜, 호스트, 포트 중 하나라도 자신의 출처와 다를경우 브라우저는 정책상 차단하게 된다.

<p align="center">
<img width="80%" src="https://github.com/user-attachments/assets/92e2287a-004a-4ef7-8664-8e94260c4dbd" alt="url sample image" />
</p>

```
- Protocol(Scheme) → http, https
- Host → 사이트 도메인
- Port → 포트 번호
- Path → 사이트 내부 경로
- Query string → 요청의 key와 value값
- Fragment → 해시 태크
```

<br />

### CORS는 사실 해결책이다

##### 교차 출처 리소스 공유 (Cross-Origin Resource Sharing)

결국 웹개발자를 괴롭히던 시뻘건 에러 메세지는 사실 브라우저의 SOP 정책에 따라 다른 출처의 리소스를 차단하면서 발생된 에러이며, CORS는 다른 출처의 리소스를 얻기위한 해결 방안 이었던 것이다.

요약하자면 **SOP 정책을 위반해도 CORS 정책에 따르면 다른 출처의 리소스라도 허용한다는 뜻**이다.

##### 브라우저의 CORS 기본 동작 살펴보기

① 클라이언트에서 HTTP요청의 헤더에 Origin을 담아 전달
② 서버는 응답헤더에 Access-Control-Allow-Origin을 담아 클라이언트로 전달
③ 클라이언트에서 Origin과 서버가 보내준 Access-Control-Allow-Origin을 비교

결국 CORS 해결책은 서버에서 Access-Control-Allow-Origin 헤더에 허용할 출처를 기재해서 클라이언트에 응답하면 되는 것이었다. <br />
즉, 백엔드 개발자가 고쳐야될 부분...👀

<br />
<hr />

References.

- [악명 높은 CORS 개념 & 해결법 - 정리 끝판왕](https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-CORS-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC-%ED%95%B4%EA%B2%B0-%EB%B0%A9%EB%B2%95-%F0%9F%91%8F)
