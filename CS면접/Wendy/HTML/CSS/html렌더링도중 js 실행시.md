html 렌더링도중 js가 실행되면 html파싱이멈추는 이유

-   js 가 돔트리를 변경할수도 있기때문
-   파싱이 중단되지않으면 아직 그려지지않은 돔트리에 접근하여 오류 발생률이 높아지고 렌더트리가 완성되지않았는데 자바스크립트가 돔트리를 변경시킬수도 있음.

## 간략한 브라우저 렌더링 과정

DOM 트리 → CSSOM 트리 → 렌더트리 → 레이아웃 → 페인트

-   서버로부터 HTML 자원을 받아와서 DOM 트리를 생성한다.
-   서버로부터 CSS 자원을 받아와서 CSSOM 트리를 생성한다.
-   DOM Tree와 CSSOM Tree로 브라우저에 레이아웃을 잡아줄 렌더트리를 생성한다.
-   렌더트리 노드 있는 속성이나 스타일을 기반으로 브라우저에 크기, 위치, 크기에 맞게 레이아웃을 잡는다.
-   브라우저에 페인트 한다.

## html파싱 블로킹 현상 해결방법

-   async : js파일 로드를 html파싱과 비동기적으로 동시에 진행 -> but, js파일 실행시에는 멈추긴함
-   defer : async와 같지만. js파일 실행시 DOM이 생성된 이후에 진행된다는 차이점이 있음

## 그렇다면 왜 css는 파싱 중단하지않나?

-   스타일 시트는 이론적으로 dom 트리를 변경하지않음.
