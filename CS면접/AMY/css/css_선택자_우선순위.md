## 🧐 Additional Informations

인라인 스타일 **>** Id 선택자 **>** 클래스 선택자 / 속성 선택자 / 가상 클래스 선택자 **>** 요소 선택자

위의 우선순위는 일반적인 경우이지만, 가상 클래스나 가상 요소 선택자는 추가적인 우선순위를 갖기도 합니다.

<br />

### 인라인 스타일 (inline-style)

- HTML 요소에 직접 적용된 스타일
- example) **`<div style="color: red;">`** 과 같이 스타일이 직접 지정

<br />

### ID 선택자

- **`#`**으로 시작
- ID는 문서 내에서 고유한 값 (마치라잌 PK)
- example) **`#myDiv {color: blue;}`**와 같이 사용 가능

<br />

### class 선택자

- **`.`**으로 시작
- example) **`#divs {width: 200px;}`**와 같이 사용 가능

<br />

### 속성 선택자

- **`[]`**의 형태로 표시
- example) **`input[type=button] {background-color: green;}`** 와 같이 사용 가능

<br />

### 가상 선택자

- `:hover`, `:focus` 등의 형태로 표시

<br />

### 요소 선택자

- 해당하는 요소 이름 전부에게 동일한 스타일 적용
- example) **`div {color: green;}`**와 같이 사용 가능

<br />

### !important

또한, 중요도를 나타내는 **`!important`**도 있습니다.
이는 어떤 스타일 선언에 **`!important`**를 붙이면 해당 선언이 다른 모든 스타일을 우선합니다.
하지만 **`!important`**는 남용하지 않는 것이 좋습니다.

<br />
