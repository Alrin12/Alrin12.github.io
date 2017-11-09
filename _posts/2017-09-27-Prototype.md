---
layout: post
title: ECMAScript Prototype
tags: [ECMAScript, Javascript, Data type, Object]
date: 2017-09-27
comments: false
---
## Prototype Object
- Javascript의 모든 Object는 자신의 Prototype 객체를 가리키는 [[Prototype]]이라는 property를 가진다.
여기서 자신의 Prototype 객체란 클래스 기반 언어들에서 말하는 '부모 클래스'와 유사하다고 생각하면 된다.
객체는 [[Prototype]]을 통해 프로토타입 연쇄 동작을 한다. 이는 Scope와 직접적으로 관련이 있다.

* 브라우저 Chrome, Firefox 등에서는 이 property를 \__proto__\라고 명명하였고,  따라서 [[Prototype]]과 \__proto__\는 같은 property이다.

``` javascript
var paerson = {
    name: 'John';
    nation: 'USA';
}
console.log(person.\__proto__\ === Object.prototype); // true
```

## 함수의 Prototype
- Javascript에서 함수는 객체이기 때문에 함수 역시 [[Prototype]] property를 가진다.
그런데, 함수는 일반 객체와 달리 prototype라는 property라는것도 소유하게 된다.
prototype property는 함수 객체가 생성자로 생성될 때, 이 객체의 실질적인 부모 역할을 하는 객체를 참조한다.

- 함수의 [[Prototype]] property는 Object.prototype 객체를 직접 참조하지 않고, Function.prototype을 참조한다.
이유는 Javascript에서 함수나 객체를 생성할 때, 생성된 객체(함수를 포함) 프로토타입 연쇄의 종점이 Object.prototype이라는 Built-in Object인데, 일반 객체는 Prototype chain에서 생성된 객체의[[Prototype]]이 바로 Object.prototype을 참조하는 반면, 함수 생성자는 Object.prototype과 인스턴스 사이에 FunctionName.prototype 객체를 하나 더 생성하기 때문이다. 

## Prototype chain
- Class가 없는 ES5에서 Class와 같은 상속을 구현하는 방법이다.
함수의 경우, 생성자 함수로 생성된 객체에 해당 Property가 없으면 그 객체의 부모 객체(Function.prototype)에서 해당 Property를 찾는다. (일반 객체의 경우 Object.prototype에서 Property를 찾는다.)
Function.prototype 객체는 자동으로 생성되는 숨겨진 객체이지만, 임의로 수정이 가능하기 때문에 Class와 같은 상속을 구현 할 수 있다.
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