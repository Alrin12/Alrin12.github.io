---
layout: post
title: "Learning ECMAScript"
description: Lorem ipsum dolor sit amet, consectetur adipisicing elit.
image: 'http://res.cloudinary.com/dm7h7e8xj/image/upload/c_scale,w_760/v1504807239/morpheus_xdzgg1.jpg'
category: 'blog'
---
# Data type
- Primitive Data Type
    - Boolean
        - 부울이라는 사람이 고안한 대수 체계로, 컴퓨터에서는 연산의 값이 두개의 상태(True, False)로 귀결되는 것을 표현한 것이다.
        조건에 의한 분기 또는 반복문을 만들 때 유용하게 사용된다.
    - Number
        - 숫자 자료형으로 정수(Integer)와 실수(float)를 표현한다.
    - String
        - 문자 자료형으로 문자를 표현하며, Number자료형 간 형 변환도 가능하다.
    - null
        - 존재하지 않는 메모리 주소를 의미한다. 주로 메모리가 할당되기 전 초기화를 하기 위해 사용하였는데, 현재에는 큰 의미가 없기에 null 자체를 배제하는 움직임이 있다. 심지어 null reference를 만든 사람이 null을 만든것은 실수였다고 말하기까지 했다.
    - undefined
        - 변수에 자동적으로 할당되는 초기값으로 말 그대로 '아무것도 할당되지 않았을 때' 변수에 자동적으로 할당되는 기본값이다.
    - symbol
        -   ECMAScript6에서 등장한 기본 자료형으로, html의 <id>태그 같은 존재이다. 즉, 전체 구문에서 재사용되지 않을(또는 않아야 할)것들을 표현할 때 사용된다.
- Object
    - 위에서 언급한 기본 자료형을 제외한 모든 것들을 나타낸다.

# 변수(Variable)
변수란 사람이 이해할 수 있는 언어로 명명한 식별자이며, 메모리의 주소를 저장한다. 이때, 메모리의 주소를 살펴보면 해당 주소가 참조하고 있는 값 또는 실제로 가지고 있는 값을 알 수 있다.

# 객체(Object)
- 위의 Primitive data type을 제외한 모든것을 지칭하며, Property(name : value로 구성된 데이터)와 동작을 나타내는 method를 포함하고있다.
여기서 method란 object에 제한돼 있는 함수를 말하며 property의 값이 함수일 경우 일반 함수와 구분하기 위해 method라고 부른다.

# Object의 생성
- ### Object literal
    - object의 생성에 있어 가장 간결한 방식이다.
    중괄호를 사용하여 객체를 생성하며, property를 부여하지 않으면 빈 객체가 생성된다.
- ### Object 생성자 함수
    - new 연산자와 Object()생성자 함수를 사용하여 object를 만드는 방법이다.
    어떤 방법으로든 object를 생성할때, 실제 내부 동작은 모두 이 방법에 의해서 생성이 된다. 따라서 일반적인 경우에 굳이 이 방식으로 object를 만들 이유는 없다.
- ### 생성자 함수
    - 생성자 함수란, form이 같은 object를 찍어내는 함수이다.
    즉, property의 값 부분은 같은데 이름이 다른 여러 object를 만들 때 유용하게 사용되며, 이 때 'this'연산자를 이용한 형태가 자주 등장한다.

# Object property 접근
- object의 property 값에 접근하기 위한 방법으로는 마침표 표기법과 대괄호 표기법이 있다.
``` javascript
var dog = {
    'name' : 'Tommy',
    'gender' : 'female',
};
console.log(dog);   // 'name' : 'Tommy', 'gender' : 'female'
console.log(dog.name);  // 'Tommy'
console.log(dog['name']);   // 'Tommy'
console.log(dog.gender);    // 'female'
console.log(dog['gender']); // 'female'
```
Object의 property 값에 접근할 때, 특별한 경우(property의 이름이 Javascript의 예약어인 경우)에는 대괄호 표기법만을 사용해서 값에 접근 할 수 있지만, 이외의 경우에는 마침표 표기법과 대괄호 표기법 모두 사용 할 수 있다.

# Pass by reference & Pass by value
- ### Pass by value
    - Javascript의 기본 자료형 중, immutable한 자료형의 값을 가지고 있는 변수를 다른 변수에 할당할 때 내부적으로 이루어지는 동작으로, 해당 변수가 가지고있는 값을 copy하여 전달하는 방식을 말한다.
- ### Pass by reference
    - object를 값으로 가지고 있는 변수를 다른 변수에 할당 할 때 내부적으로 이루어지는 동작으로, object가 참조하고 있는 값을 공유하는 방식을 말한다.

# Function
- ### 함수란?
    - 함수란 특정 작업을 수행하기 위한 statement들을 그룹화 하는 것으로 모듈화의 근간이 된다.
- ### 함수의 정의
    - 함수를 정의하는 방식은 3가지로, Function declaration, Function expression, Function 생성자 함수로 나뉜다.

## Function declaration
- function function_name(parameter or arguments) {statement} 의 구조로 선언되며 function_name은 생략할 수 없다. 

## Function expression
- 함수의 object 특성을 이용하여 literal 방식으로 함수를 정의하고 변수에 할당하는 방식이다.
var variable_name = function(parameter or arguments) {statement}의 구조로 선언한다.
함수를 변수에 할당할 때, 변수는 함수명이 아닌 할당된 함수의 참조값을 저장하고, 호출될 때 함수명은 변수처럼 사용된다.

## Function constructor
- 위의 Function declaration 정의 방식과 Function expression 방식으로 정의된 함수들이 내부적으로 동작하는 방식으로 object constructor와 비슷한 개념이다.

``` javascript
var foo = function(a, b) {
    return a + b;
};

var bar = foo;

console.log(foo(10,10));  // 20
console.log(bar(10,10));  // 20
```

## Function Hoisting
 함수도 변수와 같이 Javascript에서 로딩되는 시점에서 Hoisting이 일어난다.
 그런데, 함수의 Hoisting은 정의 방식에 따라 약간의 차이가 있다.

    - ### Function declaration으로 정의할 경우
        - Javascript는 모든 선언문(variable, function)을 해당 scope의 최상위로 옮기는 hoisting 작업을 한다.
        function declaration 방식으로 정의된 함수는 Javscript 엔진이 script가 로딩되는 시점에 초기화하고, 이를 variable object에 저장하여 함수의 선언, 초기화, 할당을 한번에 처리한다. 그렇기 때문에 함수의 위치와 상관 없이 소스 내 어느 곳에든지 함수 호출이 가능하다.

    - ### Function expression으로 정의할 경우
        - 이 경우, 변수에 함수를 할당하기에 함수는 Function hoisting이 아닌 Variable hoisting방식으로 hoisting된다.
        따라서 Javascript에서 로딩 될 때 Variable Object에 함수를 할당하지 않고, runtime에 해석되고 실행되어 함수의 선언과 초기화만 동시에 처리되고 할당은 되지 않는다.
        이같은 특성으로, Javascript에서 함수를 선언 할 때는 Function expression방식으로 선언하는 것을 권장한다.
        또한 Function declaration 방식으로 함수를 정의하면 사용하기엔 쉽지만, 규모가 큰 Application을 개발하는 경우 인터프리터가 많은 양의 코드를 Variable Object에 할당하므로 Application의 응답속도가 현저히 떨어지는 경우가 발생 할 수 있기에 주의해야 한다.

## First-class object
- First-class object란 생성, 대입, 연산, 인자 또는 반환값으로서의 전달 등의 프로그래밍 언어의 기본조작을 제한 없이 사용할 수 있는 object를 의미한다.
First-class object는 다음의 조건을 만족시킬 때 인정된다.
    * 무명의 리터럴로 표현 가능
    * 변수나 자료구조(object, array)에 할당 가능
    * 함수의 parameter로 전달 가능
    * return 값으로 사용 가능

## Parameter & Arguments
- 함수 내에서 Parameter는 변수와 동일하게 메모리 공간을 확보하며 동작한다. 전달된 Arguments는 Parameter에 할당되며, 할당 되지 않은 Parameter는 undefined로 초기화된다.
``` javascript
var tmp = function(t1,t2) {
    console.log(t1, t2);
    };
    tmp(1); // 1 undefined
```

## Callback Function
- Callback Function은 명시적으로 호출하는 함수가 아닌, 특정 상황이 발생했을 때 시스템에 의해 호출되는 함수이다.
대표적으로 Event Handler 처리에 자주 사용된다.
``` html
<!Doctype html>
<html>
<body>
    <button id = "testButton">Click!</button>
    <script>
        var button = document.getElementById('testButton");
        button.addEventListener('click', function() {
            console.log('Clicked!');
        });
    </script>
</body>
</html>
```
- Callback Function은 주로 비동기식 처리모델(Asynchronous processing model)에 사용된다.
비동기식 처리모델이란 처리가 종료되면 호출될 함수(Callback Function)을 미리 Parameter에 전달하고 처리가 종료되면 호출하는 것이다.
- Callback Function은 Callback queue에 들어가 있다가 해당 이벤트가 발생하면 호출되며 closure라 Queue에 단독으로 존재하다 호출되어도 Callback Function을 전달받은 함수의 변수에 접근할 수 있다.

## Prototype Object
- Javascript의 모든 Object는 자신의 Prototype을 가리키는 [[Prototype]]이라는 property를 가진다.
여기서 자신의 Prototype이란 사실상 클래스 기반 언어들에서 말하는 '부모 클래스'와 유사하다고 생각하면 된다.
브라우저 Chrome, Firefox 등에서는 이 property를 \__proto__\라고 명명하였기 때문에 [[Prototype]]과 \__proto__\는 같은 property이다.

``` javascript
var paerson = {
    name: 'John';
    nation: 'USA';
}
console.log(person.\__proto__\ === Object.prototype); // true
```

## 함수의 Prototype
- Javascript에서 함수는 객체이기 때문에 함수 역시 [[Prototype]] property를 가진다.
그런데, 함수는 일반 객체와 달리 prototype property라는것도 소유하게 된다.
prototype property는 함수 객체가 생성자로 생성될 때, 이 객체의 부모 역할을 하는 객체를 가리킨다.

- 함수의 [[Prototype]] property는 Object.prototype 객체를 가리키지 않고, Function.prototype을 가리킨다.
이유는 사실 Javascript에서 함수나 객체를 생성할 때, 생성된 객체(함수를 포함)의 종점이 Object.prototype이라는 Built-in Object인데, 객체는 Prototype-chain에서 생성된 객체의[[Prototype]]이 바로 Object.prototype을 가리키는 반면, 함수는 중간 단계에 FunctionName.prototype이라는 객체가 하나 더 생성되기 때문에 new 명령어로 생성된 객체의[[Prototype]]이 가리키는 객체가 FunctionName.prototype이기 때문이다.

## Prototype-chain
- Class가 없는 ES5에서 Class와 같은 상속을 구현하는 방법이다.
생성자 함수로 생성된 객체에 해당 Property가 없으면 그 객체의 부모 객체((?).prototype)에서 해당 Property를 찾는다.
(?).prototype 객체는 자동으로 생성되는 숨겨진 객체이지만, 임의로 수정이 가능하기 때문에 Class와 같은 상속을 구현 할 수 있다.
``` javascript
function Person(name) {
    this.name = name;
}
Person.prototype.gender = 'male';

var foo = new Person('Kim');
var bar = new Person('Baek');

console.log(foo.gender); // male
console.log(bar.gender); // male
// foo, bar object에 gender property가 없으면 동적 추가

foo.gender = 'female'; // foo object에 gender property가 있으면 해당 property에 값 할당
console.log(foo.gender); // female
console.log(bar.gender); // male
```

## Javascript의 Scope
- Javascript에서는 함수 내에 있는 변수가 아닌 변수들을 모두 전역 변수로 간주한다.
전역 변수의 [[Prototype]]은 전역 객체(Window object)이다.
즉, 변수는 기본적으로 코드 내 어디에서든 참조 할 수 있는 전역 Scope를 가진다.
전역 변수는 설계상 프로그램이 종료 될 때 까지 Garbage collection이 되지 않기 때문에, 프로그램을 계속 실행 시켜둘 시 큰 성능 저하를 야기한다.
이 때문에, Javascript에서 코드를 작성할 시 익명함수를 만들고, 모든 코드를 익명함수 안에 작성하는걸 권장한다.
이렇게 되면 모든 변수가 지역변수가 되기 때문에, System에서 Garbage collection을 자동으로 처리해주어, 프로그램을 계속 실행 하여도 성능 저하를 어느정도 방지 할 수 있다. (ECMAScript 6부터는 let이라는 새로운 방식의 변수 선언으로 block-level scope를 구현 할 수 있다.)

``` javascript
var x = 'global';

function foo() {
  var x = 'local';
  console.log(x); // local

  function bar() {
    console.log(x); // local
  }

  bar();
}
foo();
console.log(x); // global
```

## 암묵적 전역(implied globals)
Javascript에서는 함수 내에 변수 선언을 할 때라도, 'var'이라는 변수 선언문이 없으면 해당 변수를 전역 변수로 생성한다.
``` javascript
function test() {
    x = 1;
    var y = 5;
}

test();

console.log(x); // 1
console.log(y); // ReferenceError: y is not defined
```

## this
- 'this'는 새로운 object를 생성할때 기존 객체의 속성값을 재사용 하게 해주는 역할을 한다.
``` javascript

var Person = function(name, age) {
    this.name = name;
    this.age = age;
}

user1 = new Person('Jason', '18');
console.log(user1.name, user1.age); // jason, 18
```
- 그런데, Javascript의 this는 기본적으로 전역객체 global에 바인딩 되고, 이는 전역 함수 내부에 선언된 this, 내부 함수에 선언된 this 역시 마찬가지다.
이러한 전역객체로 바인딩 되는것을 방지하기 위해 여러 호출 패턴이 있다.
(일반 함수의 호출 시엔 this가 전역객체에 바인딩되고, 생성자 함수를 호출 할 경우 this는 생성자 함수가 생성할 객체에 바인딩 된다.)
``` javascript
// method invocation pattern
var obj = {
    name: 'Jason',
    sayName: function() {
        console.log(this.name);
    }
}

var obj_2 = {
    name: 'John'
}

obj_2.sayName = obj.sayName;
obj.sayName();
obj_2.sayName();
```
- 다음과 같이 생성자 함수를 호출할 때 new 명령어를 붙이지 않으면 this가 전역객체에 바인딩 되기 때문에 undefined가 표시된다.
```javascript
var Person = function(name) {
    this.name = name;
}

var you = Person('John');
var me = new Person('Jason');

console.log(you); // undefined
console.log(me); // Jason
```

## String
 String Object는 기본자료형인 string을 다룰 때 유용한 Property와 Method를 제공하는 Wrapper Object이다. 변수 또는 객체의 Property가 문자열을 값으로 가지고 있다면, 별도의 생성 없이 String객체의 Property와 Method를 사용할 수 있다.
 기본자료형으로 Wrapper 객체의 메소드를 사용할 수 있는 이유는 프로퍼티나 메소드를 호출할 때, 기본자료형과 연관된 Wrapper 객체로 일시적으로 변환되어 Prototype Object를 공유하게 되기 때문이다.
 String객체는 String() 생성자 함수로 생성할 수 있다. 이때 전달된 인자는 모두 문자열로 변환된다.
 ``` javascript
 var strObj = new String('Value');
 console.log(strObj); // String {0: 'V', 1: 'a', 2: 'l', 3: 'u', 4: 'e', length: 3, [[PrimitiveValue]]: 'Value'}
 ```
## 정규표현식(Regular Expression) 



## Javascript Execution Context
 Execution Context는 실행 가능한 코드가 실행 되는 환경이다.
이 때, 실행 되는 코드란

- Global code: Global 영역에 존재하는 코드
- Function code: 함수 내에 존재하는 코드
- Eval code: Eval 함수로 실행되는 코드

이다.
Javascript의 Engine은 코드를 실행하기 위해 실행에 필요한 여러가지 정보(변수, 함수 선언, 변수의 Scope, this)를 알고 있어야 한다.
이와 같은 코드의 실행에 필요한 정보를 형상화하고 구분하기 위해, Javascript Engine은 Execution Context를 물리적 객체의 형태로 관리한다.
``` javascript
var x = 'xxx';

function foo() {
    var y = 'yyy';
    function bar() {
        var z = 'zzz';
        console.log(x + y + z);
    }
    bar();
}
foo();
```
위의 코드를 실행하게 되면, Execution Context Stack이 생성되고 소멸한다.
현재 실행중인 context에서 현재 context와 관련없는 코드(다른 함수 등)가 실행되면 새로 실행된 context가 생성되고, 이 context는 Execution Context Stack에 쌓이고 control(제어권)이 이동한다.
함수를 실행하면, 직전에 실행중인 context stack 위에 새로운 실행된 함수의 context가 쌓이게 되며, 함수 실행이 끝나면 해당 함수의 context를 stack에서 파기하고 직전 context로 control(제어권)을 반환한다.
이 때문에, 전역객체의 실행 컨텍스트(Global Object Execution Context)는 Execution Context Stack의 가장 아랫부분(최상위 Stack)에 있으므로 해당 Application이 종료될 때 까지 Stack에서 파기되지 않는다.(계속 실행 되고 있다)

## Execution Context의 3가지 Object
 Execution Context는 추상적인 개념이지만, 물리적 객체 형태를 취하며 Variable Object, Scope Chain, thisValue라는 3가지 Property를 가진다.

## Variable Object
 Execution Context가 생성되면, Javascript Engine은 실행에 필요한 여러가지 정보를 담을 객체를 생성한다. 이를 Variable Object라고 한다. Variable Object는 코드가 실행될 때 Engine에 의해 참조되며, 코드 내에서는 접근할 수 없다.
 Variable Object가 담는 정보는 변수(variable), 함수의 선언(function declaration), 매개변수와 인자(Parameters & Arguments)이다.
 Variable Object는 Execution Context의 Property이기 때문에 값을 갖는데, 이 값은 다른 객체를 가리킨다. 그런데, 전역 코드 실행시 생성되는 Global Execution Context의 경우와 함수를 실행할 때 생성되는 Function Execution Context의 경우, 전역코드와 함수의 내용이 다르기 때문에 Context가 가리키는 객체가 다르다. 예를들어, 전역코드에는 매개변수가 없지만 함수에는 있기 때문이다.
 즉, Global Execution Context의 경우 V.O는 최상위 객체인 전역객체를 가리키고, Function Execution Context의 경우 V.O는 Activation Object라는 활성 객체를 가리키며, A.O에는 매개변수와 인수들의 정보를 배열의 형태로 담고있는 arguments object가 추가된다.

## Scope Chain
 Scope Chain은 일종의 리스트로서 중첩된 함수 스코프의 레퍼런스를 차례로 저장하고 있다.
 즉, Scope Chain은 현재 실행 컨텍스트의 Activation Object를 선두로하여 순차적으로 상위 컨텍스트의 Activation Object를 가리키며, 최정적으로 전역 객체를 가리킨다.
 Javascript Engine은 이를 통해 변수의 Scope를 파악한다.
 Scope Chain을 통해 변수를 차례로 검색한 뒤, 최상위 객체인 Global Object에도 변수가 없다면 Reference Error를 발생시킨다. Scope Chain은 [[scope]] property로 참조할 수 있다.


## Rest Operator

 ### Rest Parameter
 ES5의 arguments객체를 대신할 방법이다.

 ``` javascript
 function foo(...rest) {
     console.log(Array.isAarray(rest)); // true;
     console.log(rest); // [1,2,3,4,5]
 }
 
 foo(1,2,3,4,5);
 ```
 Rest Paremeter을 사용하면 인수를 함수 내부에서 배열로 전달받을 수 있다.
 ES5에서는 arguments 객체에 유사배열을 집어넣고 이를 apply 또는 call 메소드로 배열로 변환을 해야했다.
 이 때, Rest Parameter은 반드시 마지막 Parameter이어야 한다.
 * Parameter의 최대 갯수는 255개이다.
 * Rest Parameter 앞에 ...은 Spread Operator이다. 즉, Rest Parameter은 Spread연산을 한 Parameter이다.
 
## 배열에서 사용하는 경우
 
 ### concat
 ``` javascript

 // ES5
 var arr = [1,2,3];
 console.log(arr.concat[4,5,6])); // [1,2,3,4,5,6]

 // ES6

 const arr = [1,2,3];
 console.log([...arr, 4, 5, 6]); // [1,2,3,4,5,6]

 ```
 ### push
 ``` javascript

 // ES5
 var arr1 = [1, 2, 3];
var arr2 = [4, 5, 6];

// apply 메소드의 2번째 인자는 배열. 이것은 개별 인자로 push 메소드에 전달된다.
Array.prototype.push.apply(arr1, arr2);

console.log(arr1); // [ 1, 2, 3, 4, 5, 6 ]

```
 * Spread Oprator은 가독성이 좋지만 Performance가 좋지않다.(concat > push > ...) 그러니까 1000개 정도 되는 배열은 concat을 쓰자...
 * Attribute에서 요소를 가져오면 무조건 string형으로 가져온다

## Enhanced Object Property
 
 ### Property 축약 표현
 ES6에서는 Property 값으로 변수를 사용하는 경우, Property 이름을 생략할 수 있다. 이 때, Property 이름은 변수의 이름으로 자동 생성된다.

 

# Destructuring
 Destructuring은 기존에 구조로 가지고 있던 객체를 개별적인 변수에 할당하는 것이다. 배열 또는 객체 리터럴에서 필요한 값만을 추출하여 변수에 할당하거나 반환할 때 유용하다.

 ### Array destructuring
 ``` javascript
 const arr = [1,2,3];
 const [one, tow, three] = arr;
 console.log(one, two, three); // 1 2 3
 ```
 위와 같이 사용한다.
 
 ### Object destructuring
 ``` javascript
 const obj = { firstName: 'Ungmo', lastName: 'Lee' };
 const { firstName, lastName } = obj;
 console.log(firstName, lastName); // Ungmo Lee
 ```


# Class
 
 ES6에 도입된 Class는 사실 Function이다.
 많은 논란이 있었지만, 결국 많은 사용자들의 요구에 의해 Syntax sugarting으로 도입되었다.
 Class는 Prototype chain에 의해 구현되는 Function이지만, 좀 더 직관적이다.

 ``` javascript
 // ES5
 var Person = (function () {

     // Constructor 역할을 하는 함수 생성
     function Person(name) {
         this._name = name;
     }

     // Method
     function sayHi() {
         console.log('Hi ' + this._name);
     }

     return Person; // 내부에 선언된 Person 함수를 리턴
 }())
 
 var user1 = new Person('Jason');
 user1.sayHi(); // 'Hi Jason'
 ```
 ES6의 Class를 ES5로 나타낸 코드이다.
 위와 같이 Class는 사실 외부함수(즉시 실행 함수)에서 내부함수를 리턴하는 것으로 구현 할 수있다.
 이때 내부함수 Person은 생성자 함수로 동작한다.
 즉, return Person은 Constructor을 리턴하는것이다.

 ``` javascript
 // ES6
 class Person {
     
     constructor(name) {
         this._name = name;
     }

     sayHi() {
         console.log('Hi ' + this._name);
     }
 } 

 const user1 = new Person('Jason');
 user1.sayHi(); // 'Hi Jason'
 ```

 Class의 body에는 Method만을 쓸 수 있다.
 만일, body에 직접 변수를 선언하면 Syntax Error를 발생시킨다.
 따라서 멤버변수는 Method 내부에 선언해야한다.

 * 멤버변수: 클래스 내부에 선언된 변수

 ### constructor
 constructor는 인스턴트를 생성하고 초기화하기 위한 Method이다.
 
 ### 멤버변수
 멤버변수는 Property를 의미하는데, Property의 값으로 data만 올 수 있다.(객체 리터럴에서 Property value는 undefined를 제외한 모든것을 쓸 수 있다.) 즉, Method를 제외한 모든것을 값으로 쓸 수 있다.
 멤버변수는 constructor() {} 내부에서만 쓸 수 있다.(멤버변수는 this를 앞에 붙인 변수이다.)

 ### getter & setter
 멤버 변수에 접근하기 위한 연산자이다.
 getter는 멤버변수를 참좋하여 값을 반환해야하므로 return이 있어야하고, setter는 멤버변수를 참조하여 값을 써야하므로 return이 없어야 한다. 또한 setter는 parameter을 가져야한다.

 ### Static Method
 Static Method는 new 연산자를 통한 인스턴스화 없이 실행 가능하며, 특정 인스턴스에 적용되지 않는다.
 Static Method에서 this는 인스턴스에 바인딩 되지 않고, 클래스 자체에 바인딩되며 이 때, 일반적으로 this대신 클래스 이름을 사용한다.
 ``` javascript

  class Car {
      static getNextVin() {
          return Car.nextVin++; // this.nextVin++와 동치
      }

      constructor(make, model) {
          this.make = make;
          this.model = model;
          this.vin = Car.getNextVin();
      }

      static areSimilar(car1, car2) {
          return car1.make === car2.make && car1.model === car2.model;
      }

      static areSame(car1, car2) {
          return car1.vin === car2.vin;
      }
  }
  Car.nextVin = 0;

  const car1 = new Car('Tesla', 'S');
  const car2 = new Car('Mazda', '3');
  const car3 = new Car('Mazda', '3');

  car1.vin; //0
  car2.vin; //1
  car3.vin; //2

  Car.areSimilar(car1, car2); // false
  Car.areSimilar(car2, car3); // true
  Car.areSame(car2, car3); // false
  Car.areSame(car2, car2); // true
 ```

 * 일반 메소드(프로토타입)는 반드시 new를 통해 인스턴스화 한 후 호출이 가능하다.

 
 ``` javascript

 class Foo {
     constructor (prop) {
         this.prop = prop;
     }
     static staticMethod() {
         return 'staticMethod';
     }
     prototypeMethod() {
         return 'prototypeMethod';
     }
 }
 
 const foo = new Foo(123);

 console.log(Foo.staticMethod());
 console.log(foo.staticmethod()); // Type Error

 ```
 ES5에서 Staitc Method는 Object.creator() Method이다.

 ### Class의 상속
 class의 상속은 extends 명령으로 이루어진다.

 ### Super keyword
 부모 클래스의 constructor를 사용하겠다는 키워드로, 자식클래스의 선두에 사용하는것이 좋다.(부모클래스를 한번 호출하면 super키워드 없이도 부모클래스의 속성값을 이용할 수 있다. 이를 single-turn pattern이라 한다.)
 

 ## Promise
 비동기 함수에서의 에러 처리, 콜백 헬 등의 문제점을 보완하기 위해 ES6에서 새로 나온 개념이다.
 비동기함수는 값을 리턴할 수 없기에, 에러를 발생시키기 위해서는 콜백 함수 안에 또다른 콜백함수를 넣어야 하기 때문에 콜백의 Depth가 깊어지는 문제가 발생한다.
 이같은 문제를 해결하기 위해 ES6에서 Promise가 등장하게 되었다.
 Promise의 기본 개념은 Promise 기반 비동기 함수를 호출하면 해당 함수는 Promise 인스턴스를 반환한다.
 Promise는 성공(fulfilled)하거나, 실패(rejected)하거나의 두가지 상태를 가지며, 하나의 상태를 가지면 해당 상태가 변하는 경우는 없다.
 이를 Promise가 결정됐다(settled)라고 한다.
 promise 객체를 리턴하여 오류가 발생했는지 확인할 수 있다.
 promise 객체는 상태(state)를 가지는데, 비동기 처리가 성공하였는지 실패하였는지의 상태를 가진다.
 
 ### Promise 생성
 Promise는 생성자 함수로 만들며, 콜백 함수를 인자로 가지게 한다.

 ``` javascript
 let promise = new Promise((resolve, reject) => {
     if (/* 비동기 작업 수행 성공 */) {
         resolve(/* 성공했을 시 콜백함수 내에서 수행할 작업 */)ㅣ
     }
     else {/*비동기 작업 수행 실패 */
        reject(Error(/* Error의 내용 */));
     }
 });
```

 ## 모듈(module)
- 캡슐화하고 공개가 필요한 API를 외부에 노출하여 다른 코드에서 로드하고 사용할 수 있도록 작성된
재사용 가능한 코드 조각을 말한다.

### export & import
- 모듈 안에 선언한 항목을 외부에 공개하여 다른 모듈들이 사용할 수 있게 하고 싶다면 export해야 한다.
선언된 변수, 함수, 클래스 모두 export할 수 있다.

``` html
<!DOCTYPE html>
<html>
<body>
  <button id="btn">Click me</button>
  <script>
    var btn = document.getElementById('btn');

    // 전통적 DOM Event Handler 방식은 이벤트 핸들러에 하나의 함수만을 바인딩할 수 있다
    // 첫번째 바인딩된 이벤트 핸들러 => 실행되지 않는다.
    btn.onclick = function () {
      alert('Button clicked 1');
    };

    // 두번째 바인딩된 이벤트 핸들러
    btn.onclick = function () {
      alert('Button clicked 2');
    };

    // DOM Level 2 Event Listener
    // 첫번째 바인딩된 이벤트 핸들러
    btn.addEventListener('click', function () {
      alert('Button clicked 1');
    });

    // 두번째 바인딩된 이벤트 핸들러
    btn.addEventListener('click', function () {
      alert('Button clicked 2');
    });
  </script>
</body>
</html>
```
위 코드에서 첫번째 btn.onclick은 무시된다.
이는, EVENT Handler에 하나의 함수만을 할당 할 수 있기 때문이다.

## XMLHttpRequest
 _Browser_는 _XMLHttpRequest_ 객체를 이용하여 Ajax 요청을 생성하고 전송한다.
 서버가 브라우저의 요청에 때해 응답을 반환하면 같은 _XMLHttpRequest_객체가 결과를 처리한다.

### XMLHttpRequest.open
 XMLHttpRequest 객체의 인스턴스를 생성하고 XMLHttpRequest.open 메소드를 사용하여 서버로의 요청을 준비한다.

### XMLHttpRequest.send
 XMLHttpRequest.send 메소드로 준비된 요청을 서버에 전달한다.
 서버로 전송하는 데이터는 GET, POST메소드에 따라 전송 방식에 차이가 있는데,
 GET메소드는 URL의 쿼리문자열로 데이터를 서버로 전송하고,
 POST메소드는 데이터를 Request Body에 담아 전송한다.

 * GET메소드는 쿼리문자열로 데이터를 전송하기 때문에 보안상 문제로 POST를 사용할 때가 많다.

## Ajax response

 ``` javascript
 // XMLHttpRequest.readyState 프로퍼티가 변경(이벤트 발생)될 때마다 이벤트 핸들러를 호출한다.
req.onreadystatechange = function (e) { // 'on'이 빠진 readystatechange가 실행된다.
  // readyStates는 XMLHttpRequest의 상태(state)를 반환
  // readyState: 4 => DONE(서버 응답 완료)
  if (req.readyState === XMLHttpRequest.DONE) {
    // status는 response 상태 코드를 반환 : 200번대 => 정상 응답 400번대 => 에러
    if(req.status === 200) {
      console.log(req.responseText);
    } else {
      console.log("Error!");
    }
  }
};
```
 서버에서 받을 _data_는 위 코드의 responseText에 담겨있다. 

 * XMLHttpRequest로 만든 객체를 서버에 전송하고, 서버는 다시 그 객체에 data를 담아 응답한다.
 
 * send 메소드에 인자를 주면 payload를 주는것이다.