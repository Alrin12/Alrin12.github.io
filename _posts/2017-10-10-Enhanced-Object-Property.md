---
layout: post
title: ECMAScript Enhanced Object Property
tags: [ECMAScript, Javascript, Data type, Object]
date: 2017-10-10
comments: false
---
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