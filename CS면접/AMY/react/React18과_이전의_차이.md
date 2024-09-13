## 🧐 Additional Informations

### 자동 배칭(Automatic Batching)

> 레스토랑에서 종업원이 손님이 주문하는 첫번째 메뉴를 듣자마자 주방으로 달려가지 않듯이 Batching은 반드시 필요한 하나의 리렌더링을 수행한다.

React 18에서는 여러 상태 업데이트를 하나의 렌더링 주기로 자동으로 묶어서 성능을 최적화합니다. <br />

React 18 버전 이하에서는 리액트의 이벤트 핸들러 내부의 state update 작업에 대해서만 batching이 가능했습니다.<br />
브라우저의 이벤트가 실행되는 중에만 batching을 수행했기 때문에 이벤트가 종료된 후에 실행되는 경우는 batching이 불가능했습니다.

하지만 React 18 버전 이후부터는 18 이전에 포함되지 않았던 작업에 대해서도 batching을 자동으로 수행될 수 있도록 변경되었습니다.

React18에서 제공하는 `ReactDOM.createRoot` 메서드를 기반으로 렌더링을 진행할 경우 모든 state update 작업은 자동으로 batching 처리되는데 이 기능을 Automatic Batching 이라고 합니다.

<br />
<br />

### 동시성 모드(Concurrent Rendering)

React 공식 문서에선 Concurrency를 다음과 같이 설명하고 있습니다.

> Concurrency is not a feature, per se.
> It’s a new behind-the-scenes mechanism that enables React to prepare multiple versions of your UI at the same time.

즉, 동시성 그 자체로는 기능이 아니고, React에서 여러 버전의 UI를 동시에 준비할 수 있도록 하는 메커니즘이라는 겁니다.

동시성 모드는 컴포넌트가 백그라운드에서 렌더링되는 기능을 통해 UI의 응답성을 높입니다. <br />
이를 통해 사용자가 방해받지 않고 상호작용을 계속할 수 있도록 도와줍니다. <br />
React 18에서는 이 기능이 기본적으로 적용됩니다.

<br />

실제론 동시에 실행하지는 않지만, CPU가 현재 실행중인 프로세스를 중단하고 다른 프로세스를 실행하는 작업인 context switching을 하면서 ‘동시에 실행되는 것처럼 보이게 하는 것’이 바로 Concurrency...

<br />
<br />

### useTransition & useDeferredValue Function

##### 탄생 배경

###### Blocking Rendering

React 18 이전까지는 렌더링 시 발생하는 문제점이 하나 있었습니다.

브라우저의 메인 스레드는 싱글 스레드이기 때문에 한 번에 한 가지의 작업만 할 수 있습니다. <br />
HTML을 파싱하거나 JS를 실행하거나 화면에 렌더링하는 등, 모든 작업을 하나씩 처리해 나갑니다.

그런데 만약 연산이 오래 걸리는 화면을 렌더링해야 한다면 어떻게 될까요? <br />
페이지 지연이 발생하여 사용자가 불편을 겪는 Blocking Rendering이 발생하게 됩니다.

이러한 문제를 해결하기 위해 추가된 기능이 바로 useTransition hook입니다.

<br />

#### useTransition

useTransition은 동시성 모드와 함께 사용되는 훅으로, UI 업데이트를 더 부드럽게 처리할 수 있도록 해줍니다. <br />
비동기적인 UI 전환을 '덜 중요한' 작업으로 취급하여 사용자에게 더 빠르고 응답성 있는 경험을 제공합니다.

#### useDeferredValue

이 함수는 useTransition과 비슷하게 우선순위를 낮춰서 concurrent features를 사용할 수 있는 hook입니다.

<br />

차이점으론 ‘상태를 업데이트하는 코드’를 래핑하여 우선순위를 낮추는 useTransition과 달리 useDeferredValue는 ‘값’의 업데이트 우선순위를 낮춘다는 것입니다.

또한 React 팀원인 Dan Abramov의 말에 따르면 useDeferredValue는 상태를 props로 받는 등 제어할 수 없을 때 사용하는 것을 권장하고 있습니다.

<br />
<br />

### Suspense의 개선

React 18에서는 서버 사이드 렌더링과 클라이언트 사이드 렌더링 모두에서 Suspense가 개선되어 데이터 로딩 시점에 더 유연하게 사용할 수 있습니다. <br />
이로 인해 컴포넌트가 비동기적으로 로딩될 때 로딩 스피너를 보여주고, 준비되면 다시 렌더링하는 것이 더 쉬워졌습니다.

<br />
<br />

### 서버 컴포넌트 지원(Experimental)

React 18에서는 서버 컴포넌트가 실험적으로 도입되었습니다. <br />
서버에서만 렌더링되고 클라이언트로 전송되지 않는 컴포넌트를 작성할 수 있어, 더 빠른 로딩과 더 적은 클라이언트 사이드 자원 사용이 가능합니다.

<br />
<br />
<hr />

references.

- [React 18 - 동시성 렌더링](https://tecoble.techcourse.co.kr/post/2023-07-09-concurrent_rendering/)
