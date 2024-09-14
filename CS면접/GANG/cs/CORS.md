# CORS란?

-   웹 브라우저는 기본적으로 '동일 출처 정책(Same-Origin Policy)'을 따른다.
-   이 정책은 한 출처에서 로드된 문서나 스크립트가 다른 출처의 리소스와 상호작용하는 것을 제한한다.
-   여기서 '출처'는 프로토콜, 도메인, 포트의 조합을 말한다.

## 필요성

-   현대 웹 애플리케이션에서는 프론트엔드와 백엔드가 다른 도메인에 있는 경우가 많다.
-   CDN이나 서드파티 API를 사용하는 경우도 흔하다.
-   이런 상황에서 동일 출처 정책은 너무 제한적이기 때문에 CORS가 필요하게 되었다.

## 작동 방식

### 단순 요청

-   GET, HEAD, POST 중 하나의 메서드를 사용
-   Content-Type이 application/x-www-form-urlencoded, multipart/form-data,text/plain 중 하나
-   커스텀 헤더를 포함하지 않음 이런 경우, 브라우저는 그냥 요청을 보내고 서버의 응답을 확인한다.

### 프리플라이트 요청

-   단순 요청 조건을 만족하지 않는 경우
-   브라우저는 먼저 OPTIONS 메서드로 프리플라이트 요청을 보낸다.
-   서버가 허용한다고 응답하면, 실제 요청을 보낸다.

### 주요 CORS 헤더

-   Access-Control-Allow-Origin : 어떤 출처에서의 요청을 허용할지 지정
-   Access-Control-Allow-Methods : 허용할 HTTP 메서드 지정
-   Access-Control-Allow-Hedad : 허용할 헤더 지정
-   Access-Control-Allow-Credentials : 인증 정보(쿠키 등) 포함 여부
-   Access-Control-Max-Age : 프리플라이트 요청 결과를 캐시할 시간

## CORS 구현

### 백엔드

-   Node.js / Express의 경우

```jsx
app.use(
    cors({
        origin: "https://example.com",
        methods: ["GET", "POST"],
        allowedHeaders: ["Content-type", "Authorization"],
    })
);
```

-   Spring Boot의 경우

```java
@CrossOrigin(origins = "https://example.com")
@RestController
public class MyController { ... }
```

### 프론트엔드

-   fetch 사용 시

```jsx
fetch("https://api.example.com/data,", {
    credentials: "include", // 쿠키 포함 시
});
```

-   axios 사용 시

```jsx
axios.get("https://api.example.com/data", {
    withCredentials: true, // 쿠키 포함 시
});
```

## 주의 사항

-   `*`를 사용한 와일드카드 허용은 보안상 위험할 수 있다.
-   인증이 필요한 요청의 경우, Access-Control-Allow-Origin에 구체적인 출처를 지정해야 한다.
-   프리플라이트 요청의 캐싱을 적절히 설정하여 성능을 개선할 수 있다.

---

### CORS에서 '\*'를 사용한 와일드카드 허용은 실제로 모든 경우에 다 작동하지 않는다.

1. 인증 정보를 포함한 요청의 제한

-   '\*'를 사용할 때의 가장 큰 제한은 인증 정보(credentials)를 포함한 요청과 함께 사용할 수 잆다.
-   즉, 쿠키나 HTTP 인증을 사용하는 요청의 경우 '\*'로 설정된 Access-Control-Allow-Origin은 무시된다.

2. 실제 동작

-   프론트엔드에서 credentials: 'include' 또는 withcredentials: true로 요청을 보냈을 때
-   서버에서 Access-Control-Allow-Origin: '\*'로 응답하면,
-   브라우저는 이를 유효하지 않은 CORS 설정으로 간주하고 요청을 차단한다.

3. 이유

-   이는 보안상의 이유 때문인데, 인증 정보를 포함한 요청을 모든 출처에 허용하는 것은 매우 위험할 수 있기 때문이다.

4. 해결 방법

-   인증이 필요한 요청의 경우, Access-Control-Allow-Origin에 구체적인 출처를 명시해야한다.
-   예: Access-Control-Allow-Origin: https://example.com
-   또한, Access-Control-Allow-Credentials: ture 헤더도 함께 설정해야 한다.

5. 동적 Origin 설정

-   여러 출처를 허용해야 하는 경우, 요청의 Origin 헤더를 확인하고 동적으로 Access-Control-Allow-Origin을 설정할 수 있다.
-   이 방법을 사용하면 허용된 출처 목록을 관리하면서도 유연하게 대응할 수 있다.

6. 예시

```jsx
const allowedOrigins = ["https://example.com", "https://example2.com"];

app.use((req, res, next) => {
    const origin = req.headers.origin;
    if (allowedOrigins.includes(origin)) {
        res.setHeader("Access-Control-Allow-Origin", origin);
        res.setHeader("Access-Control-Allow-Credentials", "true");
    }
    next();
});
```

결론, '\*'를 사용한 와일드카드 허용은 단순한 요청에는 사용할 수 있지만, 인증이 필요한 중요한 요청에는 사용할 수 없다.
보안과 기능성 사이의 균형을 위해, 가능한 구체적인 출처를 지정하는 것이 좋다.

---

### 디버깅

-   CORS 오류는 주로 브라우저 콘솔에서 확인 가능하다.
-   서버 로그와 함께 확인하면 문제 해결에 도움이 된다.
