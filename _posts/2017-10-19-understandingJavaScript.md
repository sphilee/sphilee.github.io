--- 
title: "자바스크립트 이해하기" 
layout: post 
date: 2017-10-19 15:00 
tag: tips-and-tricks 
blog: true 
draft: false 
author: sphilee 
summary: "자바스크립트 이해하기" 
permalink: Understanding-JavaScript 
---
### 비트연산자 보수이해하기
* 1의 보수에 1을 더함

### 10을 2진표현으로 변경하려면 어떤 순서로 계산해야 하는지 설명하기.
* 2로 나눠 나머지를 계속 일의자리수부터 나타내는 식으로

### hoisting 에 대해서 설명하기
* 자바스크립트 코드를 인터프리터가 로드할 때, 변수의 정의가 그 범위에 따라 선언과 할당으로 분리되어 변수의 선언을 항상 컨텍스트 내의 최상위로 끌어올리는 것을 의미한다. 이는 오로지 변수에만 해당되는 것은 아니고 함수도 가능하며, 자바스크립트에서 함수의 호출을 첫 줄에서 하고 마지막 줄에 함수를 정의해도 문제없이 작동되도록 하는 유용한 특성이다.

### !! 은 무엇을 의미하는가? 어떻게 활용할 수 있을까?
* 모든 type을 boolean type으로 바꿔준다.

### 3개이상의 switch 문을 어떻게 3항연산자로 대체할 수 있을까? 코드로 예시를 들라.
* a ? b : c ? d : e

### ==와 ===의 차이는 정확히 무엇인가?
* ==  : 값만 비교
* === : type과 값 비교
  
### const value = a || b; 코드의 의미는 무엇인가?
* a가 없으면 b로 할당

### eval 은 무엇인가?
* 문자로써 표현된 JavaScript 코드를 실행하는 메소드이다.

### 변수값을 출력할때 null, undefined, is not defined으로 출력되는 차이점은 무엇인가?
* null : 사용자가 값이 없다라고 null을 설정한 경우라면 null을 반환
* undefined : 객체(변수)가 선언되었으나, 값이 설정되지 않은 경우
* is not defined : 객체 자체가 존재하지 않는 경우

### Function.prototype.bind 에 대해서 설명하기
* bind() 메소드는 호출될 때 그 this 키워드를 제공된 값으로 설정하고 새로운 함수가 호출될 때 제공되는 주어진 순서의 선행 인수가 있는 새로운 함수를 생성합니다.
```javascript
fun.bind(thisArg[, arg1[, arg2[, ...]]])
```

### this가 가리키는 건 언제 결정되는가?
* 자바스크립트의 경우 함수 호출 패턴에 따라 어떤 객체를 this에 바인딩할 지가 결정된다. 즉 함수 호출 패턴에 따라 this의 참조값이 달라진다.

### 함수 호출 패턴(Function Invocation Pattern)
* 전역객체(Global Object)는 모든 객체의 유일한 최상위 객체를 의미하며 일반적으로 Browser-side에서는 window, Server-side(Node.js)에서는 global 객체를 의미한다.

### 메소드 호출 패턴(Method Invocation Pattern)
* 함수가 객체의 프로퍼티이면 메소드 호출 패턴으로 호출된다. 이때 메소드 내부의 this는 해당 메소드를 소유한 객체 즉 해당 메소드를 호출한 객체에 바인딩된다.

### 생성자 호출 패턴(Constructor Invocation Pattern)
1. 빈 객체 생성 및 this 바인딩
* 생성자 함수의 코드가 실행되기 전 빈 객체가 생성된다. 이 빈 객체가 생성자 함수가 새로 생성하는 객체이다. 이후 생성자 함수 내에서 사용되는 this는 이 빈 객체를 가리킨다. 그리고 생성된 빈 객체는 생성자 함수의 prototype 프로퍼티가 가리키는 객체를 자신의 프로토타입 객체로 설정한다.
2. this를 통한 프로퍼티 생성
* 생성된 빈 객체에 this를 사용하여 동적으로 프로퍼티나 메소드를 생성할 수 있다. this는 새로 생성된 객체를 가리키므로 this를 통해 생성한 프로퍼티와 메소드는 새로 생성된 객체에 추가된다.
3. 생성된 객체 반환
* 반환문이 없는 경우, this에 바인딩된 새로 생성한 객체가 반환된다. 명시적으로 this를 반환하여도 결과는 같다.
* 반환문이 this가 아닌 다른 객체를 반환하는 경우, this가 아닌 해당 객체가 반환된다. 따라서 생성자 함수는 반환문을 명시하지 않는다.

### call과 apply의 차이점은?
* 함수 호출 시 각 상황에 따라 this에 바인딩될 객체가 결정된다. 이는 자바스크립트 엔진 내부에서 자동으로 실시되는 것이다. 이러한 내부적인 바인딩 이외에 this를 특정 객체에 명시적으로 바인딩하는 방법도 제공된다. 이것을 가능하게 하는 것이 Function.prototype.apply(), Function.prototype.call() 메소드이다.
* call() 메소드의 경우, apply()와 기능은 같지만 apply()의 두번째 인자에서 배열 형태로 넘긴 것을 각각 하나의 인자로 넘긴다.

### add(10)(2) -12 가 되도록 구현해보기
```javascript
Function.prototype.curry = function() {
  var args = [].slice.apply(arguments);
  var self = this;
  return function() {
    return self.apply(null, args.concat([].slice.apply(arguments)));
  };
};
add( 10 )( 2 ); // 12
```

### 함수의 인자갯수와 파라미터가 일치하지 않으면 어떤일이 생기는가 설명하기
* 파라미터가 많을경우 나머지 매개변수 구문에 넣음.
* 나머지 매개변수(rest parameter) 구문은 정해지지 않은 수(an indefinite number, 부정수) 인수를 배열로 나타낼 수 있게 합니다.

### 함수의 반환값이 없을때 어떻게 되는가?
* undeifned를 반환한다.

### 익명함수는 무엇인가?
* 이름이 없는 함수를 뜻 한다. 이는 함수명을 메모리에 할당하지 않을 수 있다는 장점이 있다.