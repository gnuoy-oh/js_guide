## Asynchronous Call (비동기 출력)

- 자바스크립트의 비동기 처리란, 특정 코드의 연산이 끝날 때까지 코드의 실행을 멈추지 않고, 다음 코드를 먼저 실행하는
    자바스크립트의 특성을 의미한다.

### A. CALLBACK  
    
* 다른 코드의 argument(인수)로서 넘겨주는 함수를 말한다.

* 콜백을 parameter로 넘겨받는 코드는 이 콜백을 필요에 따라 즉시 실행할수도, 나중에 실행할수도 있다.

        function executableCode(){
        
        }
        
        function otherCode(callback){
        
            callback(); 
            
            //it can be executed
             
        }
        
        otherCode(executableCode);


### B. CALLBACK in ACTION

* iterator(반복자)

        [1,2,3].map(function(element, index){
        
            return element * element;
            
        })  
        
        //(3) [1, 4, 9]
        
* event handler

        document.querySelector('#btn').addEventListner('click', function(e){
        
            console.log('button clicked');
        
        }
        
* Event

    - event가 발생하고 handler가 실행될 때, 두 가지 이상의 일이 동시에 진행됨을 확인할 수 있으나
    
        사실 자바스크립트는 single thread 기반의 언어이다.

### C. 타이머 관련 API

* setTimeout( callback, milisecond)

     - 코드를 바로 실행하지 않고, 지정한 시간만큼 기다렸다가 로직을 실행한다.
     
     - argument : 실행할 callback함수, callback 함수 실행 전에 기다려야 할 시간(밀리 초)
     
     - return value : 임의의 타이머 ID
     
            #1
            
            console.log("hello");
            
            #2
            
            setTimeout(function(){
            
                console.log("3초 후 실행");
                
            },3000);
            
            #3
            
            console.log("hello again");
            
            //"hello"출력
            
            //"hello again" 출력
            
            //3초 후에 "3초후 실행" 출력
            
* setInterval(callback, milisecond)

    - 일정 시간의 간격을 가지고, 함수를 반복적으로 실행한다.
    
    - arguments: 실행할 callback함수, 반복적으로 함수를 실행시키기 위한 시간 간격(밀리 초)
    
    - return value : 임의의 타이머 ID
    
            setInterval(function(){
            
                 console.log('1초마다 실행');
                 
             } , 1000 );
             
             //1초마다 반복 실행된다.
             
             
* clearInterval(timerId)

    - 반복 실행중인 타이머를 종료한다.
    
    - arguments : 타이머 ID
    
    - return value : 없음
    
            var timer = setInterval(function(){
            
                console.log('1초마다 실행');
                
            } , 1000 );
            
            clearInterval(timer);
            
            //더 이상 반복 실행되지 않음
            
### D. 비동기 출력의 케이스
    
* EVENT HANDLER

* 타이머에서의 callback

    1. animation
    
* 서버에 자원을 요청할 때 

### E. 제이쿼리의 ajax 통신

* 표시할 이미지나 데이터를 서버에서 불러와 표시해야하는데, ajax 통신으로 해당 데이터를 서버로부터 가져올 수 있다.

            function getDate (){
                let tableData;
                $.get('https://domain.com/products/1',function(res){
                    tabelData = res;
                });
                return tableData;
            }
            console.lot(getDate()); // undefined

## Recursion (재귀)

- 원래의 자리로 되돌아가거나 되돌아온다는 뜻으로, 자기 자신을 부르는 함수이다.

- 자기 스스로를 호출하는 function

    - function foo(){
    
        foo();
        
       }
       
       foo 
       
       // foo
          
- 즉, 어떠한 함수가 있을 때 그 안에서 자기 자신을 호출하는 함수이다.
  
### A. 재귀를 사용하지 않고 직관적으로 프로그래밍을 하는 것 (iterative way) - 반복문

* case 01
    
        var factorial = function(number){
        
            var result = 1; 
            
            for(var i = number; i > 0; i--){
            
                result *= i ;
                
            }
            
        return result;
        
        }
       
### B. 재귀를 사용하여 프로그래밍을 하는법(recursion function)
       
* case 02   
    
        factorial - n! == n(n-1)(n-2)(n-3)......;
        
            var factorial = function(number){
            
                if(number === 0 ){
                
                    return 1;
                
                }
                
                return (number * factorial(number-1);
                
        }
        
### C. 재귀함수의 가장 기본적인 케이스
    
* case 03
   
        function factorial(n){
        
        //base case
        
        //when n is equal to 0, we stop the recursion
            
            if(n == 0 ){
            
                return 1;
                
            }
        
        //recursion case
        
        //it will run for all other conditions except when n is equal to 0
        
            return ( n * (factorial(n-1) ) ;
        
        }
            
    
        
        
### D. 재귀함수의 기본적인 형태  
    
* case 04

    var function_name = function(inpiut){
    
        //예외처리를 반드시 한다. to provent infinite recurtion
        
        if(termination_condition == 예외처리할 값, 음수나 예상 못하는 값){
        
            return value;
            
        }
        
        else if (base_case){
        
            return value;
            
        } 
        
        //recursion case
        
            return (expression_with_recursion_call)
            
        }
        
### E. 다른 다양한 케이스

* 피보나치 number

    - 1,1,2,3,4,8,13,21,34,55,89.144 (앞과 현재 숫자를 더한 값)

    - recursion
    
        function fibonacci(number){
        
            //base case
            
            if(number === 0){
            
                return 0;
                
            } else if (number === 1){
            
                return 1;
                
            }
            
            //recursion case
            
            return fibonacci(number-1) + fibonacci(number-2);
            
            }
            
            var result = fibonacci(10);
            
            console.log(result);
            
* 반복문 (iterator)

        function fibonacci(number){
        
            var a = 1 ,
            
                b = 0,
                
                temp;
                
            while(number > 0){
            
                temp = a;
                
                a = a + b;
                
                b = temp;
                
                num--;
                
            }
            
            
            return b;
            
        }
        
        var result = fibonacci(10);
        
        console.log(result);
        
* tree 구조
                
    1. Node를 찾을 때
    
    2. stirngfy JSON
    
            {
            
             'key' : {
             
                'key 1-1' : {
                
                    'key 1-1-1' : 'value1-1-1';
                    
                    'key 1-1-2' : 'value1-1-2';
                    
                    }
                    
                }
                
            }
     
    3. getElementByClassName                         
             
             
    
     
