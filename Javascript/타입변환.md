## 타입 변환?

- 개발자에 의해 의도적으로 값의 타입을 변환하는 것을 명시적 타입 변환(Explicit coercion) / 타입 캐스팅(Type casting) 이라고 한다.
```
    let x = 10;
    
    //명시적 타입 변환
    let str = x.toString(); // 숫자 -> 문자열로 타입 캐스팅
    console.log(typeof str); // string
```
- 동적 타입 언어인 JS는 자바스크립트 엔진에 의해 암묵적으로 타입이 자동 변환 되기도 한다. 이를 암묵적 타입 변환 (Impolicit coercion) 또는 타입 강제 변환 (Type coercion)이라고 한다.
```
    let x= 10;
    
    // 암묵적 타입 변환
    // 숫자 타입 x의 값을 바탕으로 새로운 문자열 타입의 값을 생성해 표현식을 평가한다.
    let str = x + '';
    console.log(typeof str, str); // string 10
```

## 암묵적 타입 변환

- 자바스크립트 엔진은 표현식을 평가할 때 문맥, 즉 컨텍스트(Context)에 고려하여 암묵적 타입 변환을 실행한다.
```
    //표현식이 모두 문자열 타입이어야 하는 컨텍스트
    '10' + 2 // '102'
    `1 * 10 = ${1 * 10}`// 1 * 10 = 10
    //표현식이 모두 숫자 타입이어야 하는 컨텍스트
    5 * '10' // 50
    // 표현식이 불리언 타입이어야 하는 컨텍스트 
    !0 // true
    if(1) { }
```
- 암묵적 타입이 발생하면 문자열, 숫자, 불리언과 같은 원시 타입 중 하나로 타입을 자동 변환한다. 타입별로 암묵적 타입 변환이 어떻게 발생할까?

### 문자열 타입으로 변환
```
    1 + '2' // 12
```
- 문자열 연결 연산자의 피연산자는 문맥, 즉 컨텍스트 상 문자열 타입이여야 한다.

### 숫자 타입으로 변환
```
    1 - '1'    // 0
    1 * '10'   // 10
    1 / 'one'  // NaN
```
- 산술 연산자의 피 연산자는 문맥, 즉 컨텍스트 상 숫자 타입이여야 한다.

### 불리언 타입으로 변환
```
    if ('') console.log(x);
```
- 자바스크립트 엔진은 제어문의 조건식을 평가 결과를 불리언 타입으로 암묵적 타입 변환한다.
- 아래 값들은 제어문의 조건식과 같은 불리언 값으로 평가되어야 할 컨텍스트에서 false로 평가되는 falsy 값이다.
```
    false
    undefined
    null
    0, -0
    NaN
    ’’ (빈문자열)
```
- Falsy 값 이외의 값은 제어문의 조건식과 같이 불리언 값으로 평가되어야 할 컨텍스트에서 모두 true로 평가되는 Truthy 값이다.

## 명시적 타입 변환

### 문자열 타입으로 변환

1. String 생성자 함수를 new 연산자 없이 호출하는 방법
2. Obejct.prototype.toString 메소드를 사용하는 방법
3. 문자열 연결 연산자를 이용하는 방법
```
    // 1. String 생성자 함수를 new 연산자 없이 호출하는 방법
    // 숫자 > 문자 type
    console.log(String(1)); //"1"
    console.log(String(NaN)); //"NaN"
    console.log(String(Infinity)); //"Infinity"
    // 불리언 > 문자 type
    console.log(String(true)); //"true"
    
    // 2. Object.prototype.toString 메소드를 사용하는 방법
    console.log((1).toString()); //"1"
    console.log((NaN).toString()); //"NaN"
    console.log((Infinity).toString); //"Infinity"
    // 불리언 > 문자 type
    console.log((false).toString) //"false"
    
    // 3. 문자열 연결 연산자를 이용하는 방법
    // 숫자 > 문자 type
    console.log(1 + ''); // "1"
    console.log(NaN + ''); // "NaN"
    console.log(Infinity + ''); // "Infinity"
    // 불리언 > 문자 type
    console.log(true + ''); //"true"
```
### 숫자 타입으로 변환

1. Number 생성자 함수를 new 연산자 없이 호출하는 방법
2. parseInt, parseFloat 함수를 사용하는 방법(문자열만 변환 가능)
3. . 단항 연결 연산자를 이용하는 방법
4. . 산술 연산자를 이용하는 방법
```
    // 1. Number 생성자 함수를 new 연산자 없이 호출하는 방법
    // 문자 > 숫자 type
    console.log(Number('0')) // 0
    console.log(Number('-1')) // -1
    console.log(Number('10.53')) // 10.53
    // 불리언 > 숫자 type
    console.log(Number('true')) // 1
    console.log(Number('false')) // 0
    
    // 2. parseInt, parseFloat 함수를 사용하는 방법 (문자열만 변환 가능)
    console.log(parseInt('0')); //0
    console.log(parseInt('-1')); //-1
    console.log(parseFloat('10.53')); //10.53
    
    // 3. + 단항 연결 연산자를 이용하는 방법
    console.log(+'0');     // 0
    console.log(+'-1');    // -1
    console.log(+'10.53'); // 10.53
    // 불리언 타입 => 숫자 타입
    console.log(+true);    // 1
    console.log(+false);   // 0
    
    // 4. * 산술 연산자를 이용하는 방법
    // 문자열 타입 => 숫자 타입
    console.log('0' * 1);     // 0
    console.log('-1' * 1);    // -1
    console.log('10.53' * 1); // 10.53
    // 불리언 타입 => 숫자 타입
    console.log(true * 1);    // 1
    console.log(false * 1);   // 0
```
### 불리언 타입으로 변환
```
1. Boolean 생성자 함수를 new 연산자 없이 호출하는 방법
2. ! 부정 논리 연산자를 두 번 사용하는 방법

    //1. Boolean 생성자 함수를 new 연산자 없이 호출하는 방법
    // 문자 > 불리언 type
    console.log(Boolean('x')) // true
    console.log(Boolean('')) // false
    console.log(Boolean('false')); // true
    
    //숫자 > 불리언 type
    console.log(Boolean(0)); // false
    console.log(Boolean(1)); // true
    console.log(Boolean(NaN)); // false
    console.log(Boolean(Infinity)); // true
    
    // null > 불리언 type
    console.log(Boolean(null)); // false
    
    // undefined > 불리언 type 
    console.log(Boolean(undefined)); // false
    
    // 객체 > 불리언 type
    console.log(Boolean({})); // true
    console.log(Boolean[]); // true
    
    //2. ! 부정 논리 연산자를 두 번 사용하는 방법
    // 문자 > 불리언 type
    console.log(!!'x');       // true
    console.log(!!'');        // false
    console.log(!!'false');   // true
    
    // 숫자 타입 => 불리언 타입
    console.log(!!0);         // false
    console.log(!!1);         // true
    console.log(!!NaN);       // false
    console.log(!!Infinity);  // true
    
    // null 타입 => 불리언 타입
    console.log(!!null);      // false
    
    // undefined 타입 => 불리언 타입
    console.log(!!undefined); // false
    
    // 객체 타입 => 불리언 타입
    console.log(!!{});        // true
    console.log(!![]);        // true
```