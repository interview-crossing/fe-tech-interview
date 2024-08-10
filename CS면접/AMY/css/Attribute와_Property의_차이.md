## 🧐 Additional Informations

### HTML Attribute (속성)

HTML 태그에 추가되어 태그의 동작을 제어하거나 추가 정보를 제공하는 값

HTML 태그 내에 사용되며 요소의 초기 설정값을 정의하는 역할

example) `<input type="text" value="Hello">`에서 `type`과 `value`는 속성

[ 특징 ]

- **초기값 설정**: 요소의 초기 설정값을 지정
- **HTML 문서에서 사용**: 주로 HTML 태그 내에서 사용
- **문자열로 저장**: 대부분의 HTML 속성 값은 문자열로 저장
- **DOM 접근**: 자바스크립트를 통해 `getAttribute`와 `setAttribute` 메서드를 사용하여 속성 값을 읽고 쓸 수 있음
  ```jsx
  <img src="image.jpg" alt="Description">
  ```

---

### CSS Property (프로퍼티)

CSS 스타일링에서 사용되는 속성으로, HTML 요소의 스타일과 레이아웃을 정의

CSS에서 사용되거나 자바스크립트 DOM 객체의 속성으로 사용되며 요소의 스타일과 배치를 동적으로 제어하는 역할

example) `color`, `font-size`, `margin` 등

[ 특징 ]

- **동적 제어**: 요소의 스타일과 레이아웃을 동적으로 제어 가능
  - example) `color`, `font-size`, `margin` 등
- **CSS에서 사용**:
  CSS 파일이나 `<style>` 태그 내에서 사용
  자바스크립트를 통해 `style` 객체를 사용하여 프로퍼티 값을 설정 가능
- **다양한 데이터 타입**: 프로퍼티 값은 숫자, 문자열, 색상 등 다양한 데이터 타입을 가질 수 있음
  ```jsx
  .example {
    color: blue;
    font-size: 16px;
  }
  ```

---

## HTML Attributes + CSS Property

HTML 속성과 CSS 프로퍼티는 종종 함께 사용되며, 자바스크립트 DOM에서 상호작용 가능

- **HTML 속성에서 CSS 프로퍼티로**
  HTML 요소의 속성 값이 요소의 스타일을 결정하는 경우
  ```jsx
  <div id="myDiv" style="color: red;"></div>
  ```
- **자바스크립트를 통한 동적 변경**
  자바스크립트를 사용하여 HTML 속성과 CSS 프로퍼티를 동적으로 변경 가능
  ```jsx
  const element = document.getElementById("myDiv");

  // HTML 속성 접근
  console.log(element.getAttribute("id")); // 'myDiv'

  // HTML 속성 설정
  element.setAttribute("id", "newId");

  // CSS 프로퍼티 접근
  console.log(element.style.color); // 'red'

  // CSS 프로퍼티 설정
  element.style.color = "blue";
  ```
