# Immutablity

- 객체가 생성된 이 후 그 상태를 변경할 수 없는 디자인 패턴을 의미한다.
- 객체는 참조 형태로 전달하고 전달 받는다. 객체가 참조를 통해 공유되어 있다면 그 상태가 언제든지 변경될 수 있기 때문에 문제가 될 가능성도 커지게 된다.

### immutable value vs mutable value

- **js의 원시 타입 (primitive data type)은 변경 불가능한 값(immutable value)이다.**
```
    Boolean
    null
    undefined
    Number
    String
    Symbol
```
- 원시 타입 이외의 모든 값은 객체(Object) 이며 객체 타입은 변경 가능한 값이다.
    - 즉, 객체는 새로운 값을 다시 만들 필요없이 직접 변경이 가능하다.
```
    var str = "Hello",
    str = "world"
```
- 첫번째 구문이 실행되면 메모리에 문자열 'Hello'가 생성되고, 식별자 str은 메모리에 생성된 문자열 'Hello' 메모리 주소를 가리킨다.
- 그리고 두번째 구문이 실행되면, 이 전에 생성된 문자열 'Hello'을 수정하는 것이 아니라 새로운 문자열 'world'를 메모리에 생성하고, 식별자 str은 이것을 가리킨다.
- 이 때 문자열 'Hello'와 'world'는 모두 메모리에 존재하고 있다.
- 변수 str은 문자열 'Hello'를 가리키고 있다가 문자열 'world'를 가리키도록 변경 되었을 뿐이다.

```
    var arr = [];
    console.log(arr.length); // 0
    
    var v2 = arr.push(2); // arr.puss() 는 메소드 실행 후 arr의 length를 반환
    console.log(arr.length); // 1
```

- v2 값은 무엇인가? 문자열의 예제와 같이 배열이 동작한다면, vs는 새로운 배열 (하나의 요소를 가지고 그 값은 2인)을 가지게 될 것이다.
- 그러나 객체인 arr은 push 메소드에 의해 update되고, v2에는 배열의 새로운 length값이 반환된다.
- 처리 후 결과의 복사본을 리턴하는 문자열의 메소드 slice()와 달리 배열의 메소드 push는 직접 대상 배열을 변경한다.
- 그 이유는 객체이고 객체는 immutable value가 아닌, 변경 가능한 값이기 때문이다.
```
    var user = {
      name: 'Lee',
      address: {
        city: 'Seoul'
      }
    };
    
    var myName = user.name; // 변수 myName은 string 타입이다.
    
    user.name = 'Kim';
    console.log(myName); // Lee
    
    myName = user.name;  // 재할당
    console.log(myName); // Kim
```
- user.name의 값을 변경했지만 변수 myName 값은 변경되지 않았다.
- 변수 myName에 user.name을 할당 했을 때, user.name의 참조를 할당하는 것이 아니라, immutable한 값 'Lee'가 메모리에 새로 생성되고, myName은 이것을 참조하기 때문이다.

- 따라서 user.name의 값이 변경된다 하더라도, 변수 myName이 참조하고 있는 'Lee'는 변함이 없다.

## 불변 데이터 패턴 (immutable data pattern)

- 의도하지 않은 객체의 변경이 발생하는 원인의 대다수는 "레퍼런스를 참조한 다른 객체에서 객체를 변경" 하기 때문이다.
- 이 문제의 해결 방법은 비용은 조금 들지만 객체를 불변객체로 만들어 property의 변경을 방지하며, 객체의 변경이 필요한 경우에는 참조가 아닌 객체의 방어적 복사를 통해 새로운 객체를 생성한 후 변경한다.
    - 객체의 방어적 복사
        - Object.assign
    - 불변객체화를 통한 객체 변경 방지
        - Object.freeze

### Object.assign

- 타깃 객체로 소스 객체의 프로퍼티를 복사한다.
- 이 때 소스 객체의 프로퍼티와 동일한 프로퍼티를 가진 타겟 객체의 프로퍼티들은 소스 객체의 프로퍼티로 덮어쓰기 된다.
- 리턴 값으로 타깃 객체를 반환한다.
- ES6에 추가된 메소드이며, IE는 지원하지 않는다.
```
    // Syntax
    Object.assign(target, ...sources)
    
    //Copy
    const obj = { a : 1 };
    const copy = Object.assign({}, obj);
    
    console.log(copy); // { a : 1 }
    console.log(obj === copy) // false
    
    //merge
    const o1={a:1};
    const o2={b:2};
    const o3={c:3};
    
    const merge1 = Object.assign(o1,o2,o3);
    
    console.log(merge1); // { a:1, b:2, c:3 }
    console.log(o1); // { a:1, b:2, c:3 }, 타깃 객체가 변경 된다.
    
    // Merge
    const o4 = { a: 1 };
    const o5 = { b: 2 };
    const o6 = { c: 3 };
    
    const merge2 = Object.assign({}, o4, o5, o6);
    
    console.log(merge2); // { a: 1, b: 2, c: 3 }
    console.log(o4);     // { a: 1 }
```
- Object.assign 을 사용해서 기존 객체를 변경하지 않고, 객체를 복사해서 사용할 수 있다.
- Object.assign 은 완전한 deep copy를 지원하지 않는다.
- 객체 내부의 객체 (Nested Object)는 Shallow copy 된다.
```
    const user1  = {
    	name: 'Lee',
    	address: {
    		city: 'Seoul'
    	}
    };
    
    //새로운 빈 객체에 user1을 copy 한다.
    const user2 = Object.assign({}, user1);
    
    //user1과 user2는 참조값이 다르다.
    console.log(user1 === user2); // false
    
    user2.name = 'Kim'
    console.log(user1.name); // Lee
    console.log(user2.name); //Kim
    
    //객체 내부의 객체 (Nested Object)는 Shallow copy 된다.
    console.log(user1.address === user2.address); // true
    
    user1.address.city = 'Busan';
    console.log(user1.address.city); // Busan
    console.log(user2.address.city); // Busan
```
- user1 객체를 빈객체에 복사하여 새로운 객체 user2를 생성하였다.
- user1과 user2는 address를 공유하지 않으므로, 한 객체를 변경하여도 다른 객체에 아무런 영향을 w주지 않는다.

### Object.freeze

- Object.freeze를 사용해서 불변객체(immutable)로 만들 수 있다.
```
    const user1 = {
    	name: 'Lee',
    	address: {
    		city: 'seoul'
    	}
    };
    
    //Object.assign 은 완전한 deep copy를 지원하지 않는다.
    const user2 = Object.assign({}, user1, {name: 'Kim'})
    
    console.log(user1.name); // Lee
    console.log(user2.name); // Kim
    
    Object.freeze(user1);
    
    user1.name = 'Kim' ;//무시된다
    
    console.log(user1); // { name: 'Lee, address: {city: 'seoul'}}
    
    console.log(Object.inFrozen(user1)); // true
    
    // 객체 내부의 객체(Nested Object)는 변경이 가능하다.
    
    const user = {
      name: 'Lee',
      address: {
        city: 'Seoul'
      }
    };
    
    Object.freeze(user);
    
    user.address.city = 'Busan'; // 변경된다!
    console.log(user); // { name: 'Lee', address: { city: 'Busan' } }
```
- 내부 객체까지 변경 불가능 하게 만들려면 Deep Freeze를 해야한다.
```
    function deepFreeze(obj){
    	const props = Object.getOwunPropertyNames(obj);
    
    	props.forEach(name) => {
    		const props = obj[name];
    		if(typeof prop === 'object' && prop !== null){
    			deepFreeze(prop);
    		}
    	});
    	return Object.freeze(obj);
    }
    
    const user = {
      name: 'Lee',
      address: {
        city: 'Seoul'
      }
    };
    
    deepFreeze(user);
    
    user.name = 'Kim';           // 무시된다
    user.address.city = 'Busan'; // 무시된다
    
    console.log(user); // { name: 'Lee', address: { city: 'Seoul' } }
```