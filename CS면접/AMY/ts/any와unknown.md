## 🧐 Additional Information

any 타입과 unknown 타입의 차이

## any와 unknown

any는 타입 검사를 완전히 무시하고, 어떤 값이든 허용하며, 이는 타입 안전성을 해칩니다.
unknown은 타입 검사를 요구하여, 타입이 확인되기 전까지 안전하게 사용할 수 있습니다.

<br />

#### any

타입스크립트에서 모든 타입을 허용하는 '모든 것을 받아들이는' 타입입니다.
any로 설정된 변수는 타입스크립트의 엄격한 타입 검사에서 벗어나 자유롭게 사용할 수 있습니다.
즉, 타입 안전성이 보장되지 않습니다.

```js
let value: any = "Hello";
value = 42; // OK, no error
value.toFixed(2); // OK, but dangerous since "Hello" is not a number
```

any는 타입 검사를 무시하기 때문에 코드에서 런타임 에러를 발생시킬 수 있는 잘못된 타입 사용을 방지하지 못합니다.

<br />

#### unknown

any와 마찬가지로 모든 타입을 받을 수 있지만, unknown은 타입 안전성을 보장합니다.
unknown으로 정의된 값은 그 타입이 명확하게 확인되기 전까지는 그 값을 사용할 수 없습니다.
unknown은 타입 검사를 강제하여 any보다 안전하게 사용할 수 있습니다.

```js
let value: unknown = "Hello";
// value.toUpperCase();  // Error: Object is of type 'unknown'

if (typeof value === "string") {
  value.toUpperCase(); // OK
}
```

<br />
