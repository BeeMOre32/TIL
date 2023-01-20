# Class 는 무엇인가

`class` 문법은 ES6에서 처음으로 도입 되었으며, 이전에는 `prototype`을 사용하여 객체를 생성하였다. `class` 문법은 `prototype`을 사용하지 않고 객체를 생성할 수 있게 해준다.\

`class`를 선언하는 방법은 다음과 같다.

```js
class Person {
  constructor(name) {
    this.name = name;
  }
  sayHello() {
    console.log(`Hello, I'm ${this.name}`);
  }
}
```

`class`를 선언하면 `constructor` 함수가 자동으로 생성되며, `constructor` 함수는 `class`를 생성할 때 호출된다. `constructor` 함수는 `class`의 인스턴스를 생성할 때 호출되며, `constructor` 함수의 인자로 전달된 값은 `class`의 인스턴스를 생성할 때 전달된 값이다.

`class`를 생성할 때는 `new` 키워드를 사용한다.

```js
const person = new Person('John');
person.sayHello(); // Hello, I'm John
```

이런식으로 사용하며, `class` 를 사용한다. 하지만 이렇게 본다면 그냥 객체를 사용하여 생성하는 것과 큰 차이가 없으며 오히려 객체를 사용하는 것 보다 훨씬 더 복잡하게 보인다.

```js
const person = {
  name: 'John',
  sayHello() {
    console.log(`Hello, I'm ${this.name}`);
  }
}

person.sayHello(); // Hello, I'm John
```

하지만 `class`를 사용하는 이유는 `class`를 사용하면 `class`를 상속할 수 있기 때문이다. `class`를 상속할 때는 `extends` 키워드를 사용한다.

```js
class Programmer extends Person {
  constructor(name, language) {
    super(name);
    this.language = language;
  }
  sayHello() {
    console.log(`Hello, I'm ${this.name}. I'm a ${this.language} programmer.`);
  }
}

const programmer = new Programmer('John', 'JavaScript');
console.log(programmer); // Programmer { name: 'John', language: 'JavaScript' }
```

`class`를 상속할 때는 `super` 키워드를 사용하여 부모 클래스의 `constructor` 함수를 호출해야 한다. `super` 키워드를 사용하지 않으면 `this` 키워드를 사용할 수 없다.

`class`를 상속하면 부모 클래스의 메소드도 마찬가지로 사용할 수 있다. 

지금도 사실 감이 잘 안오기는 한다. 그 이유는 `this` 라는 키워드 때문인데 `this` 키워드는 바로 다음시간에 알아보고 지금은 이 `class` 문법을 사용하는 이유를 알아보자.

- `class` 문법을 사용하면 `class`를 상속하여 객체를 일일이 생성하는 번거러움을 줄일 수 있다.

만약 내가 객체를 100개 만든다고 치면 그 내용이 비슷하거나 같다면 `class`를 사용하여 `class`를 상속하여 객체를 생성하면 된다.

```js
class Person {
  constructor(name) {
    this.name = name;
  }
  sayHello() {
    console.log(`Hello, I'm ${this.name}`);
  }
}

const john = new Person('John');
const jane = new Person('Jane');
const jack = new Person('Jack');
// ...
```

등등 하나의 `class`를 만들고 객체를 생성할 때마다 `class`를 상속하여 객체를 생성하면 된다. 이렇게 코딩을 하는 방식을 바로 `객체지향형 프로그래밍(OOP)`라고 한다.

- `class` 문법을 사용하면 `class`를 상속하여 객체를 생성할 때 `class`를 상속하는 객체의 내용을 변경할 수 있다.

```js
class Person {
  constructor(name) {
    this.name = name;
  }
  sayHello() {
    console.log(`Hello, I'm ${this.name}`);
  }
  set name(value) {
    this._name = value;
  }
}

const john = new Person('John');

john.name = 'Jane';
console.log(john); // Person { _name: 'Jane' }
```

이런식으로 내가 원하는 객체의 내용을 자유롭게 함수를 호출하여 별도의 로직을 통해 객체의 상태가 변하게 되면 자동으로 객체의 내용이 변경되는 것도 가능하다. 

그렇게 된다면 `javaScript`의 고질적인 문제인 변수가 변하는 것을 추적하지 못하는 문제를 해결할 수 있다. 어떻게 하는 지 간단하게 예시를 보자

```js
class Person {
  constructor(name) {
    this.name = name;
  }
  sayHello() {
    console.log(`Hello, I'm ${this.name}`);
  }
  set changeName(value) {
    console.log('이름이 바뀝니다.');
    this._name = value;
  }
}

const john = new Person('John');
john.changeName = 'Jane';
console.log(john); // Person { _name: 'Jane' }
```

이렇게 `set`을 사용하여 객체의 내용을 변경하면 객체의 내용이 변경되는 것을 확인할 수 있다.

이것을 살짝 응용하게 된다면 변수의 상태를 저장하고 또 추적하여 변경되었을 때 연계된 데이터를 바꿀 수 있는 `store` 라는 개념을 만들 수 있다.

이렇게 `class`를 사용하면 객체지향형 프로그래밍을 할 수 있고 객체의 상태를 추적할 수 있다.

하지만 개념이 어렵기도 하고 다른 프로그래밍 언어에서 오는 `class`의 개념도 상당한 괴리감을 불러올 수 있기도하다. 하지만 이를 잘만 응용한다면 `javaScript`의 강점을 살릴 수 있는 방법이 될 수 있다.

