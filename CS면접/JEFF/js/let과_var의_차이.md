# var

## function scope
함수 스코프를 갖는다. (var 를 통해,) 함수 내부에서 선언된 변수는 해당 함수 내부에서만 접근이 가능하다.

```tsx
function func(){
  var local = "local" 
  console.log(local) // ✅ 정상출력: local
}
console.log(local) // 🚨 ReferenceError: local is not defined
```

블록 스코프내에 선언될 경우, 해당 블록을 바깥 스코프에서도 접근이 가능하다.
```tsx
if(true){
  var global = "global"
  console.log(global) // ✅ 정상출력: global
}
console.log(global) // ✅ 정상출력: global
```

## 호이스팅
var 로 선언된 변수는 호이스팅(hoisting)되어 변수 선언이 코드의 최상단으로 끌어올려진다. 

하지만 초기화는 선언된 위치에서 이뤄지고, 그 전에 호출될 경우 undefined 값을 가진다.

```tsx
console.log(varHoisting) // ✅ 정상출력: undefined
var varHoisting = "var-hoisting"
console.log(varHoisting) // ✅ 정상출력: var-hoisting
```

<br/>
<br/>
<br/>

# let

## block scope
블록 스코프를 갖는다. (var 를 통해,) 함수를 포함하여 블록 내부에 선언된 변수는 해당 블록 내부에서만 접근이 가능하다.

```tsx
function func(){
  let local = "local" 
  console.log(local) // ✅ 정상출력: local
}
console.log(local) // 🚨 ReferenceError: local is not defined
```

블록 스코프내에 선언될 경우, 해당 블록을 바깥 스코프에서도 접근이 가능하다.
```tsx
function func(){
  let local = "local" 
  console.log(local) // ✅ 정상출력: local
}
console.log(local) // 🚨 ReferenceError: local is not defined
```

## 호이스팅
let도 호이스팅되지만, 선언과 초기화가 동시에 이루어지지 않는다. 
초기화 전에 변수에 접근하려고 하면 ReferenceError가 발생한다.

```tsx
console.log(letHoisting) // 🚨 ReferenceError: Cannot access 'letHoisting' before initialization

let letHoisting = "let-hoisting"
```