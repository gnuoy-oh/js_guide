
## Naming = 이름

* 변수의 이름

    - 한단어로 표현하는 것이 가장 좋다.
    - 구조적인 부분 보다는 변수가 존재하는 목적을 고려해서 이름을 짓는다.
    - 비슷한 값들을 갖는 변수는 복수 명사가 좋다.
    - var animals = [ a, b, c ];

* Boolean의 이름
    
    - 전형적인 형식을 가진다.
    - 참, 거짓 이므로 변수의 이름 앞에 is/are를 붙이는 것이 좋다.
    - var isEqual = true;
    
* 함수의 이름 

    - 동사로 시작한다. 그러면 변수 이름 의미가 자명해지고, 빠르게 훑어보는 사람들이 함수의 입력 값과 출력 값, 둘 사이의 변환 과정을 파악하기가 쉬워진다.
    - var countWaterBlock = function () { }
    
* 변수 이름에서의 대문자

    - 변수가 포함한 class를 지시하기 위해, 변수 이름의 첫 글자를 대문자로 쓴다.
    - new 키워드를 사용한 함수에 한해서 대문자를 쓰기도 한다.
    - 상수(constant - 정해진값) 즉, 프로그램 전체에서 일정한 값을 가지는 변수의 이름을 정할때는 그 변수의 이름은 전체를 대문자로 쓴다.
    - function Animal (){}
    - const MAX_ITEMS_IN_QUEUE = 100;
    
* 연산자와 키워드

    - 반드시 === 와 !==를 사용한다.
    - x ? y : z --> x 가 참이면 y를, 거짓이면 z를 실행한다.
        - 아주 짧고 명확한 코드를 쓸 때, 3항 연산자를 사용한다.
    
* 짧게쓰기

    - 분명하고 실행되는 한, 되도록 짧게 쓴다.
       
        good – function square(n){ return n*n };
        
        bad – function square(n) { var squaren = n*n; return squareN; }
        
    - 되도록 부정을 사용하지 않는다.
    - Boolean 결과 값을 바로 리턴한다.
    
* 코드 문장과 구문 사이 공간

    - 줄바꿈을 최소로 사용한다. 한 화면에서 더 많은 코드를 볼 수 있기 때문에..
    - 들여쓰기는 처음과 끝을 똑같이 사용한다.
    - 콤마 (,) 사이에 띄어쓰는 것이 좋다.
    - 연산자 사이에 띄어쓰기
     
  

## Method = 메소드

* 일종의 명령어


### STRING METHOD - 유사배열

** 모든 string 메소드는 원본이 변하지 않는다!!!!!!!!!!!!

    var str = "code"; 
    str = str.toUpperCase(); 로 변수에 담아줘야 한다.

* str[index] --> 스트링 번호 값을 출력한다.

        var str = 'codestates';
        console.log(str[0]); 
        // c
        
        ** string은 str[0] = "h" 와 같이, 값을 바꿀 수 없다. 
* length --> 문자열의 길이를 한다.

* indexOf("h") --> 찾고자하는 문자열을 반환한다.
        
    - 처음 일치하는 index 번호를 반환하고, 없으면 -1을 출력한다.

* lastIndexOf("0") --> 문자열 뒤에서부터 찾는다.
        
* includes("d") --> 찾고있는 문자열을 포함하고 있는지 확인한다.
        
* split(" ") --> 따옴표 안을 기준으로 스트링을 분리(argument)하고, 배열로 리턴(value)한다.
        
    - csv(comma seperated value) 형식을 처리할 때 유용한 메소드이다.

* substring(1,4) --> 문자열을 부분부분 잘라주는 메소드 
        
    - 시작과 끝 index 사이의 문자열을 자른다.
    - slice(start, end) 메소드와 비슷함
    
* toLowerCase() --> 소문자로 변환 / toUpperCase() --> 대문자로 변환 
        
    - argument는 없다.
    
    

### NUMBER METHOD

* Number.isInteger(value) -> value가 정수인지 아닌지 검사한다.

    - true / false 를 반환한다.

* Number("12.567") // 12.567 --> 스트링을 숫자로 바꿔준다.

* parseInt("12.345") // 12 --> 문자열을 분석하고 특정 진수를 사용한 정수로 변환해 반환한다.

    - parseInt("hello") // NaN
    - parseInt("-19") // -19
    
* toFixed([digits]); --> 소수점 뒤에 나타날 자릿수 (optional, 기본값 : 0), 숫자를 나타내는 문자열을 반환한다.

        var number = 1234.5678;
        number.toFixed(); // 1234
        number.toFixed(1); // 1234.5
        number.toFixed(6); // 1234.567800
        
* Math.x([value1, [value2, [value3....]]]); --> argument : 숫자 몇 개든 상관 없음
    
    - argument : 없음
    
    - 최솟값 : Math.min();
        console.log(Math.min(2,3,4)); // 2
    
    - 최댓값 : Math.max();
        console.log(Math.max(4,6,2)); // 6
    
    - Math.floor(x) / Math.round(x)
        - argument : 숫자, 주어진 숫자의 내림/반올림 값
        - console.log(Math.floor(45.67)) // 45
        - console.log(Math.round(20.5)) // 21
    
    - Math.random();
        - 0과 1 사이의 난수를 반환한다.
        - argument : 없음
        - 특정 범위의 랜덤한 정수를 리턴할 때 사용한다.
       
            Math.random * 10 
            
        - Math.round(100*Math.random()) --> 10~100 사이의 정수가 나온다.
    
    - Math.pow(3,2) // 제곱근. 3의 2 제곱 // 9
    
    - Math.ceil(10.3) // 올림

### ARRAY METHOD

* property
    - length : 배열의 길이를 반환한다.

* CALLBACK 함수
    
        - argument로 넘겨주는 함수(A)
        - 이 함수 A를 paramter로 받는 함수 B가 callback함수 A를 즉시 실행할지, 나중에 실행할지 결정할 수 있다.
        ex)
        function system(callback){
            callback();
        }
        function foo(){
        console.log("실행 가능한 콜백함수")
        }
        system(foo);
        
* Array.isArray(obj);
    
    - 검사할 객체가 배열이면 true, 아니면 false를 반환하는 메소드
    - argument : 검사할 객체
    - return value : true / false (boolean으로 반환)
    
* arr.forEach(callback 함수) - IMMUTABLE

        ex)
        function printArray(currentElement, currentIndex, array){
            console.log(index + " : " + currentElement);
        }
        ['hello' , 3, 5].forEach(printArray);
        // 0 : hello
        // 1 : 3
        // 2 : 5
                
    - 배열을 반복하고, 배열의 각 요소를 인라인 함수 표현식을 사용하여 조작하는 다른 방법을 제공한다. 
    - element마다 함수를 반복 실행한다.
    - argument : element 길이만큼 반복하는 함수
    - parameter : 순서대로 (현재 element, 현재 index, 배열 그 자체 - 항상 고정되어 있음)
    - return value : 없음 (immutable로 기존의 배열 값이 바뀌지 않는다)
    
* arr.map(callback 함수) - IMMUTABLE

        ex) [1, 3, 5].map(function (currentElement, currentIndex, array){
            return currentElement * 2;
            }
            // [2, 6, 10]
            
    - foreach 함수를 사용하면 원래 배열을 영구적으로 수정하기 어려우나, map 함수는 기존의 배열에서 새 배열을 만드는 것이 간단하다.    
    - 기존 배열과 동일한 길이를 갖고, 형태가 다른 새로운 배열을 만들 때 유용하다.
    - argument : element 길이만큼 반복하는 함수
    - parameter : 순서대로 (현재 element, 현재 index, 배열 그 자체)
    - return value : callback이 실행되면서 return하는 값들을 새로운 배열로 반환한다.
    - callback 내에서 리턴이 필요하다.

* arr.filter(callback 함수) - IMMUTABLE

        ex)
        [1,3,5].filter(function(currentElement, currentIndex, array){
            return currentElement > 1;
            }
            //[3, 5]
           
    - 기존 배열에서 조건에 따라 특정 element를 걸러낼 때 유용하다.
    - argument : element의 길이만큼 반복하는 함수
    - parameter : 순서대로 (현재 element, 현재 index, 배열 그 자체)
    - return value : 조건을 통과한 element를 담은 새로운 배열을 반환한다.
    - callback 내에서 boolean형태의 return이 필요하다.
    
* arr.shift();

    - 맨 앞의 요소를 삭제한다.
  
* arr.unshift('hello');

    - 맨 앞에 요소를 추가한다.
     
* arr.push(newElement) - MUTABLE

        ex)
        ['code', 'states'].push('course');
        // ['code', 'states', 'course'];
        
    - 배열의 마지막에 요소를 추가한다.
    - argument : 추가할 element (복수 가능)
    - return value : 추가된 array의 값
    
* arr.pop() - MUTABLE

    - 배열의 마지막 요소를 제거한다.
    - return value : 제거된 element를 반환한다.
    
* arr.slice([begin, [end]]); - IMMUTABLE

        ex)
        var animals = ['ant', 'camel', 'bison', 'elephant', 'duck'];
        console.log(animals.slice(2));
        // ['bison', 'elephant', 'duck]
        console.log(animals.slice(2,4));
        //['bison', 'elephant']
        
    - index의 범위만큼 element를 추출한다.
    - argument : 처음 index, 마지막 index
    - return value : 자른 새로운 배열 객체를 반환한다.
    - 배열을 복사할 때 유용하다.
    
* arr.splice(start, deleteCunt[item1, [item2, [item3 ...]]]) - MUTABLE

       ex)
       var myFish = [‘angle’ , ‘clown’ , ‘mandarin’ , ‘sturgeon’];
       myFish.aplice(2,0,'drum'); 'drum'을 두번째 인덱스에 삽입한다.
       // [‘angle’ , ‘clown’ ,'drum', ‘mandarin’ , ‘sturgeon’]
       
   - 배열의 내용을 추가 + 삭제 할 때 사용한다.
   - argument 
    
        처음 index
        
        (삭제시) 삭제할 element의 갯수
        
        (추가시) 배열에 추가 할 element(복수 가능)
        
   - return value : 새로운 배열을 반환한다.
   - 삭제와 추가를 동시에 하지 않는다.
   
* arr.reduce(callback 함수, [innitial value]) - IMMUTABLE

        ex)
        [10,1,2,3,4].reduce(function(accumulator, currentValue, currentIndex, array){
            return accumulator + currentValue ;
        }
        //10 + 1 + 2 + 3 + 4 = 20을 반환
        
    - 모든 element의 계산을 누적해 하나의 결과를 리턴할 때 유용하다.
    - argument : element의 길이만큼 반복하는 함수값, 초깃값
    - parameter : 순서대로 (누적값 accumulator, 현재값 currentValue, 현재 index, array)
    - return value : 최종 누적값
    - 초깃값은, 첫번째 accumulator 값을 지정해서 함수를 시적하는 것이다.

* arr.join([seperator = ","]) - IMMUTABLE

        ex)
        var a = [1,2,3];
        var myVar = a.join(",");
        console.log(myVar);
        // 1, 2, 3
        
    - return value : 연결자로 element를 연결한 결과의 문자열
    - argument : 연결자
    
* arr.indexOf(searchElment) - IMMUTABLE

        ex)
        ['hello',5,'hi'].indexOf('hi');
        // 2
        
    - element 존재여부를 파악할 때 유용하다.
    - argument : 배열에서 찾을 element
    - return value : 배열 내의 요소의 최초 인덱스, 발견되지 않으면 -1
            
* arr.concat() - IMMUTABLE

        ex)
        var arr = [1,'hi',3];
        var arr2 = [3,5,2];
        console.log(arr.concat(arr2);
        //[1, 'hi', 3, 3, 5, 2];
    
    - 주어진 배열이나 값을 기존 배열에 합쳐서 새 배열을 반환한다.
    
* arr.sort([compareFunction]); = MUTABLE

        ex)
        var arr = [1,40,25,5];
        arr.sort(); 
        // [1,25,40,5];
        
    - 정렬 순서를 정의하는 함수로, 생략하면 배열은 각 요소의 문자열 변환에 따라 각 문자의 유니코드 포인트 값에 따라 정렬된다.

