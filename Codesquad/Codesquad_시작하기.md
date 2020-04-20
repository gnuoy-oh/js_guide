## 레벨1 JS 시작하기

### 추천 진도 및 참고사항

- 참고하면 좋은 커리큘럼 

    * 추천 진도
    
    - 학습 진도 가이드
        - 아래 진도는 풀타임으로 학습이 가능한 경우의 진도입니다.
        - 직장인은 평일 저녁 및 주말을 이용해서 1/2 정도의 속도로 학습하시길 권장합니다.
    - 1주차
        - 개발 환경 구축
        - 자바스크립트 문법 1
        - 변수, 조건문, 반복문, 리스트
        - git / github 사용법 1
        - 간단 HTML 문법
        - 생활코딩 웹1 공부하기
        - 구구단 구현 1
    - 2주차
        - 자바 스크립트 문법 2
        - 배열, 함수, 객체
        - 구구단 구현하기 2
    - 3주차
        - 문자열 계산기 구현
        - GUI로 계산기 구현
    - 4주차
        - 문자 퍼즐 구현하기
        
    - 중간에 짬짬히 할 것들
        - 프로그래밍 관련 생각의 영상을 시청한다.
        - JS 학습하기의 자료들을 공부한다.
    - 마치고 나서
        - 영상이나 참고 자료 없이 구구단 / 계산기 / 문자 게임을 구현 가능한지 스스로 확인해 본다.
        - 온라인 레벨1 JS 파트2를 학습한다.
        - 코드스쿼드 레벨2를 고려해 본다.
         
    - 참고 사이트
        - 자바스크립트 기초
        - https://opentutorials.org/course/3083
        - https://developer.mozilla.org/ko/docs/Learn
        - https://www.w3schools.com/js/default.asp
    - mooc
        - https://programmers.co.kr/
        - https://www.codecademy.com/learn
        - https://teamtreehouse.com/
        - https://www.inflearn.com/
    - 알고리즘 공부하기
        - https://www.hackerrank.com/
        - https://www.acmicpc.net/
        - https://leetcode.com/
        - https://www.topcoder.com/
         
    - 추천 교재
        - 교과서
            누구나 쉽게 배우는 자바스크립트 http://www.yes24.com/24/Goods/20156001?Acode=101 트위터 개발자 닉 모건이 지은 책 쉽지만 생각보다는 어렵다. 김태곤 / 김미령 역 (프론트 개발자 및 번역가 부부)
        - 러닝 자바스크립트
            http://www.yes24.com/24/goods/42806896
        - 객체 지향 자바스크립트의 원리
            http://www.yes24.com/24/Goods/16886051?Acode=101
            
### 설치해야 할 것들 

- 운영 체제 : window / mac / Linux

- 에디터 (비쥬얼 스튜디)

- 웹 브라우저 : chrome

- git GUI : 소스트리

### 개발 환경 구축

- commit 할 때에는 반드시, 어떤 작업을 했는지 구체적으로 작성하여 commit > push 를 한다.

### 자바스크립트로 무엇을 할 수 있나?

1. HTML을 제어할 수 있다.

    - 기본적인 CSS 변경이 가능하다
    
    - 더 나아가서, 동적 이벤트 구현이 가능하다. (정적인 HTML 워드 문서를 다양한 동작을 시킬 수 있음)

## 자료형

#### 1.  자료형이란?

- 어떤 종류의 데이트를 사용하는 것인지 컴퓨터에게 알려주는 것

- 자료형마다 사용 가능한 연산자(Operator)를 따로 가지고 있다.

- 자료형이 같아야 연산을 할 수 있다.

#### 2. 자료형의 종류 

- Number

- String

- Boolean

- Null

- Undefined

- Object (객체)

#### 3. Number type

- 정수와 실수 모두 Number Type이다.

        - 5;
        - 3.0
        - -4.8;
        
- 숫자의 연산자

    - 4칙 연산, 괄호, 나머지 등이 있다.
    
            + - / * ( ) %
            
#### 4. 문자열

- 문자열에도 + 가 된다. (참고로 문자열음 Immutable의 특징을 가진다 - 값이 변하지 않으므로, 따로 변수 선언을 해서 바꿔준다.)
    - "I am String";
    
    - "Hello" + "World";
    
#### 5. typeof 연산자

- 데이터 유형을 알려주는 중요한 연산자

        - typeof 5;
        - typeof -4.8; 
        - typeof "5";
        
#### 6. Boolean 

- true;

- false;

- 5 > 3;

- 5 == 5;

- 5 === 5; 으로 하는게 맞다.
 
- 5 > 5;

#### 7. 논리 연산자

- 논리 연산자에는 &&, ||, ! 등이 있다.

        true;
        !true;
        true && true;
        true || false;
        
## 변수란?(Variables)

- 데이터(값)를 담을 수 있는 그릇

- 데이터들은 컴퓨터의 메모리의 어딘가에 저장되는데, 그 값들을 구별짓고 재사용하기 위해서 변수를 사용한다.

#### 1. 변수 정보

- 변수 선언

    - var a ;
    
        - 처음 선언하면 undefined가 뜬다c (정의되지 않았다 라는 )
    
    - let
    
    - const
    
- 변수와 대입 연산자

    - 변수에 값을 넣고 싶을 때 = 연산자를 사용한다
    
    - = 은 수학에서의 같다가 아니라, 변수에 값을 할당할 때 사용하는 대입 연산자이다.
    
    - 같다는 === 을 주로 사용한다 ***
    
- 변수 사용하기

    - 여러가지 방식이 있다.
    
            * 변수 선언과 할당을 동시에 주기 
            
            var a = 7;
            var b = 10;
            var x = a + b; // 17
            b = b + 1;

- 변수 이름 잘 짓기

    - 변수의 이름은 매우 중요하다. 일반적으로 소문자로 시작해서 영어, 숫자, _ 를 주로 사용한다. 
    
    - 카멜 케이스나 스네이크 케이스 표기법을 사용한다.
            
            helloWorld (Camel Case)
            
            hello_world (Snake Case)
    
## 연산자
        
#### 1. 증감 연산자

- C 언어에서부터 나온 연산자로, a++; 스타일만 사용한다.

- a++ === a = a + 1

- a-- === a = a - 1

        var a;
        a++;
        a = 0;
        a++;
        a--; 

- ++a; 값이 선언되기 전에 미리 +1을 계산한다.

#### 2. 비교 연산자

- 비교 연산자를 수행한 결과값은 Boolean이다. 비교 연산자에는 > , < , <=, ===, != 등이 있다.

        var a = 3;
        var b = 5;
        var x = "6";
        a > b;
        a < b;
        b === c;

## 기타 

#### 문자열의 길이 구하기

- 연산자는 객체의 속성을 가져올 때 사용하는 연산자.

        var a = "hello";
        
        a.length;
        
#### 문자열 간단히 조작하기

- 예시

        var a = "HeLLo";
        a[0];
        a[1] = "H"; //안됨
        a.slice(1,4);
        -- 대 / 소문자로 변경은 Immutable이므로 새로운 변수를 선언해야한다.
        a.toUpperCase();
        a.toLowerCase();
        
#### undefined, null, NaN

- undefined : 값이 정의되지 않았다.

- null : 값이 비어있다.

- NaN : 값이 아니다. ( === "계산 불가능" )

#### console.log();

- 개발자 콘솔에 뭔가를 찍어주는 메서드

        var a = 1;
        var b = "더하기";
        var c = 2;
        console.log(a + " " + b + " " + c + " = "+ a + c);
        
#### alert() 과 prompt() 사용해보기

- 예시

        var ans = prompt("How are you?");
        alert(ans)  
       
- 참고

    - var a =prompt("");의 값은 a; 를 했을 때 나온다.

    - 그런데, 숫자를 입력했을 때, 그 숫자는 자료형이 Number가 아니라 String 으로 "100" 과같이 출력됨으로, 숫자로 바꿔줘야 한다.

    - Number("200"); // 100 으로 Number로 바꿔준다
    
## 작업하면서 생긴 궁금점

### 1. innerHTML / innerText의 차이점

1. 태그가 들어있는 값 세팅의 경우 

- innerHTML : 태그가 반영되어 보여진다. 즉, 문자열을 html로 인식하여 리턴한다. 
      
- innerText : 태그가 반영되지않고 그대로 보여진다.

- 예시

        document.getElementById('testSpan1').innerHTML = "<b>테스트</b>";
        document.getElementById('testSpan1').innerText = "<b>테스트</b>";
        
        // innerHTML : 테스트
        // innerText : <b>테스트</b>

### 2. document.write 에서 tag 인식 

1. document 문서에 씌여질 텍스트를 포함하고 있는 스트링

    - tag를 인식한다!

            document.write("<h1>안녕하세요 오민영입니다.</h1> <br> 저는 마크업 개발자 입니다.") 
            라고 하면, 태그를 인식해서 h1의 css가 적용되고, 줄바꿈이 된다.

************************************************************************************************************************

## 조건문

#### 1. 기본 문법

- {}는 생략할 수 있지만 반드시 사용할것

- indent(들여쓰기)를 해야한다. (가독성)

        if(조건문){
            //조건문이 참일 경우 실행될 구문   
        }
        
#### 2. if else

- 문법

        if(조건식){
            //조건문이 참일 경우
        } else {
        
            //조건문이 참이 아닐 경우
        }

#### 3. if else if else

- 문법

        if(조건식){
            //조건문이 참일 경우
        }else if(조건식2)
            //조건식2가 참일 경우
        } else{
            //거짓일 경우
        }

## 반복문

- 비슷한 일을 반복적으로 처리하기 위한 명령문이다. 

#### 1. while

- 기본 문법

        while(조건){
            console.log("참일 때 실행됨");
        }
        
        var a = 1;
        while(a <== 100 ){
            console.log("Hi" + n);
            n++;
        }
        
#### 2. 자주 사용하는 패턴

- 문법

        var i = 0; //(1)
        while(i <=100 ){ (2)
            console.log(i)// (3)
            i++; (4)
        }
        
        
        * 1부터 100까지의 합 계산하는 방법
        function sumNum(){
            var sum = 0;
            var n = 1;
            while( n <= 100 ){
                sum = sum + n;
                n++;
            }
            document.write("1부터 100까지의 합은" + sum + "입니다.");
        }
        sumNum();
        
### 3. for

- 위의 while 코드와 똑같고, 훨씬 편리한 방법

        for(var i = 0; i <=100 ; i++){
            console.log(i);
        }
        
## 소수 판별 프로그램

- 1,3,5 등 쪼개지지 않는 수

        var isPrime = true;
        var n = Number(prompt("2 이상의 정수를 입력해주세요."));
        
        for(var i = 2; i < n ; i++){
            if(n % i === 0){
                isPrime = false;
                break
            }
            
            console.log(isPrime, i)
        }    
        
        if(isPrime){
            document.write(n + "은 소수입니다.");
        } else {
            document.write(n + "은 소수가 아닙니다.");
        }
           
        
## git / github 간단 사용법


- 소스 업로드 + 다른 사람들과 공유

    - add > commit > push
    
- 절차

    1. github 가입

    2. github 저장소 생성

    3. github 저장소 클론

    4. 내 컴퓨터의 내 문서 아래에 생성된 프로젝트 디렉토리에서 파일 생성 및 작업 완료

    5. 커밋할 파일들 선택해서 스테이지에 올리기 (add)

    6. 커밋하기 (commit)

    7. 푸시하기 (push)

    8. github.com/내아이디/내프로젝트 링크를 통해 정상적으로 업로드 되어 있는지 확인

- 강의 url : https://www.inflearn.com/course/javascript-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-codesquad-masters_lv1/lecture/10691
        
#### 도움받은 블로그

- https://www.inflearn.com/course/javascript-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-codesquad-masters_lv1/dashboard
