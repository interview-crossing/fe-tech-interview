# Attribute
- HTML의 속성

```html
<!-- div 엘리먼트의 id와 class 속성은 어트리뷰트 이다 -->
<div id="inpa" class="bold"></div>

<!-- input 엘리먼트의 type과 value 속성은 어트리뷰트 이다 -->
<input type="text" value="0">
```

# Property
- DOM의 속성
  - DOM은 HTML을 자바스크립트 객체(Object)로 표현한 문서 모델

```html
<div class='my-class' style="color: red;"></div>

<script>
    // className 은 property 이다.
    document.querySelector('div').className;

    // style 은 property 이다.
    document.querySelector('div').style.color;
</script>

```


# 차이점

> **1️⃣ attribute 는 정적으로 변하지 않고, property 는 동적으로 변할 수 있다.**
> - javascript 를 통해 property 값이 변경되어도, html 문서는 바뀐 것이 없다.

> **2️⃣ attribute 는 아무 속성이나 추가해도 상관없다. / property 는 인식할 수 없다.**
>  - html 상에서 어떤 태그든 임의로 넣은 attribute 는 `getAttribute()` 로 확인할 수 있다.
>  - property 는 지정된 속성(=property) 값만 인식할 수 있다.
> ```ts
>    <input type="text" value="0" custom="9999"/>
>
>    <script>
>
>       const input = document.querySelector('input');
>
>       console.log(input.getAttribute('custom')); // ✅ attribute 출력: 9999
>
>       console.log(input.custom);  // ✅ property 출력: undefined             
>    </script>
> ```


> **3️⃣ property로 속성값을 조회하는 편이 조금 더 빠르다.**