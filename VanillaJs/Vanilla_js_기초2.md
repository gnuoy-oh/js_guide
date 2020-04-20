## ECMA6 ES6

### 1. let / const 
1. var 의 특징

    1.  함수 레벨 스코프 (function level scope)

        - 함수 내에서 선언된 변수는 함수 내에서만 유효하며 함수 외부에서는 참조할 수 없다. 즉, 함수 내부에서 선언한 변수는 지역 변수이며 함수 외부에서 선언한 변수는 모두 전역 변수이다.
    
        - 함수의 코드블록만을 스코프로 인정한다. 따라서 전역함수 외부에서 생성한 변수는 모두 전역변수이다. 

        - for 문의 변수 선언문에서 선언안 변수를 for 문의 코드 블록 위부에서 참조할 수 있다.

                var foo = 123; // 전역 변수

                console.log(foo); // 123

                {
                var foo = 456; // 전역 변수
                }

                console.log(foo); // 456

    2. var 키워드 생략 허용 
    
       - 암묵적 전역변수를 양산할 가능성이 크다.

    3. 변수 중복 선언 허용

        - 의도하지 않은 변수값의 변경이 일어날 가능성이 크다.

    4. 변수 호이스팅

        - 변수를 선언하기 이전에 참조할 수 있다.


2. let (block level scope)

    1. 블록 레벨 스코프

        - 모든 코드 블록 (함수, if문, for문, while문, try/catch문 등)내에서 선언된 변수는 코드 블록 내에서만 유효하며, 코드 블록 외부에서는 참조할 수 없다.

        - 즉, 코드 블록 내부에서 선언한 변수는 지역변수이다.
        
                let foo = 123; // 전역 변수

                {
                let foo = 456; // 지역 변수
                let bar = 456; // 지역 변수
                }

                console.log(foo); // 123
                console.log(bar); // ReferenceError: bar is not defined

    2. 변수 중복 선언 금지

        - let 키워드로는, 동일한 이름을 갖는 변수를 중복해서 선언할 수 없다. 변수를 중복 선언하면 문법에러 (systex error)가 발생한다.

                let bar = 123;
                let bar = 456;  // Uncaught SyntaxError: Identifier 'bar' has already been declared

    3. 호이스팅
    
        ** let 키워드로 선언된 변수를, 선언문 이전에 참조하면 참조 에러 (reference error)가 발생한다. 

        ** 이는 let 키워드로 선언된 변수는 스코프의 시작에서 변수의 선언까지 일시적 사각지대(TDZ)에 빠지기 때문이다

        - 자바스크립트는 ES6에서 도입된 let, const를 포함하여 모든 선언(var, let, const, function, function*, class)을 호이스팅한다. 
        
        - 호이스팅(Hoisting)이란, var 선언문이나 function 선언문 등을 해당 스코프의 선두로 옮긴 것처럼 동작하는 특성을 말한다.

              console.log(foo); // undefined
              var foo;

              console.log(bar); // Error: Uncaught ReferenceError: bar is not defined
              let bar;

        - 변수의 생성되는 3단계

            1. 선언 단계(Declaration phase)
            - 변수를 실행 컨텍스트의 변수 객체(Variable Object)에 등록한다. 이 변수 객체는 스코프가 참조하는 대상이 된다.

            2. 초기화 단계(Initialization phase)
            - 변수 객체(Variable Object)에 등록된 변수를 위한 공간을 메모리에 확보한다. 이 단계에서 변수는 undefined로 초기화된다.

            3. 할당 단계(Assignment phase)
            - undefined로 초기화된 변수에 실제 값을 할당한다.

        - let 키워드로 선언된 변수는 선언 단계와 초기화 단계가 분리되어 진행된다. 즉, 스코프에 변수를 등록(선언)하지만, 초기화 단계는 변수 선언문에 도달했을 때 이루어진다. 초기화 이전에 변수에 접근하려고 하면 참조 에러(reference error)가 발생한다. 이는 변수가 아직 초기화되지 않았기 때문이다. 다시 말하면 변수를 위한 메모리 공간이 아직 확보되지 않았기 때문이다. 따라서 스코프의 시작 지점부터 초기화 지점까지는 변수를 참조할 수 없다. 스코프의 시작 지점부터 초기화 시작 지점까지의 구간을 '일시적 사각지대(temporal dead zone : tdz)라고 한다.

            // 스코프의 선두에서 선언 단계가 실행된다.
            // 아직 변수가 초기화(메모리 공간 확보와 undefined로 초기화)되지 않았다.
            // 따라서 변수 선언문 이전에 변수를 참조할 수 없다.

              console.log(foo); // ReferenceError: foo is not defined

              let foo; // 변수 선언문에서 초기화 단계가 실행된다.
              console.log(foo); // undefined

              foo = 1; // 할당문에서 할당 단계가 실행된다.
              console.log(foo); // 1

        - var 키워드로 선언된 변수는 선언 단계와 초기화 단계가 한번에 이루어진다. 즉, 스코프에 변수를 등록(선언)하고 메모리에 변수를 위한 공간을 확보한 후, undefined로 초기화(초기화) 한다. 따라서, 변수 선언문 이전에 변수에 접근하여도 스코프 변수가 존재하기 때문에 에러가 발생하지 않고 undefined를 반환한다. 이후 변수 할당 단계에 도달하면 비로소 값이 할당된다. 이러한 현상을 변수 호이스팅이라고 한다.

              // 스코프의 선두에서 선언 단계와 초기화 단계가 실행된다.
              // 따라서 변수 선언문 이전에 변수를 참조할 수 있다.
              console.log(foo); // undefined

              var foo;
              console.log(foo); // undefined

              foo = 1; // 할당문에서 할당 단계가 실행된다.
              console.log(foo); // 1
    4. 클로저

      - 블록 레벨 스코프를 지원하는 let은 var 보다 직관적이다.      

    5. 전역객체와 let

      - 전역객체는 모든 객체의 유일한 최상위 객체를 의미한다.

      - browser-side 에서는 window 객체, server-side(Node.js)에서는 global 객체를 의미한다.

      - var 키워드로 선언된 변수를 전역변수로 사용하면 전역 객체의 프로퍼티가 된다. 

            var foo = 123; // 전역변수

            console.log(window.foo); // 123

      - let 키워드로 선언된 변수를 전역 변수로 사용하는 경우, let 전역변수는 전역객체의 프로퍼티가 아니다. 즉, window.foo와 같이 접근할 수 없다. let 전역변수는 보이지 않는 개념적인 블록 내에 존재하게 된다.

          let foo = 123; //전역변수

          console.log(foo); // undefined

3. const (block level scope)

  - 상수(변하지 않는 값)을 위해 사용한다. 

  1. 선언과 초기화

    - const는 재할당이 금지된다.

    - 선언과 동시에 할당을 해야만 한다.

        - const FOO = 123;

          FOO = 345; // type error : Assignment to constant variable.

        - const FOO; // SyntaxError: Missing initializer in const declaration

  2. 블록 레벨 스코프를 가진다.

        {

          const FOO = 10;
          console.log(FOO); //10

        }
        console.log(FOO); //Reference Error : FOO is not defined 

  3. 상수

    - 가독성과 유지보수의 편의를 위해 적극적으로 사용해야만 한다.

        if(rows > 10){
          // 위의 10의 의미를 알기 어렵기 때문에, 변수 선언을 해주는 것이 좋다.
        }

        var MAX_ROWS = 10;
        if(rows > MAX_ROWS){

        }

    4. const 와 객체

      - const는 재할당이 금지된다.

      - 재할당은 불가는 하지만, 객체의 내용(프로퍼티의 추가, 삭제, 프로퍼티 값의 변경)은 변경이 가능하다.

          const user = {
            name : 'Lee';
          }
          //const 변수는 재할당이 금지된다.
          // user = {} // Type error : Assignment to constant variable.

          // 객체의 내용은 변경할 수 있다.
          user.name = 'Kim';

          console.log(user); // {name : 'Kim'} 

- 참고 : https://gist.github.com/LeoHeo/7c2a2a6dbcf80becaaa1e61e90091e5d

### 2. Template Literals

1. ' / " 대신 백틱 (`)을 사용한다.

  1. `템플릿 리터럴은 작은 따옴표(')와, 큰 따옴표(")를 혼용할 수 있다.

  2. 일반적인 문자열에서 줄바꿈은 허용되지 않고, 공백을(white-space)을 표현하기 위해서는 백슬래시(\)로 시작하는 이스케이프 시퀀스를 사용해야 한다. 

  3. + 연산자를 사용하지 않아도, 간단한 방법을 새로운 문자열을 삽일할 수 있는 기능을 제공한다.

    - 이를 문자열 인터폴레이션 이라고 한다.

        const first = "Ung-mo";
        const last = "Lee";

        //EC5
        console.log("My name is" + first + " " + last + ".");

        //ES6
        console.log(`My name is ${first} ${last}.`)

### 3. 화살표 함수

1. 화살표 함수의 선언

  - 모든 경우 화살표 함수를 사용할 수 있는 것은 아니다.

        // 매개변수 지정 방법
          () => {...} // 매개변수가 없는 경우
          x => {...} // 매개변수가 한 개인 경우, 소괄호 생략 가능
          (x,y) => {...} // 매개변수가 두 개인 경우, 소괄호 생략 불가능

        // 함수 몸체 지정 방법
          x => { return x * x } // string line block
          x => x*x // 함수 몸체가 한줄의 구문이라면 중괄호를 생략할 수 있으며 암묵적으로 return된다. 위 표현과 동일하다.

        () => {return {a:1};}
        () => ({a : 1 }) // 위 표현과 동일하다. 객체 반환시 소괄호를 사용한다.

        () => {    // multi line block.
          const x = 10;
          return x * x
        }

2. 화살표 함수의 호출

  - 화살표 함수는 익명 함수로만 사용할 수 있다.

  - 따라서 함수를 호출하기 위해선, 함수 표현식을 사용한다.

        // ES5
        var pow = function(x){ return x * x};
        console.log(pow(10)) // 100

        // ES6
        const pow = x => x * x;
        consloe.log(pow(10)) //100

        //콜백함수
        // ES5
        var arr = [1, 2, 3];
        var pow = arr.map(function (x) { // x는 요소값
          return x * x;
        });

        console.log(pow); // [ 1, 4, 9 ]

        //ES6
        const arr = [1,2,3];
        const pow = arr.map(x => x * x);

        console.log(pow); //[1,4,9]
3. this

1. 일반 함수의 this

-  자바스크립트의 경우 함수 호출 방식에 의해 this에 바인딩할 어떤 객체가 동적으로 결정된다. 다시 말해, 함수를 선언할 때 this에 바인딩할 객체가 정적으로 결정되는 것이 아니고, 함수를 호출할 때 함수가 어떻게 호출되었는지에 따라 this에 바인딩할 객체가 동적으로 결정된다.

- 콜백 함수 내부의 this는 전역 객체 window를 가리킨다.

2. 화살표 함수의 this

- 화살표 함수는 함수를 선언할 때 this에 바인딩할 객체가 정적으로 결정된다. 동적으로 결정되는 일반 함수와는 달리 화살표 함수의 this 언제나 상위 스코프의 this를 가리킨다. 이를 Lexical this라 한다. 화살표 함수는 앞서 살펴본 Solution 3의 Syntactic sugar이다.

- 화살표 함수의 this 바인딩 객체 결정 방식은 함수의 상위 스코프를 결정하는 방식인 렉시컬 스코프와 유사하다.

      function Prefixer(prefix){
        this.prefix = prefix;
      }

      Prefixer.prototype.prefixArray = function(arr){
        return arr.map(x => `${this.prefix} ${x}`);
      };

      const pre = new Pewfixer('hi');
      console.log(pre.PrefixArray['Lee','Kim']);

        (2) ["Hi  Lee", "Hi  Kim"]
        0: "Hi  Lee"
        1: "Hi  Kim"
        length: 2
        __proto__: Array(0)

3. 화살표 함수를 사용해서는 안되는 경우

  1. 메소드

    - 화살표 함수로 메소드를 정의하는 것은 피해야 한다.   

        // Bad
        const person = {
          name: 'Lee',
          sayHi: () => console.log(`Hi ${this.name}`)
        };

        person.sayHi(); // Hi undefined             

        //Good
        const person={
          name : 'Lee';
          satyHi(){ // === sayHi: function() {
            console.log(`Hi ${this.name}`);
          }
        }             
        person.sayHi(); // Hi Lee                                        

  2. prototype

    - 화살표 함수로 정의된 메소드를 prototype에 할당하는 경우도 동일한 문제가 발생한다. 따라서 prototype에 메소드를 할당하는 경우, 일반 함수를 할당한다.
    
        //Bad
        const person = {
          name : "Lee",

        }
        Object.prototype.sayHi = () => console.log(`Hi ${this.name}`);
        person.sayHi(); // Hi undefined

        //Good 
        const person = {
          name : 'Lee',
        }

        Object.prototype.sayHi = function(){
          console.log(`Hi ${this.name}`);
        }

        person.sayHi(); /Hi Lee

  3. 생성자 함수

    - 화살표 함수는 생성자 함수로 사용할 수 없다. 생성자 함수는 prototype 프로퍼티를 가지며 prototype 프로퍼티가 가리키는 프로토타입 객체의 constructor를 사용한다. 하지만 화살표 함수는 prototype 프로퍼티를 가지고 있지 않다.

        const Foo = () => {};

        // 화살표 함수는 prototype 프로퍼티가 없다.
        console.log(Foo.hasOwnProperty('prototype')); //false

        const Foo = new Foo(); // TypeError: Foo is not a constructor

  4. addEventListener 함수의 콜백함수

    - addEventListener 함수의 콜백 함수를 화살표 함수로 정의하면 this가 상위 컨택스트인 전역 객체 window를 가리킨다.

    - 따라서 addEventListener 함수의 콜백 함수 내에서 this를 사용하는 경우, function 키워드로 정의한 일반 함수를 사용하여야 한다. 일반 함수로 정의된 addEventListener 함수의 콜백 함수 내부의 this는 이벤트 리스너에 바인딩된 요소(currentTarget)를 가리킨다.

        //Bad 
        var button = document.getElementById("myButton");

        button.addEventListener('click', () => {
          console.log(this === window); //true
          this.innerHTML = 'clicked button';
        })

        //Good
        var button = document.getElementById("myButton");

        button.addEventListener('click', function(){
          console.log(this === button); //true
          this.innerHTML = 'clicked button';
        })
4. 파라미터 기본값 , spread 문법 , rest/spread 프로퍼티

  1. 파라미터 기본 값

    - 파라미터에 기본값을 설정하여 함수 내에서 수행하던 파라미터 체크 및 초기화를 간소화할 수 있다.

        function plus (x = 0, y = 0){
          // 파라미터 x,y에 인수를 할당하지 않은 경우, 기본 값을 0 을 할당한다.
          return x + y;

        }
### 4. module이란
- 애플리케이션을 구성하는 개별적 요소로서 재사용 가능한 코드 조각을 말한다. 모듈은 세부 사항을 캡슐화하고 공개가 필요한 API만을 외부에 노출한다.
- 일반적으로 모듈은 파일 단위로 분리되어 있으며 애플리케이션은 필요에 따라 명시적으로 모듈을 로드하여 재사용한다.
- 쉽게 말하면, 모듈을 프로그램의 일부분으로, 프로그램은 하나 이상의 모듈의 조합으로 구성된다. 모듈은 하나 또는 그 이상의 Routine(함수, 메서드, 프로시져 등)으로 구성된다.
- 모듈은 프로그램을 구성하는 부품과 같고, 라이브러리와 비교했을 때, 라이브러리는 코드를 완성하기 위한 외부 자원(모듈)이라고 생각하면 된다.
	- 예) 자동차
	- 바퀴, 핸들 등 부품(모듈)
	- 네비게이션 시스템, 차량용 스피커 등은 외부 자원(라이브러리)
- 참고) 코드를 여러개의 파일로 분리해서 얻을 수 있는 효과!

		1. 자주 사용되는 코드를 별도의 파일로 만들어서 필요할 때마다 재활용할 수 있다.
		2. 코드를 개선하면 이를 사용하고 있는 모든 애플리케이션의 동작이 개선된다.
		3. 코드 수정 시에 필요한 로직을 빠르게 찾을 수 있다.
		4. 필요한 로직만을 로드해서 메모리의 낭비를 줄일 수 있다.
		5. 한번 다운로드된 모듈은 웹브라우저에 의해서 저장되기 때문에 동일한 로직을 로드 할 때 시간과 네트워크 트래픽을 절약 할 수 있다. (브라우저에서만 해당)

	1. 내용
	- ES6에서는 정식으로 module 시스템이 도입 되었는데, import / export 이다.
	- import
		- export 예약어를 사용해 내보낸 것을 사용할 수 있다.
	- default
		- export한 변수/상수/함수 등을 import하는 곳에서 어떠한 이름으로든 사용할 수 있게 해준다.

### 참고
- [MDN-Classes](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Classes)
- [Poiema-es6-class](https://poiemaweb.com/es6-class)
- [Poiema-module](https://poiemaweb.com/es6-module)
- [생활코딩-module](https://www.opentutorials.org/module/532/4750)
- [Module System](https://velog.io/@doondoony/JavaScript-Module-System)

### 5. 함수형 프로그래밍

  1. 프로그래밍 패러다임
    
    - 명령형 프로그래밍: 프로그래밍의 상태와 상태를 변경시키는 구문의 관점에서 연산을 설명하는 방식
      - 알로리즘을 명시하고 목표는 명시 안함
      - 절차지향 프로그래밍: 수행되어야 할 연속적인 계산 과정을 포함하는 방식 (C, C++)
      - 객체지향 프로그래밍: 객체들의 집합으로 프로그램의 상호작용을 표현 (C++, Java, C#)

    - 선언형 프로그래밍: 어떤 방법으로 해야하는지를 나타내기보다 무엇과 같은지를 설명하는 방식
      - 알고리즘 명시하지 않고 목표만 명시
      - 함수형 프로그래밍: 순수 함수를 조합하고 소프트웨어를 만드는 방식(클로저, 하스켈, 리스프)
```
// 명령형
functon double(arr){
  let result = []
  for(let i = 0; i < arr.length; i++){
    result.push(arr[i]*2)
  }
  return result
}

function add(arr){
  let result = 0;
  for(let i = 0; i < arr.length; i++){
    result += arr[i]
  }
  return result
}

$("#btn").click(function(){
  $(this).toggleClass("highlights")
  $(this).text() === 'Add Highlights'
  ? $(this).text('Remove Highlight')
  : $(this).text('Add Highlight')
})
//선언형
function double(arr) {
  return arr.map((item) => item * 2)
}

function add(arr) {
  return arr.reduce((prev, current) => prev + current, 0)
}

<Btn
  onToggleHighlight = {this.handleToggleHighlight}
  highlight = {this.state.highlight}>
    {this.state.buttonText}
</Btn>

```
### 명령형 프로그래밍은 어떻게 할 것인가(How)를 표현하고, 선언형 프로그래밍은 무엇을 할 것인가(What)를 표현한다.

  2. 함수형 프로그래밍이 필요한 이유

    - 새로운 계산 방법을 배우는 것처럼 사고의 전환을 필요로 한다. 다양한 사고방식으로 프로그래밍을 바라보면 더욱 유연한 문제해결이 가능해진다.

    - 함수형 프로그래밍은 계산을 수학적 함수의 조합으로 생각하는 방식을 말한다. 이것은 일반적인 프로그래밍 언어에서 함수가 특정 동작을 수행하는 역할을 담당하는 것과 반대되는 개념으로, 함수를 수행해도 함수 외부의 값이 변경될 수 없다.

    - 순수한 함수를 작성하고, 공유된 상태와 변경 가능한 데이터 및 부작용을 피하여 소프트웨어를 작성하는 프로세스이다.

    - 명령형이 선언형이며, 

### 참고
- [velog](https://velog.io/@kyusung/%ED%95%A8%EC%88%98%ED%98%95-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%EC%9A%94%EC%95%BD)
- [korbit](https://medium.com/korbit-engineering/%ED%95%A8%EC%88%98%ED%98%95-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D%EC%9D%B4%EB%9E%80-e7f7b052411f)
- [nesoyBlog](https://nesoy.github.io/articles/2018-05/Functional-Programming)









    




        
