## Array, Function, Obeject

### Array (mutable - 값이 바뀔 수 있다.)

- Object의 배열

- 배열의 길이 

            arr.length;

- 배열의 마지막 원소 불러오기

            arr[arr.length - 1 ];

### String (Immutable - 값이 절대 바뀌지 않으므로 새로운 변수를 선언하여 등록한다.)

- 문자열 String은 배열과 유사한, 유사 배열이다.

### Function 

- 입력과 출력이 있는 형태로, 매개변수 -> 처리 -> return 값 출력의 형태를 가진다.

- return 값이 있는 경우, 함수를 호출해서 변수에 값을 넣을 수 있다.

            var foo = function(hello){
                return "hello"
            }

            var a = foo();
            // "hello"

- 반면 return 값이 없는 경우, 변수에 값을 넣어주고 출력하면 undefined로 출력된다.

            var foo = function(hello){
                console.log("hello");
            }

            var a = foo();
            // undefined

### Object

- 변수와 함수를 묶어서 관리하는 개념으로, Property(속성) 와 Method(명령)을 가질 수 있다.

- 객체 지향 프로그래밍

    - 유지보수가 쉬워진다.

    - 가독성이 높아진다.

    - 대형 프로젝트 할 때 좋다.

            var foo = { }

            foo.name = "oh minyound";
            foo.weight = 100;
            foo.eat = function(food){
                console.log(this.name + "이 " + food + "를 먹었습니다.");
                foo.weight += 5;
            }

            foo.eat("치킨");

- this

    - 객체의 메소드 안에서 사용시, 함수를 소유한 객체를 가르킨다.

### 객체 만들기 - JSON 표기법 

- JavaScript Object Notation

### 객체 만들기 - 생성자 함수 

