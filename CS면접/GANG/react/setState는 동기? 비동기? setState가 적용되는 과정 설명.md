# setState는 동기? 비동기? setState가 적용되는 과정 설명

## 1. setState의 비동기적 특성

-   setState는 비동기적으로 동작한다.
-   이는 성능 최적화와 일관성 있는 상태 업데이트를 위한 React의 설계 결정이다.

### 비동기 동장의 이유

-   성능 최적화 : 여러 상태 업데이트를 한 번에 처리하여 불필요한 렌더링을 줄인다.
-   일관성 : 부모와 자식 컴포넌트의 상태가 동시에 업데이트되어 일관성을 유지한다.

## 2. setState의 상세 작동 과정

### setState 호출

```jsx
this.setState({ count: this.state.count + 1 });
```

-   이 호출은 상태 업데이트를 즉시 실행하지 않고 업데이트 큐에 추가한다.

### 업데이트 스케줄링

-   react네는 여러 setState 호출을 모아서 배치 처리한다.
-   이 과정은 브라우저의 이벤트 루프와 밀접하게 연관되어있다.

### 상태 계산 및 병합

-   배치 내의 모든 업데이트를 처리하고 최종 상태를 계산한다.
-   객체 업데이트의 경우 얕은 병합(shallow merge)이 수행된다.

### 렌더링 예약

-   새로운 상태가 계산되면 React는 컴포넌트의 리렌더링을 스케줄링한다.
-   이 시점에서 아직 DOM은 업데이트 되지 않았다.

### 가상 DOM 업데이트

-   React는 새로운 상태를 기반으로 가상 DOM을 업데이트한다.
-   이전 가상 DOM과 새로운 가상 DOM을 비교한다.

### 실제 DOM 업데이트

-   가상 DOM의 변경사항을 실제 DOM에 적용한다.
-   이 과정은 효율적으로 수행되어 최소한의 DOM 조작만 이루어진다.

## setState의 비동기적 특성으로 인한 주의사항

### 즉시 상태 참조의 문제

```jsx
this.setState({ count: this.state.count + 1 });
console.log(this.state.count); // 업데이트된 값이 아닐 수 있다.
```

-   setState 직후에 상태를 참조하면 업데이트 전의 값일 수 있다.

### 연속적인 setState 호출

```jsx
this.setState({ count: this.state.count + 1 });
this.setState({ count: this.state.count + 1 });
```

-   이 경우, 예상과 달리 count가 2 증가하지 않을 수 있습니다.

### 해결책: 함수형 업데이트

```jsx
this.setState((prev) => ({ count: this.state.count + 1 }));
this.setState((prev) => ({ count: this.state.count + 1 }));
```

-   함수형 업데이트를 사용하면 이전 상태를 정확히 참조할 수 있습니다.

## 상태 업데이트 이후 작업 수행

### 콜백 함수 사용

```jsx
this.setState({ count: this.state.count + 1 }, () => {
    console.log("상태가 업데이트되었습니다.", this.state.count);
});
```

-   setState의 두 번째 인자로 콜백 함수를 전달하여 상태 업데이트 후 작업을 수행할 수 있다.

### componentDidUpdate 생명주기 메서드

```jsx
componentDidUpdate(prevProps, prevState) {
    if(this.state.count !== prevState.count){
        console.log('count가 업데이트되었습니다.', this.state.count)
    }
}
```

-   클래스 컴포넌트에서는 componentDidUpdate를 사용하여 상태 변경을 감지하고 추가 작업을 수행할 수 있다.

### useEffect 훅 (함수형 컴포넌트)

```jsx
useEffect(() => {
    console.log("count가 업데이트되었습니다.", count);
}, [count]);
```

-   함수형 컴포넌트에서는 useEffect 훅을 사용하여 상태 변경을 감지하고 추가 작업을 수행할 수 있다.
