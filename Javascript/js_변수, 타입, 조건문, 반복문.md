## Variable = 변수

* var 다음에 본인이 정한 단어를 사용해서 정의를 내리는 것

        var a = 10;
        var pi = 3.145948;
   
* var hello; // 변수만 선언했을 뿐 할당을 한 게 아니므로, undefined를 출력한다.
* ' = '는 같다가 아니라, 값을 변수 이름에 대입한다. 할당을 한다는 의미이다.

* 원시 타입 : var a = 3 , b = a , a = 0, b 는 무엇인가 ? // 3
* 값이 바뀌는 경우 : var a = [1, 2, 3]; a = b, a[0] = 0, b는 무엇인가? //[0, 2, 3]


## Data Type =  데이터 타입

* Number : 소수, 정수, 등 모든 숫자

* string : " "의 문자 기호의 조합으로 반드시 따옴표 조합을 묶어야 한다.

* boolean : 참 / 거짓을 변수에 담을 때 사용한다. (false / true)

* null : 값이 없음

    - data type
    
    - value of nothing
    
    - var x = null;

* undefined : 그 자체로도 타입으로. 정의되지 않은 어떠한 값

    - data type
    
    - absence of value
    
    - var x;
    
    - console,.log(x) //undefined 

* array : 배열 ([1, 2, 3])

## PASSING VARIABLES

* 자바스크립트에는 두가지 종류의 변수 타입이 있다.



#### 1. primitive value (원시값 - scalar value)

1. primitive type 의 메모리 상의 값을 그것의 실제 값이다.
(ex, boolean의 number의 경우 34)

2. 만약 a 변수의 값을 b에 할당하고, b의 값을 변경하면 a는 그대로이다.

3. primitive type은 고정된 크기의 메모리에 저장할 수 있다.

        - null
        - undefined
        - Boolean
        - Number
        - String
        
            ex)
            var a = 13;
            var b = a;
            b = 37;
            console.log(a); 
            //13

#### 2. reference value ( = complex type, container type)

1. 다른 값을 포함할 수 있다.

2. 고정된 크기의 메모리에 저장이 불가능해서, 메모리상에서의 reference type 값은 참ㅗ 그 자체로 메모리 주소를 갖고 있다.

        - Arry
        - Object
        - Function
        
            ex)
            var a = {
                c : 14;
            }
            var b = a;
            b.c = 37;
            console.log(a.c);
            // 37
            

## CONDITIONAL = 조건문

* 조건을 정하고 출력하는 것

* boolean은 찬과 거짓으로 나누어지는 조건문의 일종이다.

* 비교연산자
    
        > , < , = , <= , >=
        === 같다.
        !== 다르다.
    
* 비교연산자
    
        NOT = ! : truthy, falsy를 반전시켜 준다.
            falsy를 출력하는 값들 -> false, null, undefined, 0, NaN, ' ' , " "
        OR = || : 하나라도 성립하면 true, 하나도 성립하지 않으면 false를 반환한다.
        AND - && : 모두 다 조건을 만족해야 true를 반환한다.
    
* 조건문
    
        if(조건 1 이 참이면){
            조건 1 만족하면 실행 될 코드
            } else if(조건 2가 참이면){
            조건2 만족하면 실행 될 코드
            } else {
            모두 만족하지 않으면 실행 될 코드
            }
            
        ex)        
        
            var id = prompt('아이디를 입력해주세요');
    
            if(id == 'oh'){
                var password=prompt("비밀번호를 입력해주세요")
    
                if(password=="111111"){
                    alert("로그인 했습니다~" + id + "님 반갑습니다.")
    
                } else{
                    alert("비밀번호가 같지 않아요")
                }
    
            } else{
                alert('아이디가 일치하지 않아요~')
            }
            
* 논리 연산자

        if( <조건1> && <조건2> ){
            조건1 + 조건2 성립하면 실행 될 코드
            }
            
        ex)
        
            var id = prompt('아이디를 입력해주세요');
            var password = prompt("비밀번호를 입력해주세요");
        
            if (id == 'oh' && password == "111111") {
        
                alert("로그인 했습니다~" + id + "님 반갑습니다.")
        
            } else {
                
                alert('아이디가 일치하지 않아요~')
            }

            
## ITERATION = 반복문

* 비슷하거나, 같은 코드를 여러 번 실행해야 하는 상황에서 유용한 식

* for loop(반복문)

        for(초기화; 조건문; 증감식){
            조건이 만족했을때 나오는 식
            }

            
* for loop(반복문2 - object에서도 가능)

        for (var 변수 in 반복할 객체명){
            조건을 만족했을때 나오는 식
            }
            
            ex)
                var obj = {
                a : 10,
                b : 20,
                c : 30
                }
                console.log(obj.a + "," + obj.b + "," + obj.c);
                console.log(obj["a"] + "," + obj["b"] + "," + obj["c"]);
                for(var i in obj){
                console.log(obj[i]);
                }
* while

        - 조건식만 안으로 들어가고, 증감식과 초기화는 바깥으로 나가는 형태
        
            초기화
            while( 조건문 ){
            조건을 만족했을때 나오는 식
            }
            증감식
            
            
            

## 그 외 추가정보

* == : true / === : strict true

* ++a : 무조건 우선적으로 1을 먼저 더하고 출력한다(전위연산)

* a++ : a로 출력한 뒤, 출력이 끝나면 a+1을 한다. (후위연산)

* NaN 

    - Not A Number
    
    - 숫자 관련한 에러에서 리턴하는 값이다.
    
    - 수학 계산을 수행한 일부 코드를 작성하여 계산이 유효하지 못하면, NaN을 반환한다.
    
* "1" == 1 //true

* 0 == false //true

* even : 짝수

* odd : 홀수

* false를 반환하는 값들

    - boolean의 false
    
    - null : 값이 없다.
    
    - undefined : 값이 정의되지 않았다.
    
    - number 0
    
    - empty string ""
    
    - odd value NaN
    
* true를 반환하는 것들

    - boolean의 true
    
    - 42
    
    - "string"
    
    - "0"
    
    - "null"
    
    - "indefined"
    
    - {}
    
    - []
    
    - 1 (==)
    
#### 참고 

- 동등연산자의 관계 : https://dorey.github.io/JavaScript-Equality-Table/