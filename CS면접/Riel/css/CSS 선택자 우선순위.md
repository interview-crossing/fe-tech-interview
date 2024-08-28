## 기준

1. 점수가 높은 선언이 우선함
2. 점수가 같으면, 가장 마지막에 해석된(나중에 작성된 ) 선인이 우선순위가 높다

# 1. 점수가 높은 CSS선택자

### CSS 선택자순위

1. important - 가장 높은 우선순위
2. Inline style 선언 - 1000점
3. ID 선택자 - 100점
4. Class - 10점
5. TAG - 1점
6. \*(전체)선택자 - 0점

```jsx
// 1. important
div {
	color: red !important;
}

// 2. Inline style 선언
<div>
	<p style="color: red;">Contents</p>
</div>

// 3. ID 선택자
#name {
	color: red;
}

// 4. Class
.name {
	color: red;
}

// 5. TAG
p {
	color: red;
}

// 6. *(전체)선택자
* {
	color: red;
}
```

## 계산 방식

- ex)

  ```jsx
  // class + tag + class = 21 점
  .name p.item{
  }

  //class + Tag = 11 점
  .name::p{
  }

  ```

  위와같이 점수는 합산되어서 체크 되고 점수가 높은 첫번째부분이 우선순위를 높게 가지게 된다

# 2 . 점수가 동일할시

- 가장 마지막에 작성된 선언의 우선순위가 높다

```jsx
.name {
	color : red
	}

.name {
	color : blue
	}
```

위 와같은 코드로 작성될 경우 2개다 class 만 사용했기때문에 name 의 색상은 blue 로 나오게 된다

pr 용커밋
