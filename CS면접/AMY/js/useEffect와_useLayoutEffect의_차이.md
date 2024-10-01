## 🧐 Additional Information

### useEffect

애플리케이션 내 컴포넌트의 여러 값들을 활용해 동기적으로 부수 효과를 만드는 매커니즘 <br />
이 부수 효과가 '언제' 일어나는지보다 어떤 상태 값과 함께 실행되는지 살펴보는 것이 더 중요

첫 번째 인수로는 실행할 부수 효과가 포함된 함수를, <br />
두 번째 인수로는 의존성 배열을 전달

<br />
<br />

### useLayoutEffect

공식문서에 따르면, 이 함수의 시그니처는 useEffect와 동일하나, <br />
모든 DOM의 변경 후에 동기적으로 발생한다고 적혀 있습니다.

<br />

"함수의 시그니처가 useEffect와 동일하다"는 것은 두 훅의 형태나 사용 예제가 동일함을 의미합니다.

```js
function App() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log("useEffect", count);
  }, [count]);

  useLayoutEffect(() => {
    console.log("useLayoutEffect", count);
  }, [count]);

  function handleClick() {
    setCount((prev) => prev + 1);
  }

  return (
    <>
      <h1>{count}</h1>
      <button onClick={handleClick}>+</button>
    </>
  );
}
```

useLayoutEffect는 "모든 DOM의 변경 후에 useLayoutEffect의 콜백 함수 실행이 동기적으로 발생"한다는 점에 유의해야 합니다.

여기서 DOM 변경이란 렌더링을 말합니다. (실제로 브라우저에서 해당 변경 사항이 반영되는 시점 X)
<br />

따라서 실행 순서는 아래와 같습니다 :

    1. 리액트가 DOM을 업데이트
    2. useLayoutEffect 실행
    3. 브라우저에 변경 사항 반영
    4. useEffect 실행

<br />

따라서 순서 상으로는 useEffect가 먼저 선언돼 있지만 항상 useLayoutEffect가 useEffect보다 먼저 실행됩니다. <br />
이는 useLayoutEffect가 브라우저에 변경 사항이 반영 되기 전에 실행되기 전에 실행되는 반면 <br /> useEffect는 브라우저에 변경 사항이 반영된 후에 실행되기 때문입니다.

<br />

그리고 동기적으로 발생한다는 것은 <br />
리액트는 useLayoutEffect의 실행이 종료될 때까지 기다린 다음 화면을 그린다는 것을 의미합니다. <br />
즉, 리액트 컴포넌트는 useLayoutEffect가 완료될 때까지 기다리기 때문에 컴포넌트가 잠시 동안 일시 중지되는 것과 같은 일이 발생하게 됩니다. <br />
따라서 이러한 작동 방식으로 인해 웹 애플리케이션 성능에 문제가 발생할 수 있습니다.

<br />

###### Q. useLayoutEffect는 언제 사용하는게 좋을까?

useLayoutEffect 특성 상 DOM은 계산됐지만 이것이 화면에 반영되기 전에 하고 싶은 작업이 있을 때와 같이 반드시 필요할 때만 사용하는 것이 좋습니다. <br />
특정 요소에 따라 DOM 요소를 기반으로 한 애니메이션, 스크롤 위치 제어 등 화면에 반영되기 전에 하고 싶은 작업에 useEffect 대신 useLayoutEffect를 사용한다면 훨씬 더 자연스러운 UX를 제공할 수 있습니다.

<br />
<br />
