---
layout: post
title: ECMAScript Scope
tags: [ECMAScript, Javascript, Data type, Object]
date: 2017-10-05
comments: false
---
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