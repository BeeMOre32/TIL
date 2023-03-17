# Design Pattern

디자인 패턴이란?

디자인 패턴은 프로그램을 설계 할때 반복적으로 발생하는 문제를 해결하기 위한 방법이다. 

## 싱글톤 패턴

싱글톤은 하나의 인스턴스만 가지고 있는 패턴이다. 하나의 인스턴스를 기반으로 여러개의 인스턴스를 생성하는 패턴이다. 데이터베이스 연결 모듈에 많이 사용한다.

하지만 보통은 하나의 인스트를 기반으로 여러개의 인스턴스를 생성하지 않고 하나의 인스턴스를 공유하는 방법이 보통 더 많이 사용된다.

js로 싱글톤 패턴을 구현해보자.

```js

class Singleton {
  constructor() {
    if (Singleton.instance) {
      return Singleton.instance;
    }
    Singleton.instance = this;
  }
}

const instance1 = new Singleton();
const instance2 = new Singleton();

console.log(instance1 === instance2); // true

```

하나의 인스턴스를 가지고 있기 때문에, instance1과 instance2는 같은 인스턴스를 가리키고 있다. 

### 싱글톤의 단점

1. TDD(Test Driven Development)를 하기 어렵다. 싱글톤은 하나의 인스턴스만 가지고 있기 때문에, 테스트를 할때 싱글톤을 초기화 해줘야 한다. 

왜냐하면 TDD는 단위별로 테스트를 하기 때문에, 단위 테스트가 서로 독립적이어야 하며 테스트를 어떤 순서로든지 실행히 가능해야 하지만.
싱글톤은 앞서 언급했다 싶이 생성된 하나의 인스턴스를 기반으로 구현하는 패턴이므로 각 테스트마다 독립적인 인스턴스를 생성하기 어렵다.

2. 의존성 주입의 어려움

의존성이란 어떤 클래스가 다른 클래스에 의존하는 관계를 의미한다. 의존성 주입이란 의존성을 주입하는 것을 의미한다.

간단히 말해서 A가 B에 의존한다고 하면, A는 B를 생성하고 사용하는 것이 아니라 외부에서 B를 생성하고 A에 주입하는 것을 의미한다.

그렇게 된다면 B의 변경사항에 대해서 A도 변경해야 하는 문제가 발생한다.
싱글톤 패턴은 의존성이 강하게 결합이 되어있기 때문에, 의존성 주입이 어렵다.

## 팩토리 패턴

팩토리 패턴은 객체를 생성하는 부분을 별도의 클래스로 분리하여 객체 생성을 캡슐화하는 패턴이다. 즉 어려가지의 공정을 거쳐서 객체를 생성하는 것을 팩토리 패턴이라고 한다.

쉽게 말하자면 커피우유 공장에 비유를 할 수 있는데, 커피우유 공장에서는 커피를 만드는 방법과 우유를 만드는 방법이 다르다. 그렇기 때문에 커피를 만드는 공장과 우유를 만드는 공장을 분리하여 만들어야 한다.
그리고 커피와 우유를 만드는 공장을 팩토리라고 한다. 그리고 그 둘을 합쳐서 커피우유를 만드는 공장도 역시 팩토리라고 한다. 

js에서 팩토리를 구현하는 방법은 꽤 간단하다.

```js
const factory = new Object(42);


console.log(factory.constructor.name); // Number
```

위의 코드를 보면, factory는 Number 객체를 생성하는 팩토리이다. 그렇기 때문에 factory.constructor.name은 Number가 출력된다.

```js
class Factory {
  constructor() {
    this.create = function (type) {
      let product;
      if (type === 'product1') {
        product = new Product1();
      } else if (type === 'product2') {
        product = new Product2();
      }
      return product;
    }
  }
}

class Product1 {
  constructor() {
    this.name = 'product1';
  }
}

class Product2 {
  constructor() {
    this.name = 'product2';
  }
}

const factory = new Factory();
const product1 = factory.create('product1');
const product2 = factory.create('product2');
```

조금더 자세히 보자면, 위의 코드는 Product1과 Product2를 생성하는 팩토리이다. 그리고 팩토리를 통해서 Product1과 Product2를 생성한다. 위와 같은 방법을
의존성 주입이라고 해도 되는데, 그 이유는 Product1과 Product2를 생성하는 팩토리를 외부에서 주입하기 때문이다. 즉 Product1과 Product2를 생성하는 팩토리를
외부에서 주입하기 때문에, Product1과 Product2를 생성하는 팩토리를 변경할 수 있다. 그렇기 때문에 언제든지 Product1과 Product2를 생성하는 팩토리를 변경할 수 있다.

장점으로는 객체 생성을 캡슐화 해서 최소한의 모듈화를 가능하게 한다. 그리고 객체 생성을 캡슐화 하기 때문에, 객체 생성에 대한 변경사항이 생겨도 팩토리를 수정하면 되기 때문에
유지보수가 쉽다.

하지만 단점도 마찬가지로 존재하는데 팩토리를 먼저 만들어야 하는 복잡한 과정을 거쳐야 하기 때문에, 코드가 상당히 복잡해 진다.

## 전략 패턴

전략 패턴은 알고리즘을 캡슐화하여 동적으로 알고리즘을 바꿀 수 있게 하는 패턴이다. 즉, 전략 패턴은 알고리즘을 캡슐화하는 것이다.

```js
class Strategy {
  constructor() {
    this.algorithms = {};
  }
  add(name, algorithm) {
    this.algorithms[name] = algorithm;
  }
  get(name) {
    return this.algorithms[name];
  }
}

const strategy = new Strategy();
strategy.add('A', () => console.log('Algorithm A'));
strategy.add('B', () => console.log('Algorithm B'));
strategy.add('C', () => console.log('Algorithm C'));
strategy.get('A')();
strategy.get('B')();
strategy.get('C')();
```

위의 코드를 보면 전략 패턴을 간단하게 구현한 것을 볼 수 있다. 전략 패턴은 내가 원하는 알고리즘을 선택을 할 수 있게 하는 패턴이다. 

근데 솔직히 설명만 들으면 잘 모르겠다... 공부가 더 필요한듯

## 옵저버 패턴

옵저버 패턴은 객체의 상태 변화를 관찰하는 패턴이다. 즉, 객채의 상태의 변화를 감지하고 있다가 변화가 일어나면 그에 맞는 처리를 해줘야 한다.

옵저버 패턴은 우리가 흔히 사용하는 `addEventListener`가 옵저버 패턴이다. 해당하는 이벤트가 일어날떄 까지 메모리에서 대기하고 있다가 이벤트가 발생하면 그에 맞는 처리를 해준다.

또한 react `setState`도 옵저버 패턴이다. `setState`를 호출하면 해당하는 컴포넌트의 상태가 변경되었다는 것을 감지하고 그에 맞는 처리를 해준다.

## 프록시 패턴

프록시 패턴은 옵저버 패턴과 비슷한 패턴이다. 프록시 패턴은 객체의 접근 제어하는 패턴이다. 

예를 들어, 어떤 객체의 접근을 제어하고 싶을때 프록시 패턴을 사용한다. 객체를 직접 접근하지 못하고 오직 프록시의 중간 객체를 통해서만 접근할 수 있게 한다.
그렇게 하면 객체의 접근을 제어할 수 있다. 

이 프록시 패턴은 보안을 위해서 사용할 수도 있고, 객체의 접근을 제어하기 위해서 사용할 수도 있다.

## 이러테리터 패턴

이터레이터 패턴은 컬렉션의 요소를 순회하는 패턴이다. 이터레이터 패턴은 컬렉션의 요소를 순회하는 방법을 통일시키는 패턴이다.

예를 들어, 배열을 순회하는 방법과 객체를 순회하는 방법이 다르다. 그렇기 때문에 이터레이터 패턴을 사용하면 컬렉션의 요소를 순회하는 방법을 통일시킬 수 있다.

## 노출모듈 패턴

노출 모듈 패턴은 모듈을 즉시 실행 함수로 감싸고, 모듈의 내부에 접근할 수 있는 함수를 반환하는 패턴이다. 자바스크립트는 public, private, protected 같은 접근 제어자가 없기 때문에
노출 모듈 패턴을 사용해서 모듈의 내부에 접근할 수 있는 함수를 반환한다.

## mvc 패턴

mvc 패턴은 모델, 뷰, 컨트롤러로 구성된 패턴이다. 모델은 데이터를 담당하고, 뷰는 사용자에게 보여지는 화면을 담당하고, 컨트롤러는 모델과 뷰를 연결해주는 역할을 담당한다.

장점으로는 유지보수가 쉽고, 코드의 재사용성이 높아진다. 그리고 코드의 분리가 잘 되어 있기 때문에 코드의 가독성이 좋아진다. 

## mvp 패턴

mvp 패턴은 mvc패턴에서 파생된 패턴이며 mvc 패턴의 문제점을 보완하기 위해 나온 패턴이다. mvc 패턴의 문제점은 뷰와 모델이 서로 의존적이라는 것이다. 그래서 mvp 패턴에서는 뷰와 모델을 분리시켜서
뷰와 모델이 서로 의존적이지 않게 만들었다.

과거 리덕스에서 사용하던 패턴이 mvp 패턴이였다. 하나의 프레젠터로 보여주고 모델에서는 데이터를 관리하며 뷰와 모델은 서로 의존적이지 않다. 프레젠터를 통해서 뷰와 모델을 연결시켜준다.

## mvvm 패턴

mvvm 패턴은 mvp 패턴에서 파생된 패턴이다. mvp 패턴에서는 뷰와 모델이 서로 의존적이지 않게 만들었지만 뷰와 프레젠터는 서로 의존적이다. 그래서 뷰와 프레젠터를 대신하여 뷰모델로 뷰와 모델을 연결시켜준다.

이 모델은 vue에서 사용하는 모델이다. 뷰모델을 통해서 뷰와 모델을 연결시켜준다.

