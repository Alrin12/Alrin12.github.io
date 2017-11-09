---
layout: page
title: ECMAScript Basic Flow
tags: [ECMAScript, Javascript, Data type, Object]
date: 2017-09-21
comments: false
---
# Data type
 ECMAScript의 자료형은 7개로, 각각의 자료형은 아래와 같다.
 
 ## Primitive Data Type
  
  ### Boolean
  - Bool이 고안한 대수 체계로, 컴퓨터에서는 연산의 값이 두개의 상태(True, False)로 귀결되는 것을 표현한 것이다.
  조건에 의한 분기 또는 반복문을 만들 때 유용하게 사용된다.
  
  ### Number
  - 숫자 자료형으로 정수(Integer)와 실수(float)를 표현한다.
   
  ### String
  - 문자 자료형으로 문자를 표현하며, Number자료형 간 형 변환도 가능하다.
   
  ### null
  - 존재하지 않는 메모리 주소를 의미한다. 주로 메모리가 할당되기 전 초기화를 하기 위해 사용하였는데, 현재에는 큰 의미가 없기에 null 자체를 배제하는 움직임이 있다. 심지어 null reference를 만든 사람인 Tony Hoare가 null을 만든것은 실수였다고 직접 말하기까지 했다.
   undefined
  
  - 변수에 자동적으로 할당되는 초기값으로 말 그대로 '아무것도 할당되지 않았을 때' 변수에 자동적으로 할당되는 기본값이다.
  엄밀히 말하자면, 실행 컨텍스트상에서 일어나는 변수의 호이스팅에서 변수를 초기화할 때 자동으로 할당되는 값으로, 모든 변수는 null을 할당하지 않는 이상 적어도 한번 undefined 값을 가지게 된다. 이후에 변수에 할당되는 다른 값이 있다면, 실행컨텍스트의 할당단계에서 해당 값을 변수에 할당한다. 
   
  ### symbol
  - ECMAScript6에서 등장한 기본 자료형으로, html의 <id>태그 같은 존재이다. 즉, 전체 구문에서 재사용되지 않을(또는 않아야 할)것들을 표현할 때 사용된다.
  이를 이용하여 자바스크립트 스펙에서 지원하지 않는 접근제한을 구현할 수 있다. 
  
  ### Object
  - 위에서 언급한 기본 자료형을 제외한 모든 것들을 나타낸다.

# 변수(Variable)
 변수란 사람이 이해할 수 있는 언어로 명명한 식별자이며, 메모리의 주소를 저장한다. 이때, 메모리의 주소를 살펴보면 해당 주소가 참조하고 있는 값 또는 실제로 가지고 있는 값을 알 수 있다.

 * 사실, 메모리의 주소를 참조하는 것이 포인터이다.
 즉, C나 C++이 아닌 Java, Python 또는 Javascript에서 포인터가 없다는 것은 틀린 말이다.
 가령 아래와 같은 예시가 있다고 해보자.

```python
a = 1
b = a
a += 1

print(b) # 1 
print(a) # 2

// in C
int a = 1;
int b = a;
a += 1;
 
printf('%d', %a); // 2
printf('%d', %b); // 2
```

 위 코드에서 파이썬의 변수 b의 값은 a가 1 증가하였음에도 여전히 1이다. 이는 파이썬과 같은 언어에서는 얕은복사를 기본으로 하기 때문에 일어나는 현상으로, 변수 b가 a의 주소 참조하기 때문에 b의 값은 변하지 않는다.
 반면 C에서는 기본적으로 할당을 할 때 깊은 복사를 하므로, a와 b가 모두 같은 값을 가지게 되는 것이다.

 * 자바스크립트의 또 다른 특징중 하나로는 변수 선언시 변수명만 선언하여도 에러를 발생시키지 않는다는 것이다. 
 이는 실행 컨텍스트가 변수를 생성할 때 undefined 값을 할당하기 때문에 일어나는 현상으로, 자바스크립트의 유연성을 보여주는 한 예이다.

# 객체(Object)
 - 위의 Primitive data type을 제외한 모든것을 지칭하며, Property(name : value로 구성된 데이터)와 동작을 나타내는 method를 포함하고있다.
 여기서 method란 object에 제한된 함수를 말하며 property의 값이 함수일 경우 일반 함수와 구분하기 위해 method라고 부른다.
 * 일반적으로 다른 클래스 기반 언어에서는 method를 클래스에 종속되어 있는 함수를 말한다.

# Object의 생성

 ### Object literal
    - 객체의 생성 방법 중 가장 간결한 방식이다.
    중괄호를 사용하여 객체를 생성하며, property를 부여하지 않으면 빈 객체가 생성된다.

 ### Object 생성자 함수
    - new 연산자와 Object()생성자 함수를 사용하여 object를 만드는 방법이다.
    어떤 방법으로든 object를 생성할때, 실제 내부 동작은 모두 이 방법에 의해서 생성이 된다. 따라서 일반적인 경우에 굳이 이 방식으로 object를 만들 이유는 없다.
    
 ### 생성자 함수
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
 * 사실 객체에 접근할 때, 해당 프로퍼티를 선언한 객체 내에서 찾지는 않는다. 예를 들어 위 코드의 dog.name의 경우, 선언된 dog 객체 내의 name 프로퍼티 값을 참조하는 것 처럼 보이지만, 내부적으로는 [[get]]연산자를 사용하여 name 프로퍼티를 호출하는것이다. 이는 프로토타입 체인과 관련있으며, 객체 내에서 찾는 프로퍼티가 없으면 [[Prototype]]링크를 통해 연결된 객체에서 해당 프로퍼티를 찾은 후, 최종적으로 찾지 못하였다면 undefined를 반환한다.

# Pass by reference & Pass by value

  ## Pass by value
  - Javascript의 기본 자료형 중, immutable한 자료형의 값을 가지고 있는 변수를 다른 변수에 할당할 때 내부적으로 이루어지는 동작으로, 해당 변수가 가지고있는 값을 copy하여 전달하는 방식을 말한다. (깊은복사)
  ## Pass by reference
  - object를 값으로 가지고 있는 변수를 다른 변수에 할당 할 때 내부적으로 이루어지는 동작으로, object가 참조하고 있는 값을 공유하는 방식을 말한다. (얕은 복사)