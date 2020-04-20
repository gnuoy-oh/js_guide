## 웹에 필요한 필수적인 자바스크립트를 바닐라 스크립트로 익혀보기

- js = 프로그래밍 언어 
  
- js 파일은 가장 마지막에 입력한다

    - 이유?
    
- console.log = print (파이썬)

- 변수 : 변경되거나 변경될 수 있는 것

    - 첫 사용은 const, 진짜 필요할 때만 let을 사용한다.

    - 변수는 변수의 시작에는 반드시 선언해주어야 한다.
    
    - let > Create > Initialize > Use (변수 사용 방법)
    
    - let ? 생성하고 초기화 할 상황에서만 let을 사용한다.
    
            let a = 221;
            let b = a - 10;
            a = 2;  --> 값을 바꿀 수 있다.
            console.log(b,a);
    
        - 값을 다른 값으로 바꿀 수 있다. 
    
    - const ? constatnt(상수) - 안정적, 변하지 않는 수     
    
            const a = 221;
            let b = a - 10;
            a = 2;  --> 상수는 재선언, 대입할 수 없다.
            console.log(b,a);
            
            > Assignment to constatnt variable
            > 상수 변수에 대입 (상수는 바뀔 수 없다.)
            
        - 변수가 바뀌면 안되는 상황에서는 const를 사용한다.
        
    - var ? 값을 바꿀 수 있다. 
    
        - var 는 사용하지 않고, 대신 let을 사용하는 것이 좋음
        
* 에러 내용을 이해할 수 있어야 함

        const monguCheez = {
            name : "oh",
            age : 23,
            gender : "female"
            // syntacError : Unexpected identifier 
            // (예상하지 못한 에러)
            // syntacError : Unexpected token
            likeWhat : ["캣닙","츄르","파티믹스"]
        }

        
- 변수에 넣을 수 있는 Data 종류 

    - 주석 : 일종의 메모를 남길 때 사용하는거
    
        - 한줄 // 여러줄 /**/   

    - String : "Nicolas" (텍스트)
    
    - Boolean : true / false
    
    - Number : 356
    
    - Float(floating number - 떠돌이 소숫점) : 55.1; 

- 다양한 데이터 타입 정렬하는 방법

    - Array
    
        - 데이터를 저장하는 곳, 리스트 같이 저장을 한다.
        
        - 다양한 데이터 타입을 포함시킬 수 있다.
        
        -   []
        
                const monday = "Mon";
                const tue = "tue";
                const wed = "wed";
                const thu = "thu";
                const fri = "fri";
                console.log(mon,tue,web,thu,fri);
                > 비효율적이므로, array 사용!
                
                const something = "Something"
                const daysOfWeek = ["mon","tue","web","thu","fri", true, "stuff", something]
                console.log(daysOfWeek)
                ["mon","tue","web","thu","fri", true, "stuff", something]
                
        - 규칙
        
                - 0 부터 카운트
                
                - daysOfWeek[0] > "mon"
        
    - Object
    
        - 데이터를 저장하는곳, 목적에 맞는 결과를 출력할 수 있음
        
        - 실제 객체를 만드는 것으로 label을 저장하고 싶은 data에게 줄 수 있다. 
        
                const ohInfo = {
                    name : "mintoung",
                    age:30,
                    gender : "female",
                    isHandsome:true 
                } 
                console.log(ohInfo);
                // ohInfo 의 name, age, gender, inHandsome 은 변수에 해당한다고 생각하면 되서 ""를 쓰지 않는다.
                
                console.log(ohInfo.gender); //Female
                
                ohInfo.gender = "Male";
                
                console.log(ohInfo.gender); //Male
                
                ohInfo = true; //  > Assignment to constatnt variable 으로 오류를 출력한다.
                
        - 규칙
        
            - oh.gender // female을 출력함
            
            - const 안에 있는 값은 바꿀 수 없다.
            
            - BUT, ohInfo 자체는 바꿀 수 없다 !!
            
    - Object를 Array 안에 넣을 수 있고, Array를 Object안에 넣을 수 있다.
    
            const favoriteSome = {
                movie : ["신과함께", "노트북" , "무드인디고","올드보이"],
                favFood:[
                    {
                        name:"kimChi",
                        fatty:false
                    },
                    {
                        name:"burger,
                        fatty:true
                    }
                    ]
            }
            
### 논리적인 코딩

- console.log(favoriteSome.favFodd)를 생각해보자

- favoriteSome가 Object인 것과 같이, console 도 Object 이다.

- 즉 .log 는 아래와 같이 해석할 수 있다. 

        console = {
        
            log : ????
        
        }
        
- 컴퓨터 소프트웨어 속에 console 이라는 object가 있고 log라는 key가 있다.

- 이 경우에 log는 functoin(함수)이다. 근데 Object 이다. 

- concole.log(console) 을 찍어보자.

- console 은 favoriteSome보다 더 큰 오브젝트이다.

- console.log, alert, prompt 등 많은 함수들은 내장함수(built-in function)

- 함수 ? 어떤것의 기능, 기능적인 부분, 한 코드 조각으로 원하는 만큼 쓸 수 있다 

    - 함수는 인자(아규먼트)를 받는다. 일종의 변수와 같다. 때문에, 함수를 만드는 시점에 인자를 변수명과 같이 넣어준다.

            - 함수 정의하는 문법
            
            function sayHello(){
                console.log('Hello');
            }   
            sayHello();
            
            //하단 ( ) 안에 들어가는 것을 인자(아규먼츠) - [값은 파라미터] 라고 한다.
            
            sayHello('Nicolas');
            console.log('Hi');
            
            function sayHello(potato,chiken){
                console.log('Hello',potato, 'i' , chiken, 'years of age');
            } 
            
            sayHello('Nicolas', 15);
            //"Hello" "Nicolas" "i" 15 "years of age"
            
- 함수 더 간결하게 작업하기 
        
        console.log('Hello',potato, 'i' , chiken, 'years of age');
        ->
        console.log('Hello '+ potato + ' i ' + chiken + ' years of age ');
        ->
        `(option + `)을 사용한 함수
        console.log(`Hello ${potato} i ${chiken} years of age`);

- console 과 return 의 차이에 대해

        const calculator = {
            plus : function(a,b){
                return a + b;
            } ,
            minus : function(a,b){
                return a-b;
            },
            multify : function(a,b){
                return a*b;
            },
            division : function(a,b){
                return a/b;
            }
        }

- html + javascript 를 사용하자

- 자바스크립트에서 element를 선택하기

    - console.log(document);
     
        // document를 대표하는 HTML을 보여준다
        // console.log 나 ohInfo.age 처럼 document도 많은 프로퍼티가 있다.

            document.getElmentById('')

- DOM (document object model)

    - 자바스크립트는 html 내의 모든 요소를 가져올 수 있다.
   
    - 즉, html object의 모든 key 를 가져올 수 있다.
    
    - HTML 페이지에서 자바스크립트로 선택한 것은 객체가 된다. 
    
    - HTML 을 DOM 객체로 바꿀 수 있다.
    
- console.dir(name)을 하면, 파라미터에 들어간 element 내의 모든 EVENT를 확인할 수 있고 변경할 수 있다~!!

        - const name = document.getElementById('helloTitle');
        
          (getElementById 외에 querySelector 등 선택할수 있는 방법 많음)
          
          name.innerHTML='바뀌었습니다!';

          name.style.color = red;
        
          document.title = 'I own you now';
        
        - 이렇게, dir로 확인하면서 자바스크립트로 HTML 을 변경할 수 있다. 

- 자바스크립트는 이벤트에 반응하기 위해서 만들어졌다,

- click, resize, input change ,submit, load, before closing 등등

- window 
        
        ex1) 
        
        function handleResize(){
            console.log('i have been resized');
        }
        window.addEventListner("resize",handleResize);
        
        //resize event가 발생하면 handleResize 함수를 호출한다.
        
        - handleResize() : 지금 바로 handleResize 함수를 호출하는 것
        
        - handleResize : 내가 필요한 시점헤 handleResize 함수를 호출하는 것 (함수를 바로 호출하지 않는다)
        
        ex2)
        function handleResize(event){
            console.log(event);
        }
        window.addEventListner("resize",handleResize(event));
        
        - 이벤트를 다룰 함수를 만들 때 마다 자바스크립트는 자동적으로 함수를 객체에 붙인다. (이해 못함)
        
        ex3)
        
        const title = querySelector('#title');
        
        function handleClick(){
                title.style.color=blue;
        }
        
        title.addEvenetListener('click', handleClick)
        
- if-else

- 조건식 

        if(condition){
        block
        } else{
        block
        }
        
- 피연산자
     
      - && / || / !==
    
- prompt('');

        const age = prompt('how old are you?');
        
        if(age > 19){
            console.log('you can drink');
        } else {
            console.log('you can't');
        }
    
- Click event 적용하기

        const title = document.querySelector('#title');
        
        const BASE_COLOR = "rgb(52,73,94)";
        const OTHER_COLOR = "#7f8c8d";
        
        function handleClick(){
            const currentColor = title.style.color;
            console.log(currentColor);
            if(currentColor === BASE_COLOR){
                title.style.color = OTHER_COLOR;
            } else { 
                title.style.color = BASE_COLOR;
            }
        }
        
        function init(){
            title.style.color = BASE_COLOR;
            title.addEventListener("click", handleClick);
        }
        init()
    
- mouseenter event 적용하기

        const title = document.querySelector('#title');
        
        const BASE_COLOR = "rgb(52,73,94)";
        const OTHER_COLOR = "#7f8c8d";
        
        function handleClick(){
            const currentColor = title.style.color;
            console.log(currentColor);
            if(currentColor === BASE_COLOR){
                title.style.color = OTHER_COLOR;
            } else { 
                title.style.color = BASE_COLOR;
            }
        }
        
        function init(){
            title.style.color = BASE_COLOR;
            title.addEventListener("mouseenter", handleClick);
        }
        init();
    
- 다양한 이벤트는 어디에 있을까

- HTML javascript DOM event MDN 을 검색하면 모든 발생하는 이벤트를 확인할 수 있다.

            ex1)
            
            function handleOffline(){
                console.log('bye bye');
            }
           
            function handleOnline(){
                console.log('welcome back');
            }
             
            window.addEvenetListener("offline",handleOffline); 
            // wifi 꺼졌을 경우 작동
            window.addEvenetLIstener("online",handleOnline);
            // wifi 졌을 경우 작동
        
- 위와 다르게 클래스를 추가해서 css를 변경하기! 

        ex1)
        const title = document.querySelector('#title');
        
        const CLICK_CLASS = "clicked";
        
        function handleClick(){
            const currentClass = title.className;
            if(currentClass !== CLICK_CLASS){
                title.className = CLICK_CLASS;
            } else {
                title.className = "";
            }
            
        function init(){
            title.addEventListener("click", handleClick);
        }
        
        init();            
        
        ------> 이렇게 작업하면, 기존에 title 에 존재할 class 가 사라지게 된다.
        
        ex2) 
        const title = document.querySelector('#title');
               
        const CLICK_CLASS = "clicked";
        
        function handleClick(){
            const hasClass = title.classList.contains(CLICK_CLASS);
            //classList.contains(??) -> ?? 를 포함하고 있는지 체크한다. 
            
            if(hasClass){
                title.classList.remove(CLICK_CLASS);
            } else {
                title.classList.add(CLICK_CLASS);
                // classList.add(??) -> ??를 추가해준다.
            }
            
        function init(){
            title.addEventListener("click", handleClick);
        }
        
        init();            
        
        ------> 훨씬 간결하게 작업하려면?
        
        ex3)₩
        
        const title = document.querySelector('#title');
               
        const CLICK_CLASS = "clicked";
        
        function handleClick(){
            title.classList.toggle(CLICKED_CLASS);
            }
            
        function init(){
            title.addEventListener("click", handleClick);
        }
        
        init();
            
                  



