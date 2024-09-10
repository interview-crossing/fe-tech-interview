### HTML 렌더링 도중 JavaScript가 실행되면 렌더링이 멈추는 이유

렌더링 도중에 자바스크립트가 실행되면 렌더링이 멈추는 이유는 자바스크립트가 싱글 스레드로 동작하기 때문입니다. <br />
브라우저는 자바스크립트 실행과 HTML 렌더링을 동시에 수행할 수 없습니다.

<br />

#### 1️⃣ 싱글 스레드 모델

자바스크립트는 이벤트 루프를 사용해 하나의 스레드에서 실행됩니다. <br />
즉, 한 번에 하나의 작업만 처리할 수 있습니다. <br />
이 때문에 자바스크립트가 실행 중이면 브라우저의 렌더링 엔진은 일시적으로 멈춥니다.

#### 2️⃣ 블로킹 코드

자바스크립트가 브라우저의 메인 스레드에서 실행되며,
동기적인 코드나 시간이 오래 걸리는 작업이 있을 경우, 브라우저는 그 작업을 마칠 때까지 다른 작업을 중지합니다. <br />
HTML이나 CSS를 그리는 작업 역시 자바스크립트가 실행 중이면 중단됩니다.

#### 3️⃣ DOMContentLoaded와 자바스크립트

자바스크립트 파일을 `<script>` 태그로 로드하는 경우, 자바스크립트는 HTML을 파싱하던 중간에도 실행됩니다. <br />
이때, 자바스크립트가 실행되는 동안 HTML 파서는 멈추고 자바스크립트 실행이 끝난 후 다시 파싱을 재개합니다.

<br />
<br />

#### 해결 방안

이 문제를 해결하기 위해 자주 사용되는 방법은 defer 또는 async 속성의 사용. <br />
이 속성들을 통해 자바스크립트가 HTML 파싱을 방해하지 않도록 지연 실행할 수 있습니다.

- defer: HTML 파싱이 끝난 후 자바스크립트를 실행합니다.

```js
// example

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Defer Example</title>
  <!-- JavaScript will be loaded and executed after HTML parsing -->
  <script src="script.js" defer /> ✅
</head>
<body>
  <h1>Hello, World!</h1>
  <p>example of defer</p>
</body>
</html>
```

- async: 자바스크립트를 병렬로 다운로드한 후 바로 실행하지만, HTML 파싱이 중단될 수 있습니다.

```js
// example

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Async Example</title>
  <!-- JavaScript will be loaded asynchronously and executed as soon as it's ready -->
  <script src="script.js" async /> ✅
</head>
<body>
  <h1>Hello, World!</h1>
  <p>example of async</p>
</body>
</html>
```

이와 같은 특성 때문에 렌더링 도중 자바스크립트가 실행되면 잠시 멈춤 현상이 발생합니다.
