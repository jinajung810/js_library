# js_library
자바스크립트 연습

### toy project - dark mode
- button을 이용한 다크/라이트모드 on/off 실행
- bootstrap 사용 

### toy project - dark mode 적용 
- 문제: dark 모드 적용시 #container에서 darkMode 클래스를 toggle처리 했더니 position한 콘텐츠와 container사이 여백이 bg변경 안됨 
```javascript
    document.getElementById("toggleBtn").addEventListener('click', function(){
    document.querySelector(".container").classList.toggle('darkmode');
    })
```
- 해결: body에서 darkMode클래스를 토글처리함 

```javascript
    document.getElementById("toggleBtn").addEventListener('click', function(){
    document.querySelector("body").classList.toggle('darkmode');
    })
```
- 추가 과제: 
1. dark 모드 변경시, dark->light로 문자변경 & 색 반전 
2. jquery 에서 javascript로 rewrite 해보기 <br>
참고: https://stackoverflow.com/questions/69003055/how-to-rewrite-in-pure-javascript-code-from-jquery-code
### 시행착오
- javascript 라이브러리에서 다운받은 예시가 Jquery예시였음. 
(구별 잘하자 ㅠㅠ )
- 덤으로 jquery에서도 dark 모드 적용해봄 (아직은 jquery가 더 다루기 쉽다)