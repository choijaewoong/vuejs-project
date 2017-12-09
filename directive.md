# Directive

### v-text
* 태그 문자열을 HTML 인코딩하여 나타내기 때문에 태그 문자열 그대로 표시 (`innerText`)

### v-html
* 태그 문자열을 파싱하여 화면에 나타냄 (`innerHTML`)
* `<script>`태그를 그대로 바인딩 하므로 XSS 공격등에 취약.

### v-bind
 * 요소 객체의 속성들을 바인딩
 * ':'로 축약 가능

    ```html
    <button :class="btn-primary">
    ```
* `:value="message"`, `:src="imagePath"` 등...

### v-model
* view 요소에서 변경한 값이 모델 객체에 반영되도록 양방향데이터 바인딩
* form 엘리먼트의 초기 value, checked, selected 속성을 무시
* [v-model 참고](https://kr.vuejs.org/v2/guide/forms.html)

### v-show
* 일단 html요소를 렌더링 후에 display속성으로 화면에 보여줄 지 결정
* 화면에 노출 여부가 자주 변경되는 경우 사용

### v-if, v-else, v-else-if
* 조건에 부합하지 않는 경우 html 렌더링 자체를 하지 않음

### v-for
* 반복 렌더링. 원본 데이터의 형식에 따라 사용법이 다름
* index 또한 전달 가능

```html
//items 배열인 경우
<li v-for="(item, index) in items">
    <a href="{{item.link}}">{{index + 1}}: {{item.name}}</a>
</li>
```

```html
//items 해시맵인 경우
<option v-for"(val, key) in items" v-bind:value="key">{{val}}</option>
```
* `v-if` 와 함께 사용하는 경우, `v-for`가 먼저 수행되고 `v-if`가 적용
* 여러 요소를 그룹지어 반복 렌더링 할경우 `<template>`태그 사용
   * ex ) `<template v-for="(contact, index) in contacts"> ... </template>`
* 배열 데이터 변경 주의
   * 인덱스를 이용해 직접 배열 데이터 변경시 추적 불가능 
        * ex ) `list.contacts[0] = {no:100, name: "다혜", adress:"제주"}` ==> 불가능
    * 배열값 내부 속성을 직접 변경하거나 Vue.set 메소드 사용
        * ex ) `list.contacts[1].name = "다혜";` ==> 가능
        * ex ) `Vue.set(list.contacts, 0, {no:100, name: "다혜", adress:"제주"})` ==> 가능
    * `push, pop, shift, unshift, splice, filter, contact, slice, reduce` 등과 같은 배열 메소드 사용 권장

### v-on
* 이벤트 처리 디렉티브
* '@'로 축약 가능

```html
<button @:click="balance += parseInt(amount)">예금</button>
```

### v-pre
* HTML 요소에 대한 컴파일을 수행하지 않고 문자열 그대로 출력

### v-once 
* HTML 요소를 단 한번만 렌더링 하도록 설정. 데이터를 변경하더라도 다시 렌더링을 수행하지 않음.

### v-cloak
* 템플릿 문자열이 일시적으로 나타나는 현상을 처리하는데 사용