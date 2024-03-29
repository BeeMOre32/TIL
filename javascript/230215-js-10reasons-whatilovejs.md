![](https://velog.velcdn.com/images/beemore/post/47109d14-4397-4d11-b512-f59679883e6d/image.png)

# 서론

나는 자바스크립트를 사랑하면서 싫어한다. 왜냐면 자바스크립트는 정말정말정말정말 말도 안되는 것들을 실행을 가능케 해주면서도 당연한 것을 당연하지 않게 만든다. 하지만 누가 나에게 둘중에 무슨 감정(사랑,증오)이 더 크냐고 물어본다면 나는 사랑이 더 크다고 말할 수 있다. 그 이유를 한번 이 글을 통해서 적어보겠다.


## 내가 자바스크립트를 사랑하지만 싫어하는 이유

내가 자바스크립트를 사랑하는 이유는 크게 3가지의 이유가 있다.

1. 대체 불가능함
2. 무긍무진한 가능성
3. 다른 언어와 비교해서 주어지는 자유

위와 같은 이유로 나는 자바스크립트를 사랑한다. 하지만 나는 싫어하기도 하는데 그 이유는 다음과 같다.

1. 다른 언어과 비교해서 주어지는 지유
2. 예측불가능한 결과가 튀어나옴
3. 쉽지만, 난해한 키워드들

먼저는 내가 좋아하는 이유부터 설명을 하겠다.

### 내가 자바스크립트를 사랑하는 이유

#### 대체 불가능

자바스크립트를 좋아할 수 밖에 없는 이유의 첫번째는 바로 대체 불가능한점이다. 말 그대로다. 웹 프론트엔드 개발을 할려면 자바스크립트를 통해서 반드시 만들어야한다. 끝.

자바스크립트는 유일하게 브라우저가 이해할 수 있는 프로그래밍 언어이며, 백엔드와는 다르게 다른 언어를 선택을 할 수 없다. 최근에는 파이썬을 이용하여 파이썬을 굴려줄 수 있는 `pyScript`  나 `pynecone` 같이 파이썬을 이용하여 React 혹은 Next.js 로 바꿔주는 프레임 워크등등이 조금 있는 편이지만, 웹 브라우저가 즉시 이해할수 있는 단어인 자바스크립트로 변환하는 과정이 필요하다. 그 말은 어차피 파이썬으로 작성을 하게 되더라도 별도의 변환과정을 거친 '자바스크립트' 이기 때문에, 결국 프론트엔드 개발을 목표로 하고 있다면 필연적으로 자바스크립트를 배워야하며 사용해야한다.


#### 무긍무진한 가능성

사실 자바스크립트 언어 하나를 배우게 된다면 할 수 있는 것이 정말로 많다. 자바스크립트는 브라우저가 유일하게 이해할 수 있는 언어이기도 하지만, 이를 이용하여 정말 많은 것들을 할 수 있다.

예를 들어서 `node.js` 를 이용한다면 자바스크립트를 통해서 서버를 구축하여 백엔드까지 구현이 가능하며 게임도 만들 수 있다. `three.js` 를 통해서 브라우저에 3d 모델링을 만들어서 더욱 멋있게 웹페이지를 꾸밀수도 있으며, 기존의 자바스크립트의 단점을 보안한 자바스크립트를 기반으로 제작된 `TypeScript`도 굉장히 많은 각광을 받고 있으며, 또 웹페이지를 쉽게 동적 페이지를 만들 수 있는 `React`나 `Vue` 등등 정말 많은 프레임워크 및 라이브러리가 나오고 있다. 이렇게 자바스크립트 하나로 할 수 있는 것들이 있으며 또 지금 이순간에도 자바스크립트는 매일매일 강해지고 있다.

#### 다른 언어와 비교해서 주어지는 자유

일단 다른 언어와 비교했을때 컴파일러가 없기 때문에 내가 반영 한 결과가 즉시 웹페이지에 반영이 된다. 이는 복잡한 타입문제나 창의적(?)인 해결책으로 문제를 해결할 수도 있는 뜻이다. 정말 상상치도 못한 방법으로 문제를 해결하거나 또 내가 씽크빅을 다니고 있다면 그 넘치는 창의력으로 코딩을 하여 웹페이지를 구현 할수도 있다.

### 내가 자바스크립크를 싫어하는 이유

위의 내용까지가 내가 자바스크립트를 사랑하는 이유였다. 그렇다면 내가 자바스크립트를 싫어하는 이유까지 설명을 하겠다.

#### 다른 언어과 비교해서 주어지는 지유

위의 장점에서도 적었다 싶이 자바스크립트는 컴파일러가 없기 때문에 오류가 발생하면 바로 런타임에러가 난다. 이는 정말 최악의 상황이며, 내가 인지하지 못한 최악의 버그가 언제 어디서든지 나타나 서비스를 엉망으로 만들어 버릴 수 있다. 즉 프러덕트 버젼에서 인지하지 못하는 버그가 무사히 트로이 목마처럼 심겨져 버그가 나타날 수 있다는 뜻이다...

그 이유는 정말 무섭게도 자바스크립트에는 최소한의 안정장치만 있을 뿐 내가 타입을 실수하여 `string + boolean` 을 계산 하게 된다면 어떻게 해서든지 해당하는 로직을 실행하여 결과를 뱉어준다.

#### 예측불가능한 결과가 튀어나옴

![](https://velog.velcdn.com/images/beemore/post/2f234073-1bc3-4914-95d3-fff59995d317/image.png)


위의 설명과 연장선이다. 내가 올바르게 코딩을 하더라도 항상 예상치 못한 곳에서 예상하지 못한 결과를 뱉어내는 것이 프로그래밍이다. 하지만 최소한의 안정장치가 없으며 사용자에게 지내치게 실수에 관대하며 자유를 준다면??? 정말 끔직한 에러를 발생시킬수도 있다. 치명적인 버그를 알게 되더라도 경험이 부족하다면 어디서 부터 에러가 생기는지 예측하기도 힘들다. 왜냐면 수많은 자유속에 내가 어떤 실수를 했는지 차근차근 살펴봐야하기 때문이다.

사용자가 쉽게 작성이 고려된 프로그래밍언어의 단점이다.

#### 쉽지만, 난해한 키워드들

자바스크립트는 사실 문법 그 자체는 어렵지 않은 편이다. 하지만 몇몇 키워드들은 내가 무슨 내용을 읽고 있는지 그리고 또 정말 헷갈리는 키워드들이 정말 많다 예를들어서 `this` 라는 키워드는 호출된 위치에 따라서 해당하는 내용이 결정되며 또 호출된 함수가 화살표 함수인지 그냥 함수인지에 따라서 나뉘는데, 이는 처음배우는 사람들에게도 또 다른 프로그래밍언어를 배우고 온 사람들에게도 정말 어렵고 헷갈리는 개념이다.

그렇지만 `this`를 마냥 무시 할 수도 없는 것이 자바스크립트에서 `this` 라는 키워드를 떼어놓기가 힘들다. 그냥 욕하면서도 어쩔 수 없이 사용하게 된다. 이와 같이 중요하지만 서도 개념이 난해한 키워드들이 있다.

# 결론

> ![](https://velog.velcdn.com/images/beemore/post/09a096af-df17-4225-bbe1-87d8bc15532c/image.png)

나는 자바스크립트를 사랑하면서도 싫어한다. 만약 누가 나에게 둘중 어떤 감정이 크다고 물어본다면 나는 고민도 하지 않고, 사랑하는 쪽이 더 크다고 말할 것이다. 자바스크립트는 예측불가능 하고 난해하지만, 그의 가능성은 정말 무긍무진하며 프론트엔드 개발자에게는 떼어낼래야 떼어낼수 없는 애증의 대상이라고, 필자는 생각한다.