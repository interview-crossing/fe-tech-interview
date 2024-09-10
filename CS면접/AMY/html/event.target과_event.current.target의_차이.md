### event.target과 event.current.target의 차이

###### 요약

event.target과 event.currentTarget은 JavaScript에서 이벤트가 발생했을 때 서로 다른 요소를 참조합니다.

<br />

###### 상세 설명

#### event.target

이벤트가 발생한 실제 요소를 가리킵니다. <br />
즉, 사용자가 클릭하거나 상호작용한 요소를 반환합니다. <br />
이는 이벤트가 버블링 중일 때도 변화하지 않습니다. <br />
예를 들어, 자식 요소를 클릭했다면 그 자식 요소가 event.target이 됩니다. <br />

#### event.currentTarget

이벤트 리스너가 붙어 있는 요소를 가리킵니다. <br />
이벤트 버블링 과정에서 현재 이벤트를 처리하고 있는 요소입니다. <br />
즉, 이벤트 리스너가 호출되는 그 시점의 요소를 반환합니다.

<br />
<br />

###### 예시 상황

```js
<div id="parent">
  <button id="child">Click Me</button>
</div>

<script>
  const parent = document.getElementById("parent");

  parent.addEventListener("click", function (event) {
    console.log("target:", event.target);          // 클릭된 실제 요소 (button)
    console.log("currentTarget:", event.currentTarget); // 이벤트 리스너가 붙어 있는 요소 (div)
  });
</script>
```

여기서 버튼을 클릭하면, event.target은 button 요소이고, event.currentTarget은 div 요소가 됩니다.
