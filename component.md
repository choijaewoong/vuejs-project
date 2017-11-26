# Component

* vue 뿐만 아니라 angular, react같은 프론트엔드 UI 프레임워크(라이브러리) 에서 가장 중요한 요소

### Vue Component
* 컴포넌트들은 속성(props)을 통해 자식 컴포넌트로 정보를 전달하며 주로 부모에서 자식으로 전달한다. 자식에서 부모로 데이터를 전달할 수 있지만 어플리케이션의 복잡도 증가 및 유지보수에 어려움이 있어 권장하지 않는다. 
* 자식 컴포넌트는 부모컴포넌트로 이벤트를 발신 할 수 있다.자식 컴포넌트네서 사용자 정의 이벤트를 발생시키면 부모 컴포넌트에서 이벤트 핸들러 메소드를 호출한다. 이러한 속성 전달, 이벤트 발신으로 자식-컴포넌트 간의 상호 작용을 만들 수 있다.

### Component 정의 방법
```javascript
// 간단한 template에 유용
<script type="text/javascript">
  Vue.component('hello-component', {
    template : '<div>hello world!!!</div>'
  })
</script>
```
```javascript
// 복잡한 template에 유용
<template id="helloTemplate">
    <div>hello world</div> 
</template>
<script type="text/javascript">
    Vue.component('hello-component', {
        template: '#helloTemplate'
    })
</script>
```
```javascript
//x-template 방식
<script type="text/x-template" id="helloTemplate">
    <div>hello world!!!</div>
</script>
<script type="text/javascript">
    Vue.component('hello-component', {
        template: '#helloTemplate'
    })
</script>
```

### 주의 사항
* HTML요소 중 자식 요소로 포함시킬 수 있는 요소들이 정해져 있는 경우, 구문분석을 실행한다. 이러한 요소 안에 Vue Component를 사용하는 경우,  
브라우저가 구문 분석 단계에서 DOM요소가 올바르지 않다고 판단하기 때문에 Vue Componet를 정상적으로 렌더링 하지 못하는 문제가 발생 할 수 있다.
이러한 경우 자식 요소로 포함시킬 수 있는 요소를 작성하고 is특성을 이용하여 처리하거나 `<script type="text/x-template">`태그 안에서  사용하면 된다.
    * [예제 06~07_option_component](06_component/06~07_option_component.html)
    * [예제 08_option_component](06_component/08_option_component.html)

* 컴포넌트 내부에서 data를 사용할 경우 함수를 사용하여야 한다. 함수를 호출하여 객체를 사용하는 경우, 호출될 때마다 새로 만들어진 객체를 리턴하기 때문에 각 컴포넌트들은 서로 다른 객체를 참조하게 된다. 
    * [예제 09_component_data](06_component/09_component_data.html)

### props
* props옵션을 통해 전달할 props를 배열로 나열한다. props사용 시 주의할 점은 속성명을 부여할 때 `카멜 표기법`을 사용했다면 태그에서 그 속성명을 작성할 때는 `케밥 표기법`을 사용해야 한다. 
    * [예제 10_props](06_component/10_props.html)
* props 속성에 대해 유효성 검사가 필요한 경우(타입 정의) 객체 형태를 사용하여 정의할 수 있다. 하지만 리터럴로 속성을 전달하는 경우 type처리 없이 문자열 그대로 전달된다. 이 문제를 해결하기 위해서는 `v-bind`를 사용하여 처리한다. 또한 배열이나 객체 props의 default값을 지정하는 경우 함수를 사용해야 한다.
    * [예제 11_props](06_component/12_props.html)

### event
* props가 부모에서 자식으로 정보를 전달하는 방법이라면, event는 자식에서 부모로 정보를 전달하는 방법이다. 


### eventBus
* 부모-자식 관계가 아닌 서로 형제 관계인 경우 이벤트 버스 객체를 이용해 정보를 전달한다. 