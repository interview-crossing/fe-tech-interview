# REST
- _Representational State Transfer_ 의 약자


Restful API 란, **다음 조건을 갖추어 실행하는 리소스 교환** 을 의미한다.

1. HTTP URL 을 통해, 접근할 리소스를 명시
2. HTTP Method 를 통해, 동작(Verb, CRUD Operation)을 지정

<br/>
<br/>
<br/>
<br/>

# RESTful API 의 특징

- Server-Client(서버-클라이언트 구조)
- Stateless(무상태성)
- Cacheable(캐시 처리 가능)


# Hateoas(Hypermedia As The Engine Of Application State)

> REST 아키텍처의 중요한 구성 요소 중 하나로, 클라이언트가 서버와 상호작용할 때 
> 응답 내에 포함된 하이퍼미디어 링크를 사용해 애플리케이션 상태를 탐색하는 방법.

- 하이퍼미디어는 텍스트, 이미지, 링크 등의 다양한 형태의 미디어를 포함하는 데이터
  - 주로 링크를 사용한다.
- 클라이언트가 자원에 대한 세부 정보를 요청할 때, 
해당 자원과 관련된 다른 자원 또는 가능한 작업에 대한 링크가 함께 제공한다.
- 서버에서 애플리케이션의 다음 동작이 결정되도록 안내한다.
- (_RESTful API가 HATEOAS 를 구현해야 하는 것은 아니다._)


# RESTful API의 장점

- **단순하고 직관적**
  - HTTP 표준을 사용하고, 자원을 URI로 명확하게 표현한다.

- **확장성**
  - 서버-클라이언트 구조를 지향하기 때문에 시스템이 확장 가능하고, 서버의 부담을 낮춘다.

- **유연성**
  - 특정 플랫폼에 종속되지 않는다. 다양한 데이터 형식(JSON, XML 등)을 사용할 수 있다.


# RESTful API의 단점

- **표준 명세의 불명확성**
   - RESTful API는 설계 원칙을 제공하지만, 명확한 표준이 없어 API 설계자의 주관이 개입될 여지가 많다.

2. **복잡한 자원 간 관계**
   - 자원 간 관계가 복잡할 경우, 이를 URI로 표현하는 것이 어렵다.
   - 여러 자원에 대한 상태를 변경해야 할 때, 여러 API 요청이 필요해질 수 있다.

3. **HTTP Method의 제한성**
   - RESTful API는 HTTP 메서드(GET, POST, PUT, DELETE 등)에 의존하는데, 
   이는 CRUD 이상의 복잡한 동작을 표현하는 데 한계가 있을 수 있다.

4. **Over-fetching & Under-fetching 문제**
   - 클라이언트가 자원에 대한 요청을 할 때, 필요한 데이터만 가져오는 것이 어려울 수 있다.
   - Over-fetching: 불필요한 데이터를 많이 가져오는 문제.
   - Under-fetching: 추가 데이터를 얻기 위해 여러 번의 요청을 해야 하는 문제.

5. **HTTP의 특성에 의한 비효율성**
   - RESTful API는 HTTP 프로토콜을 사용하므로, 통신 시 헤더와 같은 추가적인 메타데이터가 붙는다.
   - 불필요한 데이터 전송이 발생할 수 있어, 네트워크 비용이 증가할 수 있다.

6. **보안 이슈**
   - RESTful API는 Stateless한 특성 때문에, 매 요청마다 인증을 처리해야 한다.
   - OAuth, JWT 등 인증 방식을 사용하더라도 추가적인 설정과 관리가 필요하다.