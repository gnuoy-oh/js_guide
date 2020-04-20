## Array = 배열

* 순서가 있는 값들의 모임, 보통 같은 type의 데이터로 이루어져 있다.

* 자바스크립트에서 배열은 하위 값들의 그룹을 나타내는 하나의 값으로 생각할 수 있다.

* var num = [1,36,73,3]
    
        - 배열의 값을 바꿀수도 있다. num[0] = 10;
        - 배열의 갯수 = num.length
        * push(값) -> 배열 끝에 값을 추가
            - arr1.push('hi');
        * pop(); -> 배열의 마지막 값을 제거
        * shift(); -> 배열 첫번째 값을 제거
        * unshift(값); -> 배열의 맨 앞에 값을 추가
        * reverse() -> 배열의 요소의 순서를 바꾼다.
        * sort -> 배열의 요소를 분류한다.
        
* 메소드 / 프로퍼티

        - PROPERTY : 인덱스 정보를 불러온다.
        
        - length : 인덱스 갯수를 불러온다.
        
        - Method : 인덱스에게 명령을 한다.
        
* 배열을 하는 방식

    1. 리터럴 방식 : 직접 대괄호를 사용해서 배열하는 방식
    
        - var arr = ["apple", "orange", "tomato"]
        
        - 위 요소들을 데이터 / 엘리먼트 / 요소 라고 한다.
        
    2. Array 생성자 함수 방식 :
    
        - Array, Number, String, Object 등 리스트와 비슷한 고 수준의 배열을 생성하는데 사용되는 전역 객체 방식
        
        - var arr2 = new Array(4,1,2,6,"apple);
        
        - console.log(arr2);
        
        - // [4,1,2,6, "apple"]

## Object = 객체

- 변수와 함수를 묶어서 관리하는 것
- Property(속성) + Method(명령)을 가질 수 있다.
- 객체 지향 프로그래밍
    - 유지보수가 쉬워진다.
    - 가독성이 높아진다.
    - 대형 프로젝트 할 때 좋다.

        var foo = {}
        
        foo.name = "oh minyoung";
        foo.weight = 100;
        foo.eat = function(food){
        	console.log(this.name + "이 " + food + "를 먹었습니다.");
        	foo.weight += 5;
        }
        
        foo.eat("치킨");

- this
    - 객체의 메소드 안에서 사용 시, 함수를 소유한 객체를 가르킨다.
- 객체 만들기 JSON 표기법 - JavaScript Object Notation
- 객체 만들기 생성자 함수

# 객체(Object)란?

- JS는 객체(Object)기반의 스크립트 언어이며, JS를 이루고 있는 거의 모든 것 이 객체이다.
- 원시 타입(Primitives)을 제외한 나머지 값들 (함수, 배열, 정규 표현식 등)은 모두 객체이다.
- JS의 객체는 key와 value로 구성된 프로퍼티(Property)들의 집합이다.
- JS의 함수는 일급 객체 이므로, 값으로 취급할 수 있다.
    - Property 값으로 함수를 사용할 수도 있으며, Property 값이 함수일 경우, 일반 함수와 구분하기 위해 Method라고 부른다.
- 이와 같이 객체는 데이터를 의미하는 Property와 데이터를 참조하고 조작할 수 있는 동작을 의미하는 Method로 구성된 집합니다. 객체는 데이터(property)와 그 데이터에 관련된 동작(method)을 모두 포함할 수 있기 때문에 데이터와 동작을 하나의 단위로 구조화 할 수 있어 유용하다.
- JS의 객체는 객체 지향의 상속을 구현하기 위해 Prototype 이라고 불리는 객체의 프로퍼티와 메소드를 상속받을 수 있다. 이 프로토타입은 타 언어와 구별되는 중요한 개념이다.

## Property

- 프로퍼티 키(이름)와 프로퍼티 값 으로 구성된다.
- 프로퍼티는 프로퍼티 키 로 유일하게 식별할 수 있다. 즉, 프로퍼티 키는 프로퍼티를 식별하기 위한 식별자다

Property Key: 빈 문자열을 포함하는 모든 문자열 또는 symbol 값
Property : 모든 값

- 프로퍼티 키에 문자열이나 symbol 값 이외의 값을 지정하면 암묵적으로 타입이 변환되어 문자열이 된다. 이미 존재하는 프로퍼티 키를 중복 선언하면 나중에 선언한 프로퍼티가 먼저 선언한 프로퍼티를 덮어쓴다.
- 배열과 달리 객체는 프로퍼티를 열거할 때 순서를 보장하지 않는다.

## Method

- 프로퍼티 값이 함수일 경우, 일반 함수와 구분하기 위해 메소드라 부른다. 즉. 메소드는 객체에 제한되어 있는 함수를 의미한다.

### 1. 객체 생성 방법

### 1-1. 객체 리터럴

- 가장 일반적인 JS 객체 생성 방식으로, 클래스 기반 객체 지향 언어와 비교할 때 매우 간편하게 객체를 생성할 수 있다.
- 중괄호 ({})를 사용하여 객체를 생성하는데, {} 내에 1개 이상의 프로퍼티를 기술하면, 해당 프로퍼티가 추가된 객체를 생성할 수 있다.
- {} 내에 아무것도 기술하지 않으면, 빈 객체가 생성된다.

    var emptyObject = { };
    console.log(typeof emptyObject); //object
    
    var person = {
    	name: 'Lee',
    	gender: 'male',
    	sayHello: function (){
    		console.log('Hi! my name is ' + this.name);
    	}
    };
    
    console.log(typeof person); // object
    console.log(person); // {name: "Lee", gender: "male", sayHello: f}
    
    persone.sayHello(); // Hi! my name is Lee
    

### 1-2. Object 생성자 함수

- new 연산자와 Object 생성자 함수를 호출하여, 빈 객체를 생성할 수 있다.
- 빈 객체 생성 이후 프로퍼티 또는 메소드를 추가하여 객체를 완성하는 방법이다.
- 생성자(constructor) 함수란, new 키워드와 함께 객체를 생성하고, 초기화하는 함수를 말한다.
- 생성자 함수를 통해 생성된 객체를 인스턴스(instance)라고 한다.
- JS는 Object 생성자 함수 이외에도 String, Number, Boolean, Array, Date, RegExp 등의 빌트인 생성자 함수를 제공한다. 일반 함수와 생성자 함수를 구분하기 위해 생성자 함수의 이름은 파스칼 케이스로 사용하는 것이 일반적이다.
- 객체가 소유하고 있지 않은 프로퍼티 키에 값을 할당하면, 해당 객체에 프로퍼티를 추가하고 값을 할당한다.
- 이미 존재하는 프로퍼티 키에 새로운 값을 할당하면 프로퍼티 값은 할당한 값으로 변경된다.

    var person = new Object();
    
    person.name = 'Lee';
    person.gender = 'male';
    person.sayHello = function (){
    	console.log('Hi! my name is ' + this.name);
    }
    
    console.log(typeof person); // object
    console.log(person); // {name: "Lee", gender: "male", sayHello: ƒ}
    
    person.sayHello(); // Hi! My name is Lee

- 반드시 Object 생성자 함수를 사용해서 빈 객체를 생성해야 하는 것을 아니다. 객체를 생성하는 방법은 객체 리터럴을 사용하는 것이 더 간편하다.
- 객체 리터럴 방식으로 생성된 객체는 결국 빌트인 함수인 Object 생성자 함수로 객체를 생성하는 것을 단순화 시킨 축약 표현이다.
- 즉, JS 엔진은 객체 리터럴로 객체를 생성하는 코드를 만나면 내부적으로 Object 생성자 함수를 사용하여 객체를 생성한다. 따라서 개발자가 일부러 Object 생성자 함수를 사용해 객체를 생성해야 할 일은 거의 없다.

### 1-3. 생성자 함수

- 객체 리터럴 방식과 Object 생성자 함수 방식으로 객체를 생성하는 것은 프로퍼티 값만 다른 여러 개의 객체를 생성할 때 불편하다. 동일한 프로퍼티를 갖는 객체임에도 불구하고 매번 같은 프로퍼티를 기술해야 한다.

    var person1 = {
      name: 'Lee',
      gender: 'male',
      sayHello: function () {
        console.log('Hi! My name is ' + this.name);
      }
    };
    
    var person2 = {
      name: 'Kim',
      gender: 'female',
      sayHello: function () {
        console.log('Hi! My name is ' + this.name);
      }
    };

- 생성자 함수를 사용하면, 마치 객체를 생성하기 위함 템플릿(클래스)처럼 사용하여, 프로퍼티가 동일한 객체 여러 개를 간편하게 생성할 수 있다.

    // 생성자 함수
    function Person(name, gender){
    	this.name = name;
    	this.gender = gender;
    	this.sayHello = function(){
    		console.log('Hi! my name is ' + this.name);
    	};
    }
    
    //instance 생성
    var person1 = new Person('Lee', 'male');
    var person2 = new Person('Kim', 'female');
    
    console.log('person1: ', typeof person1);
    console.log('person2: ', typeof person2);
    console.log('person1: ', person1);
    console.log('person2: ', person2);
    
    person1.sayHello();
    person2.sayHello();

- 생성자 함수 이름은 일반적으로 대문자로 시작한다. 이것은 생성자 함수임을 인식하도록 도와준다.
- 프로퍼티 또는 메소드 명 앞에 기술한 this는 생성자 함수가 생성할 인스턴스를 가리킨다.
- this에 연결(바인딩)되어 있는 프로퍼티와 메소드는 public(외부에서 참조 가능) 하다.
- 생성자 함수 내에서 선언된 일반 변수는 private(외부에서 참조 불가능)하다. 즉, 생성자 함수 내부에서는 자유롭게 접근이 가능하나 외부에서 접근할 수 없다.

    function Person(name, gender){
    	var married = true;
    	this.name = name;
    	this.gender = gender;
    	this.sayHello = function(){
    		console.log('Hi! my name is' + this.name);
    	}
    }
    
    var person = new Person('Lee', 'male');
    
    console.log(typeof person);// object
    console.log(person); // Person { name: 'Lee', gender: 'male', sayHello: [Function] }
    
    console.log(person.gender); //'male'
    console.log(person.married); //undefined

- JS의 생성자 함수는 이름 그대로 객체를 생성하는 함수이다. 하지만 자바와 같은 클래스 기반 객체지향 언어의 생성자(constructor)와는 다르게 그 형식이 정해져 있는 것이 아니라 기존 함수와 동일한 방법으로 생성자 함수를 선언하고 new 연산자를 붙여서 호출하면 해당 함수는 생성자 함수로 동작한다.
- 이는 생성자 함수가 아닌 일반 함수에 new 연산자를 붙여 호출하면 생성자 함수처럼 동작할 수 있다는 것을 의미한다. 따라서 일반적으로 생성자 함수명은 첫문자를 대문자로 기술하여 혼란을 방지하려는 노력을 한다.

### 2. 객체 프로퍼티 접근

### 2-1. 프로퍼티 키

- 프로퍼티의 키는 일반적으로 문자열을 지정한다. 프로퍼티 키에 문자열이나 symbol 값 이외의 값을 지정하면 암묵적으로 타입이 변환되어 문자열(String)이 된다.
- 문자열 타입의 값으로 수렴될 수 있는 표현식도 가능하다. 프로퍼티 키는 문자열 이므로 따옴표를 사용한다.
- 하지만 JS에서 사용 가능한 유효한 이름인 경우, 따옴표를 생략할 수 있다. 반대로 말하면 JS에서 사용 가능한 유효한 이름이 아닌 경우, 반드시 따옴표를 사용해야 한다.
- 프로퍼티 값은 모든 값과 표현식이 올 수 있으며, 프로퍼티 값이 함수인 경우 이를 메소드라고 한다.

    var person = {
      'first-name': 'Ung-mo',
      'last-name': 'Lee',
      gender: 'male',
      1: 10,
      function: 1 // OK. 하지만 예약어는 사용하지 말아야 한다.
    };
    
    console.log(person);
    
    표현식을 프로퍼티 키로 사용하려면 키로 사용할 표현식을 대괄호로 묶어야 한다. 이때 자바스크립트 엔진은 표현식을 평가하기 위해 식별자 first를 찾을 것이고 이때 ReferenceError가 발생한다.
    var person = {
      [first-name]: 'Ung-mo', // ReferenceError: first is not defined
    	};
    

### 2-2. 프로퍼티 값 읽기

- 객체의 프로퍼티 값에 접근하는 방법은 마침표(.) 표기법과 대괄호 ([]) 표기법이 있다.
- 대괄호 표기법을 사용하는 경우, 대괄호 내에 들어가는 프로퍼티 이름은 반드시 문자열(String)이어야 한다.
- 객체에 존재하지 않는 프로퍼티를 참조하면 undefined를 반환한다.

    var person = {
      'first-name': 'Ung-mo',
      'last-name': 'Lee',
      gender: 'male',
      1: 10
    };
    
    console.log(person);
    
    console.log(person.first-name);    // NaN: undefined-undefined
    console.log(person[first-name]);   // ReferenceError: first is not defined
    console.log(person['first-name']); // 'Ung-mo'
    
    console.log(person.gender);    // 'male'
    console.log(person[gender]);   // ReferenceError: gender is not defined
    console.log(person['gender']); // 'male'
    
    console.log(person['1']); // 10
    console.log(person[1]);   // 10 : person[1] -> person['1']
    console.log(person.1);    // SyntaxError

### 2-3. 프로퍼티 값 갱신

- 객체가 소유하고 있는 프로퍼티에 새로운 값을 할당하면 프로퍼티 값은 갱신된다.

    var person = {
      'first-name': 'Ung-mo',
      'last-name': 'Lee',
      gender: 'male',
    };
    
    person['first-name'] = 'Kim';
    console.log(person['first-name'] ); // 'Kim'

### 2-4. 프로퍼티 동적 생성

- 객체가 소유하고 있지 않은 프로퍼티에 값을 할당하면 주어진 키와 값으로 프로퍼티를 생성하여 객체에 추가한다.

    var person = {
      'first-name': 'Ung-mo',
      'last-name': 'Lee',
      gender: 'male',
    };
    
    person.age = 20;
    console.log(person.age); // 20

### 2-5. 프로퍼티 삭제

- delete 연산자를 사용하면 객체의 프로퍼티를 삭제할 수 있다. 이 때 피연산자는 프로퍼티 키어야 한다.

    var person = {
      'first-name': 'Ung-mo',
      'last-name': 'Lee',
      gender: 'male',
    };
    
    delete person.gender;
    console.log(person.gender); // undefined
    
    delete person;
    console.log(person); // Object {first-name: 'Ung-mo', last-name: 'Lee'}

### 2-6. for-in 문

- for-in문을 사용하면 객체(배열 포함)에 포함된 모든 프로퍼티에 대해 루프를 수행할 수 있다.

    var person = {
    	'first-name': 'Ung-mo',
    	'last-name': 'Lee',
    	gender: 'male'
    };
    
    // prop에 객체의 프로퍼티 이름이 반환된다. 단, 순서는 보장되지 않는다.
    for(var prop in person){
    	console.log(prop + ': ' + person[prop]);
    }
    
    /*
    first-name: Ung-mo
    last-name: Lee
    gender: male
    */
    
    var array = ['one', 'two']
    
    
    //index에 배열의 경우 인덱스가 반환된다.
    for(var index in array){
    	console.log(index + ': ' + array[index]);
    
    }
    
    /*
    0: one
    1: two
    */

- for-in 문은 객체의 문자열 키(key)를 순회하기 위한 문법이다. 배열에는 사용하지 않는 것이 좋다.
    - 객체의 경우, 프로퍼티 순서가 보장되지 않는다. 그 이유는 원래 객체의 프로퍼티에는 순서가 없기 때문이다. 배열은 순서를 보장하는 데이터 구조이지만 객체와 마찬가지로 순서를 보장하지 않는다.
    - 배열 요소들만을 순회하지 않는다.

    // 배열 요소들만을 순회하지 않는다.
    var array = ['one', 'two'];
    array.name = 'my array';
    
    for (var index in array) {
      console.log(index + ': ' + array[index]);
    }
    
    /*
    0: one
    1: two
    name: my array
    */

### 2-7. for-of 문

- 위와 같은 문제를 극복하기 위해, ES6에서 추가되었다.
- for-of 문은 배열의 요소를 순회하기 위해 사용한다.

    const array = [1, 2, 3];
    array.name = 'my array';
    
    for (const value of array) {
      console.log(value);
    }
    
    /*
    1
    2
    3
    */
    
    for (const [index, value] of array.entries()) {
      console.log(index, value);
    }
    
    /*
    0 1
    1 2
    2 3
    */

### 3. Pass-by-reference

- object type을 객체 타입 또는 참조 타입(reference type)이라고 한다.
- 참조 타입이란, 객체의 모든 연산이 실제 값이 아닌 **참조 값으로 처리됨을 의미한다.**
- 원시 타입은 값이 한번 정해지면 변경할 수 없지만(immutable),  객체는 프로퍼티를 변경, 추가, 삭제가 가능하므로 변경 가능(mutable)한 값이라고 할 수 있다.
- 따라서 객체 타입은 동적으로 변화할 수 있으므로, 어느 정도의 메모리 공간을 확보해야 하는지 예측할 수 없기 때문에, 런타임에 메모리 공간을 확보하고 메모리의 힙 영역에 저장된다.
- 이에 반해 **원시 타입은 값(value)로 전달 된다. 즉, 복사되어 전달된다. 이를 pass-by-value라고 한다.**

    // Pass-by-reference
    
    var foo = {
    	val: 10
    }
    
    var bar = foo;
    console.log(foo.val, bar,val); // 10 10
    console.log( foo === bar ); // true
    
    bar.val = 20;
    console.log(foo.val , bar.val); // 20 20
    console.log(foo === bar); // true
    
    // 변수 foo 는 객체 자체를 저장하고 있는 것이 아니라, 
    //생성된 객체의 참조 값(address)를 저장하고 있다.

- 변수 bar에 변수 foo의 값을 할당하였다. 변수 foo의 값은 생성된 객체를 가리키는 참조 값이므로, 변수 bar에도 같은 참조 값이 저장된다.
- 즉, 변수 foo, bar 모두 동일한 객체를 참조하고 있다. 따라서 참조하고 잇는 객체의 val 값이 변경이 되면 변수 foo, bar 모두 동일한 객체를 참조하고 있으므로 두 변수 모두 변경된 객체의 프로퍼티 값을 참조하게 된다.
- 객체는 참조 방식으로 전달된다. 결 코 복사되지 않는다.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/787d48d4-e095-478f-838b-39754e2d7ec5/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/787d48d4-e095-478f-838b-39754e2d7ec5/Untitled.png)

    var foo = { val: 10 };
    var bar = { val: 10 };
    
    console.log(foo.val, bar.val} // 10 10 
    console.log(foo.val === bar.val} // false
    
    var baz = bar;
    
    console.log(baz.val, bar.val); // 10 10
    console.log(baz === bar); // true

- 변수 foo 와 변수 bar는 비록 내용은 같지만, 별개의 객체를 생성하여 참조값을 할당하였다. 따라서 변수 foo와 변수 bar의 참조값 즉 address는 동일하지 않다.
- 변수 baz에는 변수 bar 값을 할당하였다. 결국 변수 baz와 변수 baz는 동일한 객체를 가리키는 참조 값을 저장하고 있다. 따라서 baz와 bar의 참조 값을 동일하다.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fdc5f7d9-231b-458a-80d6-17e87f501cb5/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fdc5f7d9-231b-458a-80d6-17e87f501cb5/Untitled.png)

    var a = {}, b = {}, c = {} // 서로 각각 다른 빈 객체를 참조 
    console.log(a===b, a===c, b===c); // false false false
    
    a = b = c = {}; // 모두 같은 빈 객체를 참조]
    console.log(a===b, a===b, b===c); //true true true

### 4. Pass-by-value(값에 의한 전달)

- 원시 타입은 값(value)로 전달된다.
- 즉 값이 복사되어 전달된다.
- 원시 타입은 값이 한번 정해지면 변경할 수 없다.(IMMUTABLE)
- 또한 이들 값은 런타임 (변수 할당 시점)에 메모리의 스택 영역 (stack segment)에 고정된 메모리 영역을 점유하고 저장된다.

    var a = 1;
    var b = a;
    
    console.log(a, b); // 1 1
    console.log( a === b ) // true
    
    a = 10;
    console.log(a, b); // 1 10
    console.log( a=== b); //false
    
    // 변수 a는 원시 타입인 number 1을 저장하고 있다.
    // 원시 타입의 경우, 값이 복사되어 변수에 저장된다.
    // 즉, 참조 타입을 저장되는 것이 아니라 값 자체가 저장되게 된다.
    // 변수 b에 변수 a를 할당할 경우, 변수 a 의 값 1은 복사되어 변수 b에 저장된다.

### 5. 객체의 분류

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a2015785-afb8-47ac-b4a6-b9e80f48702f/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a2015785-afb8-47ac-b4a6-b9e80f48702f/Untitled.png)

- Built-in Object(내장 객체)는 웹페이지 등을 표현하기 위한 공통의 기능을 제공한다.
    - 웹 페이지가 브라우저에 의해 로드되자마자 별다른 행위없이 바로 사용이 가능하다.
    - standard Built-in Object (or Global Object)
    - BOM(Browser Object Model)
    - DOM(Document Object Model)
- Standard Built-in Object(표준 빌트 인 객체)을 제외한 BOM과 DOM을 Native Object라고 분류하기도 한다. 또한 사용자가 생성한 객체를 Host Object (사용자 정의 객체) 라고 한다.
- Hose Object (사용자 정의 객체)
    - 사용자가 생성한 객체 들이다. constructor 혹은 객체리터럴을 통해 사용자가 객체를 정의하고 확장시킨 것들이기 때문에 Built-in Object 와 Native Object가 구성된 이후에 구성된다.

## Function

- 입력과 출력이 있는 형태로, **매개변수 → 처리 → return 값 출력**의 형태를 가진다.
- 리턴 값이 있을 경우, 함수를 호출해서 변수에 값을 넣을 수 있다.

    var foo =function(hello){
    	return hello
    }
    
    var a = foo();
    

- 리턴 값이 없을 경우, 변수에 값을 넣어주고 출력하면, undefined로 나온다.

### 함수란

- 어떤 작업을 수행하기 위해 필요한 문 들의 집합을 정의한 코드 블록이다.
- 함수는 이름과 매개변수를 가지며, 필요한 때에 호출하여 코드 블록에 담긴 문들을 일괄적으로 실행할 수 있다.
- 동일한 작업을 반복적으로 수행해야 한다면 미리 정의된 함수를 재사용하는 것이 효율적이다.
- 함수의 일반적 기능은 어떤 작업을 수행하는 문 들의 집합을 정의해서 코드의 재사용에 목적이 있다.
    - 이러한 일반적 기능 이외에 객체 생성, 객체의 행위 정의(메소드), 정보 은닉, 클로저, 모듈화 등의 기능을 수행할 수 있다.
- 자바스크립트의 함수는 객체(일급 객체, First-class object)이다.
    - 다른 객체와 구분될 수 있는 특징은 호출할 수 있다는 것이다.
    - 함수도 객체이므로 다른 값들처럼 사용할 수 있다.
    - 즉, 변수나 객체, 배열 등에 저장할 수 있고 다른 함수에 전달되는 인수로도 사용할 수 있으며 함수의 반환값이 될 수도 있다.

    // 함수의 정의 (함수 선언문)
    function square(number){
    	return number * number
    }
    
    // 함수의 호출
    square(2);

## 함수 정의

### 함수 선언문

- **함수명**

    함수 선언문의 경우, 함수명은 생략할 수 없다. 함수명은 함수 몸체에서 자신을 재귀적(recursive) 호출하거나 자바스크립트 디버거가 해당 함수를 구분할 수 있는 식별자이다.

- **매개변수 목록**

    0개 이상의 목록으로 괄호로 감싸고 콤마로 분리한다. 다른 언어와의 차이점은 매개변수의 타입을 기술하지 않는다는 것이다. 이 때문에 함수 몸체 내에서 매개변수의 타입 체크가 필요할 수 있다.

- **함수 몸체**

    함수가 호출되었을 때 실행되는 문들의 집합이다. 중괄호({ })로 문들을 감싸고 `return` 문으로 결과값을 반환할 수 있다. 이를 반환값(return value)라 한다.

    // 함수 선언문
    function square(number) {
      return number * number;
    }

### 함수 표현식

- 자바스크립트의 함수는 일급 객체 이므로 아래와 같은 특징이 있다.
    1. 무명의 리터럴로 표현이 가능하다.
    2. 변수나 자료 구조(객체, 배열…)에 저장할 수 있다.
    3. 함수의 파라미터로 전달할 수 있다.
    4. 반환값(return value)으로 사용할 수 있다.
- 함수의 일급객체 특성을 이용하여 함수 리터럴 방식으로 함수를 정의하고 변수에 할당할 수 있는데 이러한 방식을 함수 표현식(Function expression)이라 한다.

    // 함수 표현식
    var square = function(number) {
      return number * number;
    };

- 함수 표현식 방식으로 정의한 함수는 함수명을 생략할 수 있다. 이러한 함수를 익명 함수(anonymous function)이라 한다. 함수 표현식에서는 함수명을 생략하는 것이 일반적이다.

    // 기명 함수 표현식(named function expression)
    var foo = function multiply(a, b) {
      return a * b;
    };
    
    // 익명 함수 표현식(anonymous function expression)
    var bar = function(a, b) {
      return a * b;
    };
    
    console.log(foo(10, 5)); // 50
    console.log(multiply(10, 5)); // Uncaught ReferenceError: multiply is not defined

- 함수는 일급객체이기 때문에 변수에 할당할 수 있는데 이 변수는 함수명이 아니라 할당된 함수를 가리키는 참조값을 저장하게 된다. 함수 호출시 함수명이 아니라 함수를 가리키는 변수명을 사용하여야 한다.

    var foo = function(a, b) {
      return a * b;
    };
    
    var bar = foo;
    
    console.log(foo(10, 10)); // 100
    console.log(bar(10, 10)); // 100

- 변수 bar와 변수 foo는 동일한 익명 함수의 참조값을 갖는다.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/16254ac0-a62f-4871-8933-2a6d530a9f46/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/16254ac0-a62f-4871-8933-2a6d530a9f46/Untitled.png)

- **함수가 할당된 변수를 사용해 함수를 호출하지 않고 기명 함수의 함수명을 사용해 호출하게 되면 에러가 발생한다. 이는 함수 표현식에서 사용한 함수명은 외부 코드에서 접근 불가능하기 때문이다.** (사실은 함수 선언문의 경우도 마찬가지이다.)
- 함수 표현식과 함수 선언문에서 사용한 함수명은 함수 몸체에서 자신을 [재귀적 호출(Recursive function call)](https://ko.wikipedia.org/wiki/%EC%9E%AC%EA%B7%80%ED%95%A8%EC%88%98)하거나 자바스크립트 디버거가 해당 함수를 구분할 수 있는 식별자의 역할을 한다.
- 함수 선언문으로 정의한 함수 square의 경우, 함수명으로 호출할 수 있었는데 이는 자바스크립트 엔진에 의해 아래와 같은 함수 표현식으로 형태가 변경되었기 때문이다.

    var square = function square(number) {
      return number * number;
    };

- 함수명과 함수 참조값을 가진 변수명이 일치하므로 함수명으로 호출되는 듯 보이지만 사실은 변수명으로 호출된 것이다.
- **결국 함수 선언문도 함수 표현식과 동일하게 함수 리터럴 방식으로 정의되는 것이다.**

### Function 생성자 함수

- 함수 표현식으로 함수를 정의할 때 함수 리터럴 방식을 사용한다. 함수 선언문도 내부적으로 자바스크립트 엔진이 기명 함수 표현식으로 변환하므로 결국 함수 리터럴 방식을 사용한다.
- 따라서 **함수 선언문과 함수 표현식은 모두 함수 리터럴 방식으로 함수를 정의하는데 이것은 결국 내장 함수 Function 생성자 함수로 함수를 생성하는 것을 단순화시킨 short-hand(축약법)이다.**
- Function 생성자 함수는 Function.prototype.constructor 프로퍼티로 접근할 수 있다.

    new Function(arg1, arg2, ... argN, functionBody)
    
    var square = new Function('number', 'return number * number');
    console.log(square(10)); // 100

## 함수 호이스팅

    var res = square(3);
    
    function square(number){
    	return number * number;
    }

- 함수 선언문으로 함수가 정의되기 이 전에 함수 호출이 가능
- 함수 선언문의 경우, 함수 선언의 위치와 관계없이 코드 내 어느 곳에서든지 호출이 가능한데, 이것을 함수 호이스팅이라 한다.
- JS는 ES6의 let,const를 포함하여 모든 선언 (var, let, const, function, function*, class)을 호이스팅 한다.
- **호이스팅이란, var 선언문이나 function 선언문 등 모든 선언문이 해당 Scope의 선두로 옮겨진 것처럼 동작하는 특성을 말한다.**
- **즉, JS는 모든 선언문(var, let, const, function, function*, class) 이 선언되기 이 전에 참조가 가능하다.**
    - 함수 선언문으로 정의된 함수는 자바스크립트 엔진이 스크립트가 로딩되는 시점에 바로 초기화 하고, 이를 VO(variable object)에 저장한다. 즉, 함수 선언, 초기화, 할당이 한번에 이루어진다. 그렇기 때문에 함수 선언의 위치와는 상관없이 소스 내 어느 곳에서든지 호출이 가능하다.

    var res = square(5); // TypeError: square is not a function
    
    var square = function(number) {
      return number * number;
    }

- 함수 선언문과 달리 함수 표현식의 경우, 함수 호이스팅이 아니라, 변수 호이스팅이 발생한다.
- **변수 호이스팅은 변수 생성 및 초기화와 할당이 분리되어 진행된다.**
- **호이스팅 된 변수는 undefined로 초기화 되고 실제 값의 할당은 할당 문에서 이루어진다.**
- 함수 표현식은 함수 선언문과는 달리 스크립트 로딩 시점에 변수 객체(VO)에 함수를 할당하지 않고 runtime에 해석되고 실행되므로 이 두가지를 구분하는 것은 중요하다.

## First-class object(일급 객체)

- 일급 객체란 생성, 대입, 연산, 인자 또는 반환값으로서의 전달 등 프로그래밍 언어의 기본적 조작을 제한없이 사용할 수 있는 대상을 의미한다.
- 다음 조건을 만족하면 일급 객체로 간주한다.

> 1. 무명의 리터럴로 표현이 가능하다.
2. 변수나 자료 구조(객체, 배열 등)에 저장할 수 있다.
3. 함수의 매개변수에 전달할 수 있다.
4. 반환값으로 사용할 수 있다.

    // 1. 무명의 리터럴로 표현이 가능하다.
    // 2. 변수나 자료 구조에 저장할 수 있다.
    var increase = function (num) {
    	return ++num;
    }
    
    var decrease = function (num) {
    	return --num;
    }
    
    var predicates = { increase, decrease };
    
    // 3. 함수의 매개변수에 전달할 수 있다.
    // 4. 반환값으로 사용할 수 있다.
    function makeCounter(predicates) {
    	var num = 0;
    	
    	return function( ) {
    		num = predicates(num);
    		return num;
    	}
    }
    
    var increaser = makeCounter(predicates.increase);
    console.log(increaser()); // 1
    console.log(increaser()); // 2
    
    var decreaser = makeCounter(predicates.decrease);
    console.log(decreaser()); // -1
    console.log(decreaser()); // -2

- Javascript의 함수는 위의 조건을 모두 만족하므로 **Javascript의 함수는 일급객체이다.** 따라서 Javascript의 함수는 흡사 변수와 같이 사용할 수 있으며 코드의 어디에서든지 정의할 수 있다.
- **함수와 다른 객체를 구분짓는 특징은 호출할 수 있다는 것이다.**

## 매개변수(Parameter, 인자)

- 함수의 작업 실행을 위해 추가적인 정보가 필요한 경우, 매개변수를 지정한다.
- 매개 변수는 함수 내에서 변수와 동일하게 동작한다.

### 매개변수(parameter, 인자) vs 인수(argument)

- 매개변수는 함수 내에서 변수와 동일하게 메모리 공간을 확보하며, 함수에 전달한 인수는 매개변수에 할당된다.
- 만약 인수를 전달하지 않으면 매개변수는 undefined로 초기화된다.

    var foo = function(p1, p2){
    	console.log(p1, p2);
    }
    
    foo(1); // 1 undefined

### call by value

- 원시 타입 인수는 Call-by-value(값에 의한 호출)로 동작한다.
- 이는 함수 호출 시 원시 타입 인수를 함수에 매개변수로 전달할 때 매개변수에 값을 복사하여 함수로 전달하는 방식이다.
- 이 때 함수 내에서 매개변수를 통해 값이 변경되어도 전달이 완료된 원시 타입 값은 변경되지 않는다.

    function foo(primitive){
    	primitive += 1;
    	return primitive;
    }
    
    var x = 0;
    
    console.log(foo(x)); //1
    console.log(x); //0

### call by reference

- 객체형(참조형) 인수는 Call-by-reference(참조에 의한 호출)로 동작한다.
- 이는 함수 호출 시 참조 타입 인수를 함수에 매개변수로 전달할 때 매개변수에 값이 복사되지 않고 객체의 참조값이 매개변수에 저장되어 함수로 전달되는 방식이다.
- 이 때 함수 내에서 매개변수의 참조값이 이용하여 객체의 값을 변경했을 때 전달되어 진 참조형의 인수 값도 같이 변경된다.

    function changeVal(primitive, obj){
    	primitive += 100;
    	obj.name = 'Kim';
    	obj.gender = 'female';
    
    var num = 100;
    var obj = {
    	name: 'Lee',
    	gender: 'male'
    };
    
    console.log(num); // 100
    console.log(obj); // Object {name: 'Lee', gender: 'male'}
    
    changeVal(num, obj);
    
    console.log(num); // 100
    console.log(obj); // Object {name: 'Kim', gender: 'female'}

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1a02292a-6c43-4531-8797-4134682c2e3b/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1a02292a-6c43-4531-8797-4134682c2e3b/Untitled.png)

- changeVal 함수는 원시 타입과 객체 타입 인수를 전달 받아 함수 몸체에서 매개변수의 값을 변경하였다. 이때 원시 타입 인수는 값을 복사하여 매개변수에 전달하기 때문에 함수 몸체에서 그 값을 변경하여도 어떠한 부수 효과(side-effect)도 발생시키지 않는다.
- 하지만 객체형 인수는 참조값을 매개변수에 전달하기 때문에 함수 몸체에서 그 값을 변경할 경우 원본 객체가 변경되는 부수 효과(side-effect)가 발생한다. 이와 같이 부수 효과를 발생시키는 비순수 함수(Impure function)는 복잡성을 증가시킨다. 비순수 함수를 최대한 줄이는 것은 부수 효과를 최대한 억제하는 것과 같다. 이것은 디버깅을 쉽게 만든다.
- 어떤 외부 상태도 변경하지 않는 함수를 순수함수(Pure function), 외부 상태도 변경시켜는 부수 효과(side-effect)가 발생시키는 함수를 비순수 함수(Impure function)라 한다.

- 참고
    - [https://poiemaweb.com/js-function](https://poiemaweb.com/js-function)
