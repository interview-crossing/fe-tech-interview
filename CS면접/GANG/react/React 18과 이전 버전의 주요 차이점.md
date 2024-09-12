# React 18과 이전 버전의 주요 차이점

## 1. 동시성

-   동시성은 React 18의 가장 중요한 새 기능이다
-   이를 통해 React는 UI 없데이트의 우선순위를 정하고 중단하거나 재개할 수 있게 되었다.

### useTransition 훅

-   긴급하지 않은 상태 업데이트를 표시할 수 있다.
-   이를 통해 중요한 업데이트(예: 타이핑)가 덜 중요한 업데이트(예: 검색 결과 표시)로 인해 차단되지 않도록 할 수 있다.

### useDeferredValue 훅

-   긴급하지 않은 부분의 리렌더링을 지연시킬 수 있다.

## 2. 자동 배치(Automatic Batching)

-   React 18 이전에는 React 이벤트 핸들러 내에서만 상태 업데이트가 배치 처리되었다.
-   이제는 Promise, setTimeout, 네이티브 이벤트 핸들러 또는 기타 이벤트 내부의 업데이트도 자동으로 배치 처리된다.

```jsx
// React 17 이전
setTimeout(() => {
    setCount((c) => c + 1); // 리렌더링 발생
    setFlag((f) => !f); // 리렌더링 발생
}, 1000);

// React 18
setTimeout(() => {
    setCount((c) => c + 1); // 리렌더링 발생하지 않음
    setFlag((f) => !f); // 리렌더링 발생하지 않음
    // 여기서 한 번의 리렌더링만 발생
}, 1000);
```

## 3. 새로운 렌더링 API

-   createRoot
    -   ReactDOM.render() 대신 사용된다. 동시성 기능을 활성화함
-   hydrateRoot
    -   서버 사이드 렌더링을 위한 새로운 API

```jsx
// React 17
ReactDOM.render(<App />, document.getElementById("root"));

// React 18
const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<App />);
```

## 4. Suspense 개선

-   서버 사이드 렌더링에서 Suspense를 지원한다.
-   이를 통해 서버에서 렌더링된 콘텐츠의 일부를 클라이언트에서 지연 로딩할 수 있다.
-   새로운 SSR 아키텍쳐
    -   스트리밍 서버 렌더링과 선택적 hydration을 지원한다.

## 5. 새로운 훅

-   useId() : 서버와 클라이언트에서 안정적인 고유 ID를 생성한다. 주로 접근성 속성에 사용된다.
-   useTransition()과 useDeferredValue() : 위에서 설명한 대로 동시성을 지원한다.
-   useSyncExternalStore(): 외부 저장소를 구독하기 위한 새로운 훅이다.
-   useInsertionEffect(): CSS-in-JS 라이브러리를 위해 설계된 새로운 버전의 useEffect이다.

## 6. 스트릭트 모드 변경

-   개발 모드에서 컴포넌트를 자동으로 재마운트하여 효과 정리(cleanup)의 중요성을 강조한다.

## 7. 플러싱 우선순위 변경

-   React는 이제 브라우저가 페인트하기 전에 모든 효과를 플러시한다.
-   이는 효과가 화면 업데이트를 차단하지 않도록 하기 위함이다.
