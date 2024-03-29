# 프로그래밍 모델

프로그래밍 모델은 프로그래머에게 프로그래밍적 관점을 가지게 해주는 개발 방법론이다.

## 프로그래밍 모델의 종류

프로그래밍 모델은 크게 3가지로 나눌 수 있다.

### 1. 절차적 프로그래밍 모델

절차적 프로그래밍 모델은 프로그램을 순차적으로 실행하는 방식으로 프로그램을 작성하는 방법이다. 

절차적 프로그래밍 모델은 프로그램을 순차적으로 실행하기 때문에, 프로그램의 흐름을 제어하기 어렵다. 하지만 작성하기가 쉬우며 
그저 코드를 구현하기만 하면 되는 방법이라서 가독성이 좋은편이다.

주로 C, C++ 등의 언어에서 사용된다.

### 2. 함수형 프로그래밍

함수형 프로그래밍은 말 그대로 하나의 함수가 하나의 기능을 할 수 있도록 하는 프로그래밍 방법이다. 

함수형 프로그래밍은 함수를 이용하여 프로그래밍을 하기 때문에, 함수 하나하나를 하나의 블록으로 만들어서 관리하여 여러블록들을 쌓아 하나의 레고를
만드는 것 처럼 프로그래밍을 한다.

함수형 프로그래밍은 함수명으로만 작동하는 함수결과를 유추할 수 있게 해야하며 하나의 함수가 하나의 기능만을 수행하도록 해야한다. 그렇기 때문에 
상당히 복잡한 프로그램을 작성하기에는 어려움이 있다.

주로 clojure, scala 등의 언어에서 사용된다.

### 3. 객체지향 프로그래밍

객체지향 프로그래밍은 객체를 이용하여 프로그래밍을 하는 방법이다.

하나의 데이터를 가공하는 공장을 만들어서 그 공장을 이용하여 데이터를 가공하는 방식으로 프로그래밍을 한다.
설계에 오랜 시간이 걸리고 설계를 잘못하면 프로그램이 망가지기 쉽다. 하지만 설계를 제대로 하게 되면 유지보수가 쉽고, 재사용성이 높아진다.

객체지향형 프로그래밍의 핵심은 캡슐화 추상성 상속 다형성이다.

추상화는 복잡한 것을 간단하게 만드는 것이다. 최소한의 정보만으로도 객체를 표현할 수 있도록 만드는 것이다.

캡슐화는 객체의 속성과 행위를 하나로 묶는 것이다. 

상속은 부모 클래스의 속성과 행위를 자식 클래스가 물려받는 것이다.

다형성은 하나의 객체가 여러가지 타입을 가질 수 있는 것이다.

주로 java, c# 등의 언어에서 사용된다.

## 모델들의 혼합

사실 위의 방법중에서 완벽하거나 제일 좋은 방법은 없다. 자신에게 맞는 상황이나 자신에게 어울리는 방법을 선택하여 사용하면 된다.

조건과 맥락에 따라서 프로그래밍 모델을 혼합하여 사용할 수도 있다.

