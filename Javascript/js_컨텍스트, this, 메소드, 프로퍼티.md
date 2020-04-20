## EXECUTION CONTEXT = 실행 컨텍스트 

* 자바스크립트가 실행될 때, 생성되는 실행 단위이다.

* 자바스크립트의 경우, 함수를 실행하면 함수들이 차곡차곡 stack이란 곳에 쌓이는데,
    실행 컨텍스트는 callstack에 쌓이는 하나하나의 실행 정보이다.

* scope, hoisting, this, function, closure 등의 동작 원리를 담고있는 자바스크립트의 핵심 원리이다. 

* 실행 가능한 코드를 형상화하고 구분하는 추상적인 개념으로, 실행 가능한 코드가 실행되기 위해 필요한 환경이라고 말할 수 있다.

    1. 전역 코드 : 전역 영역에 존재하는 코드
    
    2. Eval 코드 : eval 함수로 실행되는 코드
    
    3. 함수 코드 : 함수 내에 존재하는 코드
    
* 어떤 함수가 호출되면, 실행 컨텍스트가 생성된다.

    1. call stack에 push
    
    2. 함수를 벗어나면 call stack에서 pop

    - call stack : 콘솔창 - source - call stack에 들어가면 어디서부터 에러가 났는지, 어디서부터 시작된건지 내용을 쭉 볼 수 있다.    
    
    3. 함수가 실행될 때 마다 생성이 된다. (scope 별로 생성이 된다) 
    
    4. 실행 컨텍스트에 담기는것
    
    -  scope 내에 변수 및 함수 (local, global)
    
    - 전달 인자(argument - parameter로 받는 값)
    
    - 호출된 근원(caller) 

* 다시 정리

    1. 함수 실행 시, 가장 처음으로 전역 컨텍스트를 생성시킨다. 
    
    2. 함수가 호출될 때마다 해당 함수의 컨텍스트들이 만들어진다.
    
    3. 실행컨텍스트 생성 시 컨텍스트 안에 변수객체(argument, variable), scope chain, this 가 생성이 된다.
    
    4. 실행컨텍스트 생성 후 함수가 실행 된다. 
    
    5. 사용되는 변수들은 활성객체 안에서 값을 찾고, 없다면 스코프 체인을 따라 올라가면서 찾는다. 없으면 에러가 뜬다.
    
    6. 함수 실행이 마무리 되면, 해당 컨텍스트는 사라진다.
    
    7. 페이지가 종료되면 전역 컨텍스트가 사라진다.
    
    
## THIS
    
* 모든 함수 scope 내에서 자동으로 설정되는 특수한 식별자 

* execution context의 구성 요소중 하나로, 함수가 실행되는 동안만 이용할 수 있다.

#### this의 다섯가지 패턴 - 어떤 경우에 어떤 식으로 this를 할당하는가? (binding)

##### 1. global reference --> window = this

- window : 전역 영역을 대표하는 객체(전역객체 안에서 전역변수들이 자동적으로 담긴다.)

- 변수 안에서의 this = window

        var name = "global vari";
        console.log(this.name)
        // global vari
            
##### 2.  free function invocation (함수 실행) --> window = this

- 함수가 실행되는 동시에 this가 생성된다.

- 함수 안에서의 this = window

        function foo (){
            console.log(this.name);
        }
        // global vari
            
##### 3. METHOD invocation (호출)  --> 부모 object = this
    
- 객체 안에서 불려지는 function

        var counter = {
        
            val : 0;
            
            increment : function(){
            
                    this.val += 1;
                    
                    //부모 object --> counter = this
                    
                    }
                    
            }
            
            counter.increment(); 
            console.log(counter.val); // 1 
            counter.['increment']();
            console.log(counter.val); //2
            
        var obj = {
        
            fn : function (a,b){
            
                return this;
            
        };
            
        var obj2 = {
        
            method : obj.fn;
            
        };
        
        console.log( obj2.method() === obj2 );
         //true
        
        console.log( obj.fn() === obj );
         //true
        
        
                
##### 4. construction mode(new 연산자로 생성된 function 영역의 this) --> 새로 생성된 객체 = this

- 객체 지향 프로그래밍

        function F(v){
        
            this.val = v;
            
        }
        
        //create new instance of F
        
        var f = new F('wooHoo!');
        
        console.log(f.val); 
        // wooHoo!
        
        console.log(val);
        //ReferenceError

        function Car(brand, name, color){
        
            this.brand = brand;
            
            this.name = name;
            
            this.color = color;
            
        }
        
        var avante = new Car("현대","아반뗴","gray");
        var bmw = new Car("bmw", "b021", "silver");
        
        A. 자동차 유형을 대표하는 클래스 Car를 만들었다. (함수명은 대문자로 시작한다.)
        
        B. avante / bmw 는 instance(인스턴스) 라고 부른다. 
        
        C. avante.name // "아반뗴" , avante.brand // "현대"
        
        D. 클래스 기반으로 new 연산자를 생성하여, 각각 고유의 성질을 가진 그룹을 만든 것을 INSTANCE 라고 한다.
        
        E. 여기서 this 는 avante가 된다. --> 인스턴스의 객체
            
            
##### 5. call or apply invocation (call / apply 실행) --> 첫번째 인자(argument) 로 명시된 객체 = this

### call / apply 

- Function.prototype.call

    - function.call(thisArg, arg1, arg2 ...)
    
- Function.prototype.apply

    - function.apply(thisArg, arg1, arg2 ...)


- 예제 (call)

        function makePara(){
        
            return Array.prototype.slice.call(arguments);
            
        }
        
        console.log(makePara('code','states');
        
        // ['code', 'ststes']
                
- 예제 2 (call)

        function getMax(){
        
            var argArray = Array.prototype.slice.call(arguments);
            
            var maxValue = argArray.reduce(function( accumulator , currentValue){
            
                    return (accumulator > currentValue) ? accumulator : currentValue;
                    
            
        }}
        
        console.log(getMax(1,3,5,6,4);
        
        
- 예제 3

        var add = function (x,y) {
        
            this.val = x + y;
            
        }
        
        var obj = {
        
            val : 0
            
        };
        
        add.apply(obj. [2, 8] );
        
        console.log(obj.val);
        //10
        
        add.call(obj, 2, 9);
        
        console.log(obj.val);
        //11
            
- 예시 4

        function add(x,y){
            
            return x + y;
            
        }
        
        * 함수 호출하기
        
        1. add(5,4);
        
        2. add.call(null, 4, 5); --> call : 인자를 일열로 나열한다.
        
        3. add.apply(null, [4, 5] --> apply : 인자를 배열로 나열한다.
        
        -- null : 지정할 this의 값
        
- 예시5
    
        function identify(){
        
            return.this.name.toUpperCase();
            
        }
        
        function speack(){
        
            var greeting = "hello i'm " + identify.call(this);
            
            console.log(greeting);
            
        }      
        
        var me = {name : "oh"};
        
        var you = {name : "wang"};
        
        identify.call(me); 
       //OH
       
       identify.call(you);
       //WANG 
       
       speak.call(me);
       // hello i'm OH
       
       speak.call(you);
       //hello i'm WANG
       
- 예제 6

        var obj = {
        
            string : 'origin',
            
            foo : function (){
            
                console.log(this.string);
                
                }
                
            };
            
        var obj2 = {
        
            string: 'what?';
            
        }
        
        obj.foo();
        //'origin'
        
        obj.foo.call(obj2);
        //'what?'
            
- 예제 7 (apply)

    var min = Math.min(7,35,2,8,21);
    console.log(min);
    //2
    
    var arr = [7,35,2,8,21];
    var min2 = Math.min.apply(null, arr);
    
    console.log(min2);
    //2
            
### BIND

- 인자로 넘겨준 객체와 연결(bind)된 새로운 함수를 반환한다.

- callback 함수를 특정 객체와 연결하고 싶을 때 사용한다.

        fn.bind(thisArg, [, arg1[, arg2[, ...]]])
        
- 예시 1

        function foo(){
        
            return this;
            
        }
        
        var boundFoo = foo.bind({a : 1});
        foo();
        //window
        
        boundFoo();
        //{a : 1} 
       
- 예시 2

        function Box(w, h){
        
            this.width = w;
            this.height = h;
            
            this.getArea = function(){
            
                return this.width * this.height;
                
            }
            
            this.printArea = function(){
            
                console.log(this.getArea());
                
            } 
            
            this.printArea();
            setTimeout(this.pringArea.bind(this), 2000);
            
            }
            
            var b = new Box(100, 50);
        
- 예시 3

        function template(name, money){
        
            return '<h1>' + name + '</h1><span>' + money + "</span>" ;
            
        }
        
        var templIngi = template.bind(null, 'Ingi kim');
        
        var tempMin = template.bind(null, 'oh'); 
            
            
## METHOD
    
* Array.somethingMethod()

    - Array CLASS에서만 작동하는 메소드 !!!
    
    - CLASS 자체에 내장되어 있는 메소드 !!! 

* Array.prototype.somethingMethod()

    - Array 인스턴스에서만 작동하는 메소드!!!
    
    - 인스턴스가 사용할 수 있는 메소드로, 프로토타입 메소드라고 한다!!! 
    
            var arr = [1,2,3,4]; // arr is an instance of Array
            // same as
            var arr = new Array(1,2,3,4);

## PROTOTYPE
    
* 인스턴스가 생성이(INSTANTIATION) 될 때, 원형(original form), 즉 프로토타입의 모양대로 인스턴스가 생성이 된다.

* 인스턴스의 메소드는 object.prototype.sometingMethod.로 표현한다.

    - prototype === 원형

## CLASS keyword

- class 정의 

    - class 선언
            
            class Polygon{
                constructor(height,width){
                    this.height = height;
                    this.width = width;
                }
            }
- class 와 함수 선언(function) 의 큰 차이

    - 함수 선언 : 호이스팅이 발생하여 함수 선언 시, 상위로 호이스팅 된다.

    - class : 호이스팅이 일어나지 않아서, class를 먼저 선언해야 하며, 그렇지 않으면 ReferenceError를 발생

- class 표현식

    - class를 정의하는 또 다른 방법으로, 이름을 가질수도 있고 갖지 않을수도 있다.

            //unnamed
            var Polygon = class {
                constructor(height,width){
                    this.height = height;
                    this.width = width;
                }
            }

            //named
            var polygon = class Polygon{
                constructor(height,widht){
                    this.height = height;
                    this.width = width;
                }
            }

- Strict mode 
    
    - 클래스 선언과 클래스 표현식의 본분(body)은 strict mode에서 실행된다.

    - 스크립트의 시작 혹은 함수의 시작 부분에 "use strict"를 선언하면 strict 모드로 작성할 수 있다.

            //스크립트에서 strict 선언
            "use strict"
            var v = "HI ! ";

            //함수에서 strict 선언
            function strict(){
                'ust strict'
                function nested(){return "and so am i"};
                return "hi! i'm strict mode" + nested();
            }
            function notStrict(){ return "i'm not strict"};

    - strict 모드는 문법과 런타임 동작을 모두 검사하여, 실수를 에러로 변환하고, 변수 사용을 단순화 시켜준다.

- constructor ? 

    - class로 생성된 객체를 생성하고, 초기화하기 위한 특수한 METHOD

    - constructor 메소드는 클래스 안에 한 개만 존재할 수 있고, 그렇지 않으면 syntaxError가 발생한다.

    - constructor는 부모 클래스의 constructor를 호출하기 위해 super 키워드를 사용할 수 있다.

- super? 

    - 객체의 부모가 가지고 있는 함수들을 호출하기 위해 사용된다.

            // Class(ES6)
            class Cat{
                constructor (name){
                    this.name = name;
                }

                speak(){
                    console.log(this.name + "make a noise");
                }
            }

            class Lion extends Cat {
                speak(){
                    super.speak();
                    console.log(this.name + "roars.");
                }
            }

            //function (ES5)
            function Cat(name){
                this.name = name;
            }
            Cat.prototype.speak = function(){
                console.log(this.name + "make a noise");
            }

            function Lion(name){
                //super() 호출
                Cat.call(this, name);
            }

            //`Cat`클래스 상속
            Lion.prototype = Object.create(Cat.prototype);
            Lion.prototype.constructor = Lion;
            
            // `speak()` 메서드 오버라이드
            Lion.prototype.speak = function () {
            Cat.prototype.speak.call(this);
            console.log(this.name + ' roars.');
            };

- static methods (new 연산자를 통해서 생성된 )

    - static 키워드는 class를 위한 정적(static) 메소드를 정의한다. 정적 메소드는 클래스의 인스턴스화 없이 호출되며, 클래스의 인스턴스에서는 호출할 수 없다. 정적 메소드는 어플리케이션을 위한 유틸리티 함수를 생성하는데 주로 사용된다.

            class Point{
                constructor(x,y){
                    this.x = x;
                    this.y = y
                }

                static distance(a,b){
                    const dx = a.x - b.x;
                    const dy = a.y - b.y;

                    return Math.sqrt(dx*dx + dy*dy);
                }
            }
            const p1 = new Point(5,5);
            const p2 = new Point(10,10);

            console.log(Point.distance(p1,p2));
            
- extends를 통한 클래스 상속

    - 클래스 선언이나 클래스 표현식에서, 다른 클래스의 자식 클래스를 생성하기 위해 사용된다.

            class Animal{
                constructor(name){
                    this.name = name;
                }

                speak(){
                    console.log(this.name + "makes a noise");
                }
            }

            class Dog extends Animal {
                speak(){
                    console.log(this.name + "barks.");
                }
            }

            // function 함수에서 사용하는 방법
                function Animal (name) {
                this.name = name;  
                }
                Animal.prototype.speak = function () {
                console.log(this.name + ' makes a noise.');
                }

                class Dog extends Animal {
                speak() {
                    console.log(this.name + ' barks.');
                }
                }

                var d = new Dog('Mitzie');
                d.speak();

