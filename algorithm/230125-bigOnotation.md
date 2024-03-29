# Big O Notation

## Introduction

세상에는 다양한 알고리즘이 존재하고 또 각자의 알고리즘을 실행하는 시간이 다르다. 그렇다면 과연 어떤 알고리즘을 사용하여 문제를 해결하는 것이 가장 효율적인지를 알 수 있을 까? 이를 알기 위해서는 알고리즘의 실행 시간을 측정해야 한다.

그렇다면 아래의 간단한 함수를 통해서 알아보자.

```javascript
function sum1(n) {
  let sum = 0;
  for (let i = 1; i <= n; i++) {
    sum += i;
  }
  return sum;
}

function sum2(n) {
  return (n * (n + 1)) / 2;
}

console.log(sum1(1000000000));
console.log(sum2(1000000000));
```

위의 함수는 모든 숫자의 총합을 구하는 함수이다. 하지만 둘의 차이점은 완전히 다른데 그 이유는 하나는 `for loop` 를 순회하며 값을 더하고 있지만 다른 하나는 수학적인 공식을 통해서 값을 구하고 있다. 이렇게 두 함수의 차이점을 비교하며 빅오 표기법을 알아보자.

먼저 위의 `sum1(1000000000)` 함수를 실행하게 되면 n번 만큼 for loop를 순회하며 값을 더하게 되는 데, 만약 n이 1억 이라면 말 그대로 1억번을 실행하여 값을 구하게 된다.
하지만 `sum2(1000000000)` 함수는 수학적인 공식을 통해서 값을 구하게 되는데, 이는 n번 만큼 실행하지 않고 한번의 연산으로 값을 구하게 된다. 결국 n의 값을 크게 가지면 가질수록 `sum1` 함수는 더 많은 연산을 하게 되고 `sum2` 함수는 더 적은 연산을 하게 된다.

그렇다면 당연하게도 `sum1` 함수가 더 오래 걸리며 제일 오래 걸리며 이를 시간을 표현하면 좋겠지만 이를 정확한 시간으로 표기하기에는 각자 함수를 실행하는 환경 및 컴퓨터의 성능차이 및 다양한 환경변수를 들로 인해서 차이가 있기 때문에 그렇게 좋은 방법이 아니다. 그래서 사용되는 방법이 빅오 표기법이다.

## Big O

빅오 표기법이란 알고리즘이 걸리는 시간 또는 공간을 표현하는 방법이다. 빅오 표기법은 `O (N)` 으로 표현되며 `N` 은 입력값의 크기를 의미한다. 빅오 표기법은 `O (1)` , `O (log N)` , `O (N)` , `O (N log N)` , `O (N^2)` , `O (2^N)` , `O (N!)` 등으로 표현이 가능하다.

그렇다면 이를 어떻게 구할 수 있으며 또 어떤 알고리즘이 해당하는지 알아볼 수 있을까? 이를 이해 하기 위해서 아래의 예시를 살펴보자

```js
function sum1(n) {
  let result = 0;
  for (let i = 1; i <= n; i++) {
    result += i;
  }
  return result;
}

function sum2(n) {
  return (n * (n + 1)) / 2;
}

function sumAndDown(n){
    let result = 0;
    for (let i = 1; i <= n; i++) {
        result += i;
    }
    for (let i = n; i >= 1; i--) {
        result += i;
    }
    return result;
}

function sumDuplicate(n){
  let result = 0;
  for (let i = 1; i <= n; i++) {
    for (let i = 0; i <= n; i++) {
        result += i;
    }
  }
}

console.log(sum1(1000000000))
console.log(sum2(1000000000))
console.log(sumAndDown(1000000000))
console.log(sumDuplicate(1000000000))
```

위의 코드를 통해 빅오 표기법을 어떻게 사용하는지 알아보자.

- `sum1` 함수는 `O (N)` 으로 표현이 가능하다. `N` 은 입력값의 크기를 의미하며 `N` 만큼 반복문이 실행되기 때문이다.
- `sum2` 함수는 `O (1)` 으로 표현이 가능하다. `N` 만큼 반복문이 실행 되지 않고 단 하나의 계산식을 통해 값이 나오기 때문에 함수가 실행되는 시간은 입력값의 크기와 무관하다.
- `sumAndDown` 함수는 `O (2N)` 으로 표현이 가능하지만 결국 이를 실행시키게 된다면 단순히 두배의 시간만 걸릴 뿐이지 전체적인 흐름은 `O (N)` 과 동일하게 시간이 소요되는 양상을 보일 것이다.
- `sumDuplicate` 함수는 `O (N^2)` 으로 표현이 가능하다. `N` 만큼 반복문이 실행되며 각 반복문마다 `N` 만큼 반복문이 실행되기 때문이다. 이를 통해 `N` 의 제곱만큼의 시간이 소요된다는 것을 알 수 있다.

위와 같은 예시를 통해서 빅오 표기법을 이해 할 수 있다. 사진으로 확인하자면 아래와 같은 양상을 보인다.

![big-o](https://i0.wp.com/dotnetsimplified.com/wp-content/uploads/2021/10/image-6.png?resize=843%2C484&ssl=1)

더 나아가서 빅오 표기법은 최대한 단순하게 표현을 하기 위해 상수를 제거하고 가장 높은 차수만을 표현한다. 이를 통해 `O (2N)` 은 `O (N)` 으로 표현이 가능하다. 또한 `O (N^2)` 은 `O (N^2)` 로 표현이 가능하다. 그리고 상수가 아무리 더해져 있다고 해도 걸리는 시간은 동일하기 때문에 `O (N^2 + 2N + 1)` 은 `O (N^2)` 로 표현이 가능하다.

단순히 생각하면 가장 큰 값을 남기고 나머지는 크게 신경 쓰지 않는 것이다. 왜냐면 전체적인 그래프의 양상을 따라가는 것이지 디테일한 부분까지 신경 쓰지 않기 때문이다.

# 마무리

이렇게 간단하게 빅오 표기법에 대해서 알아보았습니다. 처음에는 정말 어려웠던 개념이였지만, 막상 배우고 나서 실제 작동하는 코드를 보며 이해를 해보니 그렇게 어렵지 않은 개념이였습니다. 이제는 빅오 표기법을 통해서 어떤 알고리즘이 더 빠른지를 알 수 있게 되었습니다.