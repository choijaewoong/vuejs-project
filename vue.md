# Vue

### MVVM
* Model - 데이터 객체
```javascript
var model = {
    message: "..."
};
```
* View - UI 
```html
<div id="simple">
    <h2>{{message}}</h2>
</div>
```
* ViewModel - 뷰를 위한 모델, 상태와 연산을 처리
```javascript
var simple = new Vue( {
    ...
});
```