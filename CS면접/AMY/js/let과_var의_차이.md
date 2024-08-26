## 🧐 Additional Informations

### var

범위(Scope): var로 선언된 변수는 함수 스코프(Function Scope) <br />
함수 내에서 선언된 var 변수는 그 함수 전체에서 유효 <br />
하지만 블록 스코프를 가지지 않기 때문에, 블록 내에서 선언된 var 변수는 해당 블록 바깥에서도 접근이 가능 <br />

변수 호이스팅(Hoisting): var로 선언된 변수는 호이스팅(hoisting)됨 <br />
이는 변수가 선언되기 전에 해당 변수에 접근할 수 있다는 것을 의미 <br />
하지만 초기화는 선언 이후에 이루어지므로, 선언 전에 변수를 참조하면 undefined를 반환

재선언 및 재할당: O

<br />
<br />

### let

범위(Scope): let은 블록 스코프(Block Scope) <br />
let으로 선언된 변수는 해당 블록 내에서만 유효 <br />
블록 바깥에서는 접근 불가 <br />

변수 호이스팅(Hoisting): O
var와는 달리 초기화 전에 변수를 참조하려고 하면 ReferenceError가 발생 <br />
이는 "Temporal Dead Zone(TDZ)" 때문... <br />

재선언 : X <br />
재할당: O <br />

<br />
<br />

### const

범위(Scope): 블록 스코프 <br />
let과 마찬가지로, 블록 내에서만 유효

변수 호이스팅(Hoisting): O <br />
let과 동일하게 초기화 전에 참조하면 ReferenceError가 발생

재선언 및 재할당: X <br />
단, const로 선언된 객체나 배열의 경우에는 내부 속성이나 요소를 변경할 순 있음

<br />
<br />

### 요약

<table>
  <thead>
    <tr>
      <th>키워드 명</th>
      <th>범위(Scope)</th>
      <th>호이스팅(Hoisting)</th>
      <th>초기화 전 접근 반환 값</th>
      <th>재선언</th>
      <th>재할당</th>
      <th>비고</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>var</code></td>
      <td>함수 스코프</td>
      <td>O</td>
      <td><code>undefined</code></td>
      <td>O</td>
      <td>O</td>
      <td>블록 스코프를 지원하지 않음</td>
    </tr>
    <tr>
      <td><code>let</code></td>
      <td>블록 스코프</td>
      <td>O</td>
      <td><code>ReferenceError</code></td>
      <td>X</td>
      <td>O</td>
      <td>"Temporal Dead Zone(TDZ)" 적용</td>
    </tr>
    <tr>
      <td><code>const</code></td>
      <td>블록 스코프</td>
      <td>O</td>
      <td><code>ReferenceError</code></td>
      <td>X</td>
      <td>X</td>
      <td>객체와 배열의 내부 변경은 가능</td>
    </tr>
  </tbody>
</table>

<br />
<br />

#### 선언 전 접근 시 발생하는 값에 차이가 발생하는 건 스코프와 연관이 있을까?

스코프는 변수의 유효 범위를 정의하지만, 호이스팅과 함께 고려할 때 그 유효 범위 안에서도 접근 방식이 달라질 수 있습니다.

변수를 선언하기 전 접근 시 발생하는 값은 스코프와 관련이 있지만, 보다 구체적으로는 호이스팅의 동작 방식에 따른 결과입니다.

var로 선언된 변수는 함수 스코프를 가지며, 함수 내의 어느 위치에서든 접근이 가능합니다. 호이스팅이 발생할 때, 변수 선언은 최상단으로 끌어올려지지만, 초기화는 원래의 위치에서 이루어집니다. 이로 인해 변수를 선언하기 전에는 undefined를 반환합니다. 즉, var 변수는 스코프 내 어디에서든 접근할 수 있지만, 초기화 전에는 값이 undefined로 설정되어 있습니다.

let과 const는 블록 스코프를 가지며, 블록 내에서만 유효합니다. 이들은 호이스팅이 발생하지만, 선언되기 전에는 접근할 수 없는 "일시적 사각지대(Temporal Dead Zone, TDZ)"에 있습니다. TDZ는 선언 전 접근 시 ReferenceError를 발생시킵니다. 이는 블록 스코프 내에서도 변수를 접근할 수 있는 시점이 제한된다는 것을 의미합니다.

결론적으로, 스코프는 변수가 유효한 범위를 정의하고, 호이스팅은 변수 선언이 끌어올려지는 방식을 결정합니다. 따라서 var, let, const 각각의 호이스팅 동작 방식은 스코프와 관련이 있지만, 변수의 접근 가능 시점에서 중요한 차이를 만듭니다. var는 선언 전 접근 시 undefined를 반환하지만, let과 const는 TDZ로 인해 ReferenceError를 발생시킵니다.

<br />
