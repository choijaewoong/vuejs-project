# Options

### el
* Vue 인스턴스에 연결할 HTML DOM 요소를 지정

### data
* data 옵션에 주어진 모든 속성들은 Vue 인스턴스 내부에서 직접 이용되지 않고 Vue 인스턴스와 Data 옵션에 주어진 객체 사이에 프록시를 두어 처리

```javascript
var model = {
    name: "choijaewoong"
}
var vm = new Vue({
    el: '#test',
    data: model
})

// vm.name === model.name === vm.$data.name 
```

### computed
* `computed`라는 속성을 이용해 메소드를 등록해두면 해당 메소드를 속성처럼 이용 가능

### methods


