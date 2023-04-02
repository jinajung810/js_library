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
1. (main_javascript.html) dark 모드 변경시, dark->light로 문자변경 & 색 반전 
    ```css
    <style>
        .darkMode, 
        .darkMode div {background: #000;}
        .darkMode h2, 
        .darkMode h3, 
        .darkMode p, 
        .darkMode li {color:#fff;}
        .darkMode button {background: #fff; color:#000}
    </style>
    ```
    ```javascript
    <script>
        let toggle = document.getElementById("toggleBtn");
        let body = document.querySelector("body");

        toggle.addEventListener('click', function(){
            body.classList.toggle('darkMode');

            if (toggle.classList.contains('btn-outline-dark')){
            toggle.innerText = "Light" 
            } else {
            toggle.innerText = "Dark"
            }
        })
    </script>
    ```
    1. -> 코드 줄이기 
    ```javascript
    * if ~ else -> 삼항연산자로 변경
    toggle.classList.contains('btn-outline-dark') ? toggle.innerText = "Light" : toggle.innerText = "Dark";
    ```
    
    1. -> 문제
    - 처음 클릭했을 때 텍스트가 dark-> light로 변경된 후, <br> 다시 클릭하면 light->dark로 변경 안됨. 
    
2. jquery 에서 javascript로 rewrite 해보기 <br>
참고: https://stackoverflow.com/questions/69003055/how-to-rewrite-in-pure-javascript-code-from-jquery-code

    ### jQuery -> javascript 
     ```javascript
    * JQuery
        function darkMode() {
            let dark = $("#dark");

            if(dark.hasClass("btn-outline-dark")){
                $("body").css("background-color", "#333");
                $("body").css("color", "#fff");
                dark.text("Light");
                dark.removeClass('btn-outline-dark');
                dark.addClass('btn-outline-light');
            } else {
                $("body").css("background-color", "");
                $("body").css("color", "");
                dark.text("Dark");
                dark.removeClass('btn-outline-light');
                dark.addClass('btn-outline-dark');
            }
        }
     ``` 
    ```javascript
    * javascript
        function darkMode() {
            let dark = document.getElementById('dark')
            if (dark.classList.contains('btn-outline-dark')){
                document.querySelector("body").style.backgroundColor = "black";
                document.querySelector("body").style.color = "white";
                dark.innerText = "Light";
                dark.classList.remove("btn-outline-dark");
                dark.classList.add("btn-outline-light")
            } else {
                document.querySelector("body").style.backgroundColor = "";
                document.querySelector("body").style.color = "";
                dark.innerText = "Dark";
                dark.classList.remove("btn-outline-light");
                dark.classList.add("btn-outline-dark")
            }
        }
    ```
3. 코드 줄이기 
```javascript
    *변수 선언으로 코드 간소화
    function darkMode() {
        let dark = document.getElementById('dark');
        let body = document.querySelector("body");
                
        if (dark.classList.contains('btn-outline-dark')){
            body.style.backgroundColor = "black";
            body.style.color = "white";
            dark.innerText = "Light";
            dark.classList.remove("btn-outline-dark");
            dark.classList.add("btn-outline-light")
        } else {
            body.style.backgroundColor = "";
            body.style.color = "";
            dark.innerText = "Dark";
            dark.classList.remove("btn-outline-light");
            dark.classList.add("btn-outline-dark")
        }
    }
```
### 시행착오
- javascript 라이브러리에서 다운받은 예시가 Jquery예시였음. <br>-> 덤으로 jquery에서도 dark 모드 적용.

### 기억할 점 
- 클래스 2개를 지정해서 add하고 remove하는 방식으로 if문을 사용하는 것보다 css에서 배경색과 텍스트 색 등 클래스로 준 다음에 toggle을 사용하면 javascript를 간단하게 적용 가능.
- dark와 Light로 텍스트가 변경되게 하는 디자인인 경우, javascript에서 innerText를 사용했는데, CSS에서도 display: none등을 활용해서 가능할 것 같음.
