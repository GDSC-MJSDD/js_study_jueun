## 16장 프로퍼티 어트리뷰트

#### 내부 슬롯과 내부 메서드

1. 내부 슬롯과 내부 메서드

* 자바스크립트 엔진의 구현 알고리즘 설명을 위해 ECMAscript 사양에서 제공하는 의사 프로퍼티, 의사 메서드
* [[ ... ]] 이중 괄호로 감싸인 부분
* 실제로 구현, 동작 하지만 개발자가 직접 접근할 수 없다.
* 간접 접근은 가능하다

```javascript
const o = {};

o.[[Prototype]] // 에러
o.__proto__ // Object.prototype. 간접 접근
```


#### 프로퍼티 어트리뷰트와 프로퍼티 디스크립터 객체

자바스크립트 엔진은 프로퍼티 생성 시 프로퍼티 상태 나타내는 프로퍼티 어트리뷰트 기본값으로 자동 정의

* 프로퍼티 상태 : 값, 갱신 가능 여부, 열거 가능 여부, 재정의 가능 여부
* 프로퍼티 어트리뷰트 : 내부 슬롯 중 내부 상태 값 4가지
  * 위와 같이 직접적으로는 불가하지만 간접적으로 프로퍼티 어트리뷰트 확인 가능

```javascript
const person = {
  name : 'Lee';
};

console.log(Object.getOwnPropertyDescriptor(person, 'name'));
// { value : "Lee", writable: true, enumerable: true, configurable: true }
```
위의 코드에서 **Object.getOwnPropertyDescriptor(객체 참조, 프로퍼티 키)** 하면 **프로퍼티 디스트립터 객체 반환**
Object.getOwnPropertyDescriptor(객체 참조) 매개변수를 하나만 쓰면 모든 프로퍼티의 프로퍼티 어트리뷰트 제공하는 프로퍼티 디스크립터 객체 반환


#### 데이터 프로퍼티와 접근자 프로퍼티

* 데이터 프로퍼티
  * 키와 값으로 구성된 일반적인 프로퍼티

* 접근자 프로퍼티
  * 자체적으로 값을 갖지 않고 다른 데이터 프로퍼티 값을 읽거나 저장 시 호출되는 접근자함수로 구성된 프로퍼티

1. 데이터 프로퍼티

* 프로퍼티 어트리뷰트 : 프로퍼티 디스크립터 객체의 프로퍼티 : 상세

  * [[Value]] : value : 키를 통해 반환되는 값
  * [[Writable]] : writable : 값의 변경 가능 여부, Boolean
  * [[Enumerable]] : enumerable : 열거 가능 여부, Boolean
  * [[Configurale]] : configurable : 재정의 가능 여부, Boolean

* 프로퍼티 생성 시 하위 3가지 프로퍼티 어트리뷰트 값은 true로 초기화된다.


2. 접근자 프로퍼티

* 프로퍼티 어트리뷰트 : 프로퍼티 디스크립터 객체의 프로퍼티 : 상세

  * [[Get]] : get : 접근자 함수, getter 호출되어 결과가 프로퍼티 값으로 반환
  * [[Set]] : set : 접근자 함수, setter 호출되어 결과가 프로퍼티 값으로 반환
  * [[Enumerable]] : enumerable : 열거 가능 여부, Boolean
  * [[Configurale]] : configurable : 재정의 가능 여부, Boolean

# 224 - 226p 다시 보기


#### 프로퍼티 정의

* 새로운 프로퍼티 추가하며 프로퍼티 어트리뷰트 명시적으로 정의
* 기존 프로퍼티의 프로퍼티 어트리뷰트 재정의
* **Object.defineProperty**메서드 사용

# 밤이라 머리에 안들어와서 추후 추가 ...
