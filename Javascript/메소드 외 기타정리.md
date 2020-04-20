## JS

### 문자를 자르는 함수들 (slice, splice, split, subString, substr)

- slice(시작 index, 종료 index)

    - 기존 배열은 변하지 않고, 잘려진 배열을 반환 

    - 배열, string 가능

- splice(시작 index, 삭제 갯수, 추가할 문자)

    - 문자를 갯수만큼 삭제한 후 추가할 수 있다. 

    - 기존 배열은 변하지 않고, 잘려진 배열을 반환한다.

- split(정규식|구분문자, 제한)

    - 구분 문자를 기준으로 잘라서 배열을 만든 후 배열을 반환한다.

    - 기존 string은 유지된다.

- subString(시작index, 종료 index)

    - 시작 index부터 종료 index 전까지 잘라서 반환한다.

    - 기존 string은 유지된다.

- substr(시작index, 길이)

    - 시작 index 부터 길이를 잘라서 반환한다. 
    
    - 기존 string은 유지된다.

### 요일 구하기

- getDay()

    - 해당 요일을 얻을 수 있고, 0 일요일 ~ 6 토요일

                function getDayName(a,b){
                    let arrWeek = ['SUN','MON','TUE','WED','THU','FRI','SAT'];
                    let pullDate = new DATE(`2016-${a}-${b}`);
                    let pullWeek = pullDate.getDay();
                    return arr[pullWeek];
                }

### forEach, filter, map, reduce, every, some

- forEach - IMMUTABLE (기존 배열 유지)

    - 배열을 반복하고, 배열의 각 요소를 인라인 함수 표현식을 사용하며, 다른 방법을 제공한다.

                function printArr(currentElement, currentIndex, array){
                    console.log(currentIndex + ":" + currentElement)
                }
                ['hello', 3, 6].forEacth(printArr);

                // 0 : hello
                // 1 : 3
                // 2 : 6

- map - IMMUTABLE (기존 배열 유지)

    - forEach 함수를 사용하면, 원래의 배열을 영구적으로 수정하기 어렵지만, map 함수는 기존 함수 배열에서 새 배열을 만드는 것이 간단하다.

    - 기존 배열과 동일한 길이를 갖고, 형태가 다른 새로운 배열을 만들 때 유용하다.

                [1,3,5].map(function(currentElement,currentIndex,array){
                    return currentElement * 2;
                })
                //[2,6,10]

- filter - IMMUTABLE (기존 배열 유지)

    - 기존 배열에서 조건에 따라 특정 element를 걸러내서 새로운 배열을 생성

                [1,3,5].filter(function(currentElement,currenIndex,array){
                    return currentElement > 1;
                })
                // [3,5]

- reduce - IMMUTABLE (기존 배열 유지)

    - 모든 element의 계산을 누적해서 하나의 결과를 리턴한다.

                [1,3,6].reduce(function(accumulator, currentValue, currentIndex, array){
                    return accumulator + currentValue;
                })
                // 1+ 3 + 6 = 10을 반환

- every, some 

    - 배열을 순회하면서 특정 조건을 배열의 값들이 만족시키는지 검사하는 메서드.

    - 호출한 배열이 결론적으로 만족 시키는지 (true), 만족시키지 않는지(false) 알려준다.

    - every : 배열의 모든 값이 조건을 만족해야 true 를 return

    - some : 배열의 일부 값만 만족해도 true를 return

                let isAllOdd = [1,2,3,4,5].every(val => {
                    return val % 2 != 0
                })
                console.log(isAllOdd); // false

                let isSomeOdd = [1,2,3,4,5].some(val => {
                    return val != 0
                })
                console.log(isSomeOdd) // true
    
    - 예제

                function solution(s){
                    let splitsS = s.split(" ");

                    return splitS.map((a) => {
                        return a.split('').map((currentValue, currentIndex) => {
                            return (currentIndex%2===0) ? currentValue.toUpperCase() :  currentValue.toLowerCase()
                        }).join("");
                    }).join(" ");
                }

### object(객체)

- object 요소 추가 , 삭제

    - 삭제 : delete obj[key]

    - 추가 : obj[key2] = 211; 


- object의 키 return 하기

    - object.keys(변수명);

- key / value 값 얻어내기 (=foreach)

      for(var key in 변수명){
         console.log(key + "=> " + object[key]);
      }

- object의 갯수 알아내기

    - var length = Object.keys(변수명).length;

### 소소한 정보와 헷갈리는 것들

- default - 컴퓨터에서 변경하지 않으면 기본으로 하도록 되어 있는 방식 

- addEveneListener - 이벤트를 등록하는 가장 좋은 방식

- setTimeOut("code" , delay ) 1000->1초

- PC에서 모바일 페이지 기준 사이즈로 오픈했을 때, 모바일 마크업 경로로 이동 시키는 경우

      - 상단에서 META 태그 입력 후      
          
      <script type="text/javascript">
         if(screen.wirdt <= 699){
            document.location= "mobile.html";
         }
      </scripe>

- 배열의 마지막 값 구하기!
 
      var arr=[0,1,2,3,4,5];
      arr.slice(-1);
      
      //5

## 숫자인지 아닌지 판별하고 싶다.

### isNaN(testValue)

- 어떤 값이 NaN 인지 판별한다.
- testValue(매개변수) - 테스트되는 값
- 반환 값 - if 주어진 값이 NaN 이면 true를, 그렇지 않은 경우 false를 반환한다.

        예제
        isNaN(NaN); // true
        isNaN(undefined) // true
        isNaN({}) // true
        
        isNaN(true(1)); //false
        isNaN(null(0)); // false
        isNaN(36); // false
        
        isNaN("436"); // false "436"은 NaN이 아닌, 숫자로 변환된다.

### Number.isNaN(value)

- value(매개변수) - NaN인지 판별할 값
- 반환 값 - 유형이 Number이고, 값이 NaN이면 true, 아니면 false
- 주어진 값이 NaN인지 판별하는데, 전역 isNaN()함수의 더 엄격한 버전.

        function typeOfNan(x){
            if(Number.isNaN(x)){
                return 'Number NaN';
            } 
            if(isNaN(x)){
                return 'NaN'
            }
        }
        console.log(typeOfNaN('100F'));
        // expected output: "NaN"
        
        console.log(typeOfNaN(NaN));
        // expected output: "Number NaN"

NaN? (Not a Number) 
전역 객체의 속성으로, 숫자가 아님 을 나타낸다.  https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/NaN

## 리터럴?

- 모든 데이터에 들어가는 데이터 값 그 자체 

- https://mohwaproject.tistory.com/entry/Javascript-Literal%EC%9D%B4%EB%9E%80


# this

- 자바스크립트의 함수는 호출될 때, 매개변수로 전달되는 인자값 이외에, arguments 객체와 this를 암묵적으로 전달 받는다.

- 함수를 호출할 때 함수가 어떻게 호출되었는지에 따라 this에 바인딩할 객체가 동적으로 결정된다.

> 함수의 상위 스코프를 결정하는 방식인 렉시컬 스코프(Lexical scope)는 함수를 선언할 때 결정된다. this 바인딩과 혼동하지 않도록 주의한다.

- 함수를 호출하는 방식은 아래와 같이 다양하다.
> 1. 함수 호출
> 2. 메소드 호출
> 3. 생성자 함수 호출
> 4. apply / call / bind 호출

		var foo = function(){
			console.dir(this);
		};

		// 1. 함수 호출
		foo(); //window

		// 2. 메소드 호출
		var obj = {foo: foo};
		obj.foo(); // obj

		// 3. 생성자 함수 호출
		var instance = new foo(); // instance

		// 4. apply/call/bind 호출
		var bar = {name: 'bar'};
		foo.call(bar) // bar
		foo.apply(bar) // bar
		foo.bind(bar) // bar

## 1. 함수 호출

- 전역 객체(Global Object)는 모든 객체의 유일한 최상위 객체를 의미하며, 일반적으로 Browser-side에서는 window, Server-side에서는 global 객체를 의미한다.

		// in browser 
		this === window // true

		// in terminal
		this === global //true

- 전역객체는 전역 스코프를 갖는 전역 변수를 프로퍼티로 소유한다. 글로벌 영역에 선언한 함수는 전역객체의 프로퍼티로 접근할 수 있는 전역 변수의 메소드이다.

- 기본적으로 this는 전역객체 (Global Object)에 바인딩된다. 전역함수는 물론이고 심지어 내부함수의 경우도 this는 외부함수가 아닌 전역객체에 바인딩 된다.

- 메소드의 내부함수일 경우에도 this는 전역객체에 바인딩된다.

- 콜백함수의 경우에도 this는 전역객체에 바인딩 된다.

- 즉, 내부함수는 일반함수, 메소드, 콜백함수 어디에서 선언되었든 관계없이 this는 전역객체를 바인딩한다.

		//예시 1
		function foo(){
			console.log(`foo is this: ${this}`); //window
			function bar(){
				console.log(`bar is this ${this}`) //window
			}
			bar();
		}
		foo();

		// 예시 2
		var value = 1;

		var obj = {
		value: 100,
		foo: function() {
			console.log("foo's this: ",  this);  // obj
			console.log("foo's this.value: ",  this.value); // 100
			function bar() {
			console.log("bar's this: ",  this); // window
			console.log("bar's this.value: ", this.value); // 1
			}
			bar();
		}
		};

		obj.foo();

		// 예시3
		var value = 1;

		var obj = {
		value: 100,
		foo: function() {
			setTimeout(function() {
			console.log("callback's this: ",  this);  // window
			console.log("callback's this.value: ",  this.value); // 1
			}, 100);
		}
		};

		obj.foo();

- 위와같이 내부함수의 this가 전역객체를 참조하는 것을 회피하는 방법은 두 가지가 있다.
	
		//객체 내부에 that 이라는 변수를 사용해서 객체 내부의 this를 그 자체로 만드는 것
		var value = 1;
		var obj = {
		value: 100,
		foo: function(){
			var that = this; // this === obj
			
			console.log("foo's this: ",  this);  // obj
			console.log("foo's this.value: ",  this.value); // 100
			function bar() {
			console.log("bar's this: ",  this); // window
			console.log("bar's this.value: ", this.value); // 1

			console.log("bar's that: ",  that); // obj
			console.log("bar's that.value: ", that.value); // 100
			}
			bar();
		}
		};

		obj.foo();

		// this 를 명시적으로 바인딩할 수 있는 apply, call, bind 메소드를 제공
		// 첫번째 인자(argument) 로 명시된 객체 = this

		var value = 1;

		var obj = {
		value: 100,
		foo: function() {
			console.log("foo's this: ",  this);  // obj
			console.log("foo's this.value: ",  this.value); // 100
			function bar(a, b) {
			console.log("bar's this: ",  this); // obj
			console.log("bar's this.value: ", this.value); // 100
			console.log("bar's arguments: ", arguments);
			}
			bar.apply(obj, [1, 2]);
			bar.call(obj, 1, 2);
			bar.bind(obj)(1, 2);
		}
		};

		obj.foo();

## 2. 메소드 호출

- 함수가 객체의 프로퍼티 값이면 메소드로서 호출된다. 이 때 메소드 내부의 this는 해당 메소드를 소유한 객체, 즉 해당 메소드를 호출한 객체에 바인딩 된다.

- 프로토타입 객체도 메소드를 가질 수 있다. 프로토타입 객체 메소드 내부에서 사용된 this도 일반 메소드 방식과 마찬가지로 해당 메소드를 호출한 객체에 바인딩된다.

		var obj1 = {
			name: 'Lee',
			sayName: function(){
				console.log(this.name)
			}
		}
		var obj2 = {
			name: 'Kim'
		}
		obj2.sayName = obj1.sayName

		obj1.sayName() // Lee
		obj2.sayName() // Kim

- 전역객체는 전역 스코프를

## 3. 생성자 함수 호출

- 자바스크립트의 생성자 함수는 말 그대로 객체를 생성하는 역할을 한다.

- 기존 함수에 new 연산자를 붙여서 호출하면, 해당 함수는 생성자 함수로 동작한다.

- 반대로 생각하면 생성자 함수가 아닌, 일반 함수에 new 연산자를 붙여 호출하면 생성자 함수처럼 동작할 수 있으므로, 일반적으로 생성자 함수 명은 첫 문자를 대문자로 기술하여 혼란을 방지한다.

		// 생성자 함수
		function Person(name) {
			this.name = name;
		}

		//new 연산자 
		var me = new Person('Lee');
		console.log(me) // Person {name: 'Lee'}

		// new 연산자와 함께 생성자 함수를 호출하지 않으면 생성자 함수로 동작하지 않는다.
		var you = Person('Kim');
		console.log(you) // undefined

- 객체 리터럴 방식 과 생성자 함수 방식의 차이

	- 프로토타입 객체에 있다. 

	- 객체 리터릴 방식의 경우, 생성된 객체의 프로토타입 객체는 Object.prototype 이다.

	- 생성자 함수 방식의 경우, 생성된 객체의 프로토 타입 객체는 Person.prototype 이다.

	- 리터럴? 모든 데이터에 들어가는 데이터 값 그 자체

			// 객체 리터럴 방식
			var foo = {
			name: 'foo',
			gender: 'male'
			}

			console.dir(foo); // Object

			// 생성자 함수 방식
			function Person(name, gender) {
			this.name = name;
			this.gender = gender;
			}

			var me  = new Person('Lee', 'male');
			console.dir(me); // Person

			var you = new Person('Kim', 'female');
			console.dir(you); // Person

## 4. apply/call/bind 호출

- this에 바인딩될 객체는 함수 호출 패턴에 의해 결정된다. 이는 자바스크립트 엔진이 수행하는 것인데, 이런 자바스크립트 엔진의 암묵적 This 바인딩 외에 this를 특정 객체에 명시적으로 바인딩 하는 방법도 제공된다.

- Function.prototype.apply, Function.prototype.call 메소드이다.

- 이 메소드들은 모든 함수 객체의 프로토타입 객체인 Function.prototype 객체의 메소드이다. 

		func.apply(thisArg, [arjsArray])

		// thisArg : 함수 내부의 this에 바인딩할 객체
		// argsArray : 함수에 전달 할 argument의 배열 

		// 예시1 
		var Person = function(name){
			this.name = name;
		}

		var foo = {}

		//apply 메소드는 생성자함수 Person을 호출한다. 이 때 this에 객체 foo를 바인딩한다.
		Person.apply(foo,['Lee'])
		
		console.log(foo); // {name: 'Lee'}

- apply 메소드를 호출하는 주체는 함수이며, apply() 메소드는 this를 특정 객체에 바인딩 할 뿐 본질적인 기능은 함수 호출이다.

- call() 메소드의 경우, apply()와 기능은 값지만 apply의 두번째 인자에서 배열 형태로 넘긴 것을 각각의 하나의 인자로 넘긴다

# 화살표 함수

- function 표현에 비해 구문이 짧고, 자신의 this, arguments, super 또는 new.taget을 바인딩 하지 않는다.

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

- 또는 콜백 함수로 사용할 수 있다. 이 경우 일반적인 함수 표현식보다 표현이 간결하다.
       
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

3. 화살표 함수를 사용하면 안되는 경우

	1. 객체의 메소드를 정의할 때는 사용하지 않는다.

			// 기존 function 함수나, 축약 표현식으로 바꿔서 작성한다.

			var obj = {
				name: 'Lee',
				hi: () => console.log(`Hi ${this.name`);
			}
			obj.hi(); //Hi undefined
			// 객체의 this를 바인딩하지 않고 전역객체가 바인딩 된다.

			var obj = {
				name: 'Lee',
				hi: {
					console.log(`hi ${this.name}`)
				}
			}
			obj.hi // hi Lee

			// prototype에 메소드를 할당할 때에도 기존 함수로 사용한다.
			const obj = {
			name: 'Lee',
			};
			Object.prototype.hi = () => console.log(`Hi ${this.name}`);
			obj.hi(); // Hi undefined

			// 이게 옳은 표현이라고 한다.
			Object.prototype.sayHi = function() {
			console.log(`Hi ${this.name}`);
			};

	2. 생성자 함수는 prototype 프로퍼티를 갖지만, 화살표 함수는 prototype 프로퍼티를 갖지 않는다. 고로 생성자 함수로 사용할 수 없다.

	3. addEventListner 함수의 콜백 함수에서 사용하면, this가 상위 컨텍스트를 가리킨다.

			var button = document.getElementById('myButton');  

			button.addEventListener('click', () => {  
				console.log(this === window); // => true
				this.innerHTML = 'Clicked button';
			});
			
			var button = document.getElementById('myButton');  

			button.addEventListener('click', function() {  
				console.log(this === button); // => true
				this.innerHTML = 'Clicked button';
			});

# this 와 일반 함수에서 this의 차이 

- function 키워드로 생성한 일반함수와 화살표 함수의 가장 큰 차이점은 this 이다.

1. 일반 함수의 this

-  자바스크립트의 경우 함수 호출 방식에 의해 this에 바인딩할 어떤 객체가 동적으로 결정된다. 

- 함수를 선언할 때 this에 바인딩할 객체가 정적으로 결정되는 것이 아니고, 함수를 호출할 때 함수가 어떻게 호출되었는지에 따라 this에 바인딩할 객체가 동적으로 결정된다.

- 콜백 함수 내부의 this는 전역 객체 window를 가리킨다.

2. 화살표 함수의 this

- 화살표 함수는 함수를 선언할 때 this에 바인딩할 객체가 정적으로 결정된다.

- 화살표 함수의 this 바인딩 객체 결정 방식은 함수의 상위 스코프를 결정하는 방식인 렉시컬 스코프와 유사하다.

- 즉, 기존 함수에서 this는 dynamic scoping (동적 스코프 이 되었는데 화살표 함수는 lexical scoping을 사용하게 된다. 고로 따로 binding을 사용하지 않아도 된다. 정리하면 자신만의 this를 생성하지 않고 자신을 포함하고 있는 context의 this를 이어 받는다.

> 동적으로 결정되는 일반 함수와는 달리 화살표 함수의 this 언제나 상위 스코프의 this를 가리킨다. 이를 Lexical this라 한다.
		
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

			button.addEventListener('click', () => {
			console.log(this === window); // => true
			console.log(this === button); // => false
			});

			button.addEventListener('click', function() {
			console.log(this === window); // => false
			console.log(this === button); // => true
			});

4. 파라미터 기본값 , spread 문법 , rest/spread 프로퍼티

  1. 파라미터 기본 값

    - 파라미터에 기본값을 설정하여 함수 내에서 수행하던 파라미터 체크 및 초기화를 간소화할 수 있다.

        function plus (x = 0, y = 0){
          // 파라미터 x,y에 인수를 할당하지 않은 경우, 기본 값을 0 을 할당한다.
          return x + y;

        }

- 참고

- [MDN-화살표함수](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/%EC%95%A0%EB%A1%9C%EC%9A%B0_%ED%8E%91%EC%85%98)
- [화살표 함수](https://jeong-pro.tistory.com/110)
- [화살표 함수](https://hanjungv.github.io/2018-02-03-1_JS_arrow_function/)

- [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number/isNaN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number/isNaN)
- [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number/isNaN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/isNaN)