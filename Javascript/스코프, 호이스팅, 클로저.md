## SCOPE = 스코프

#### scope 
    
* 변수는 어떤 환경 내에서만 사용이 가능하며, 프로그래밍 언어는 각각의 변수 접근 규칙을 갖고 있다.

* scope는 변수과 그 값이 어디서부터 어디까지가 유효한지 판단하는 범위이다.
즉, scope는 변수 접근 규칙에 따른 유효범위를 의미한다.

* 함수가 선언되는(lexical) 동시에 자신만의 scope를 가진다.

    1. scope는 중첩이 가능하다.
    
    2. 하위 scope가 상위 scope의 변수에 접근이 가능하다.
    
    3. global scope는 어디에도 접근이 가능하다.
    
    4. 지역변수는 함수 내에서 전역변수보다 높은 우선순위이다. 

* 자바스크립트는 기본적으로 function level의 scoping 규칙을 따른다.
    
* 함수 선언은 선언만 될 뿐, 정의되지 않은 것이다.

    var a = function (){
    
    }
    
    1. var a;
    2. a = function (){}

* if / for문은 function이 아니라서 scope를 생성하지 않는다.

* function level을 따르지 않는 변수 선언

        1. let 과 const는 block을 벗어나면, 접근이 불가능하다.
        
        2. let 과 const는 var 정의된 변수를 재정의 할 수 없다.
        
        3. const는 불변하는 값으로, 다시 값을 할당할 수 없다.
        
        4. let
        
        5. const 
        
* 예시

        var greeting = 'Hello';
        function greetSomeone() {
          var firstName = 'Josh';
          return greeting + ' ' + firstName;
        }
        
        greetSomeone(); // 'hello Josh'
        firstName; // => // Reference Error



#### GLOBAL SCOPE (전역 변수)


* 가장 함수 외부에 선언된 모든 변수이다. 
          
* window : 전역변수에 해당하는 모든 변수들은 window에 속해있다.

        var global = "global";
        
        window.global
         
        // global 을 출력한다. 

* 키워드 없이 변수를 선언하면 전부 다 전역 범위가 되면서, 버그가 심해진다.

    - 즉, var / let / const를 사용해서 변수를 선언해야 한다.
    
            function showAge(){
             
               //age는 전역변수
            
               age = 90;
            
               console.log(age);
           
           }
               showAge();
               // 90
               console,.log(age);
               //90
           
#### LOCAL SCOPE(지역 변수)


* 함수 내에서 선언된 변수로, 함수 내에서는 전역변수보다 높은 우선순위를 가진다. 

* 예시01

        var name = "Richard";
        
        function showName() {
          var name = "Jack"; // 지역 변수
          // showName 함수 안에서만 접근 가능
          console.log(name); // ??
        }
        
        console.log(name); // Richard
        showName();  //Jack
        console.log(name); // Richard
        
* 예시02

        var name = "Richard";
        // 아래의 if문은 name변수에 대한
        // local scope를 생성하지 않는다.
        if (name) {
          name = "Jack";
          console.log(name); // Jack
        }
        // if문에서 변경된 name은 여전히 전역 변수
        console.log(name); // Jack
        
* 예시03

        for(var i=0; i<5; i++) {
          console.log(i); // 다섯번 iteration
        }
        console.log('final i:', i); 
        
        // 0
        // 1
        // 2
        // 3
        // 4
        // 5
        // final i : 5
        
        
* 예시04

        for(let i=0; i<5; i++) {
          console.log(i); // 다섯번 iteration
        }
        console.log('final i:', i); // ReferenceError
        
        //0
        //1
        //2
        //3
        //4
        //5
       
#### SCOPE CHAIN (스코프 체인)

* 내부에서 찾는다 -> 없음 -> 전역 스코프까지 넓혀가면서 찾는다. 
    
        var value = "global";
        
        function ourFunc(){
        
            console.log(value);
            
            //이때의 value는 local에 없으니, 전역의 global을 찾아간다.
            
            function innserFunc(){
            
                console.log(value);
                
                //이때도 마찬가지로 global의 value를 찾아간다.
                
                var innerValue = 'local'
                
                //지역변수 선언
                
            }
            
            innerFunc();
        
        }
        
        outerFunc();
        
        console.log(innerValue); // innerValue if not defined (외부에서 내부를 바라볼 수 없다)
        


## HOISTING = 호이스팅
    
* 변수 선언은 범위에 따라 선언과 할당으로 분리된다.

        var a = 2;
       
        1. var a; (선언)
        
        2. a = 2; (할당)
      

* 자바스크립트 엔진이 내부적으로 변수 선언을 scope의 상단으로 끌어올린다.

* 함수 선언식은 항상 상단으로 호이스팅 된다.

        function hello(){
        
            return "hello";
              
        }  
        
        와 같은 함수 선언식 자체는 상단으로 호이스팅 됨
        

* 함수 표현식은 선언된 변수만 상단으로 호이스팅 된다.

        var hello = functon(){
        
            return "hello"l
            
        }
        
        와 같이 var hello; 만 상단으로 호이스팅 됨

* 에러의 형태

        Reference Error
        
        - 보통 undefined된 변수에 접근할 때 발생하는 에러
        
        Type Error 
        
        - 보통 함수가 아닌 것을 실행하려 할 때 발생하는 에러  
        
* 예시01

        var a;
        console.log(a); // undefined
        a = 2;
        
* 예시02 

        show();
        
        function show() {
          console.log('displayed!');
        }
        
        //displayed!
        
* 예시03

        show(); // ?
        
        var show = function() {
          console.log('displayed!');
        }
        
        //Type error
        
        
## CLOSURE = 클로저
    
* 외부함수의 변수에 접근할 수 있는 내부함수

* scope chain이라고 하기도 한다.

* 보통 함수를 return하여 사용한다.

* return하는 내부함수를 closure 함수라고 지칭한다.

        function outer(){
            var outerVar = 'outer variable';
            function inner(){
                var innerVar = 'inner variable';
                console.log(outerVar + innerVar);
                
                //외부 함수의 변수(outerVar)를 내부 함수, 즉 closure가 사용할 수 있다.
            }
        }
       
* closure가 가지는 세가지 scope chain

        1. closure 자신에 대한 접근 (closure function 내에 정의된 변수)
        
        2. 외부 함수의 변수에 대한 접근
        
        3. 전역 변수에 대한 접근

* 자바스크립트 엔진이 내부적으로 변수 선언을 scope의 상단으로 끌어올린다.

* 쓰이는 예

     1. curring (function programming)
        
    - 함수 하나가 n개의 인자를 받는 대신, n개의 함수를 만들어 각각 인자를 받게하는 방법
        
            function add(x, y){
                return x + y;
            }
            
            add(2,3);
            
            function adder(x){
                return function (y){
                    return x + y;
                }
            }
            
            adder(2)(3);
                
     2. closure가 저장된 paremeter를 사용하므로, template 함수를 만들고자 할 때 유용하다.
     
            function elementMaker(tagName){
                var startTag = '<' + tagName + '>';
                var endTag = '</' + tagName + '>';
                
                return function(content){
                    return startTag + content + endTag;
                }
            }
            elementMaker('div')('hello world');
            // <div> hello world </div>
            
            var divMaker = elementMaker('div');
            divMaker('code states');
            // <div> code states </div>
            divMaker('great');
            // <div> great </div>
            
     3. closure module pattern
     
    - simple counter : 변수를 scope 안쪽에 감추어, 함수 밖으로 노출시키지 않을 수 있다.
             
             function makeCounter(){
                var privateCounter = 0;
                
                function changeBy(val){
                    privateCounter += val;
                }
                
                return {
                    increment : function (){
                        changeBy(1);
                    };
                    decrement : function(){
                        changeBy(-1);
                    };
                    getValue : function(){
                        return privateCounter;
                    }
                

            
                        
           
                  
                   
