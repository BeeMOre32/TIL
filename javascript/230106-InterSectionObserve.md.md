# IntersectionObserver

## 1. IntersectionObserver

IntersectionObserver 는 브라우저에서 지원하는 API로, 특정 요소가 화면에 보이는 지를 확인해주고 만약 보여지고 있다면, 해당 요소의 정보를 제공해준다.

기존의 스크롤을 사용하는 스크롤애니메이션은 해당 요소의 위치를 계산해야하며 스크롤 이벤트가 발생할 때 마다 계산을 해야하고, 요소를 추적하기 때문에 성능상의 문제가 발생할 수 있다.

하지만, IntersectionObserver 는 해당 요소가 화면에 보이는 지를 확인해주기 때문에 스크롤 이벤트르 일일이 계산하는 번거로움을 덜어줄 수 있어서 꽤나 유용한 API라고 할 수 있다.

## 2. 사용법

### 2.1. 생성자

```javascript
const observer = new IntersectionObserver(callback, options);
```

이렇게 new 키워드로 IntersectionObserver 생성자를 호출하면, IntersectionObserver 객체가 생성된다. setInterval, setTimeout 과 같은 타이머 함수와 비슷하다고 생각하면 된다.

생성자의 첫번째 인자로 콜백함수를 넣어주고, 두번쨰 인자는 옵션을 넣어주면 된다.

### 2.2. 콜백함수

```javascript
const callback = (entries, observer) => {
  entries.forEach((entry) => {
    if (entry.isIntersecting) {
      console.log("보여짐");
    } else {
      console.log("안보여짐");
    }
  });
};
```

콜백함수는 생성자의 첫번째 인자로 넣어주는데, 이 콜백함수는 두개의 인자를 받는다.

첫번째 인자는 entries 이고, 두번째 인자는 observer 이다. entries 는 배열이며, 감시하고 있는 요소들의 정보를 담고 있다. observer 는 IntersectionObserver 객체를 가리킨다.

### 2.3. 옵션

```javascript
const options = {
  root: null,
  rootMargin: "0px",
  threshold: 0,
};
```

옵션으로 넣어줄 수 있는 값은 root, rootMargin, threshold 이다.

- root: 기본값은 null 이며, null 이면 브라우저의 viewport 를 기준으로 감시한다. 만약 root 를 지정하면, root 요소를 기준으로 감시한다.

- rootMargin: 기본값은 0px 이며, root 요소의 margin 값을 지정할 수 있다. rootMargin 을 지정하면, root 요소의 margin 값을 기준으로 감시한다.

- threshold: 기본값은 0 이며, 0 ~ 1 사이의 값을 지정할 수 있다. 0 이면, root 요소의 경계선이 보이는 순간 감시가 시작되고, 1 이면, root 요소가 완전히 보이는 순간 감시가 시작된다.

## 3. 예제

```javascript
const target = document.querySelector("#target");

const callback = (entries, observer) => {
  entries.forEach((entry) => {
    if (entry.isIntersecting) {
     target.classList.add("show");
    } else {
        target.classList.remove("show");
    }
  });
};


const observer = new IntersectionObserver(callback);

observer.observe(target);
```

위의 방식대로 IntersectionObserver 를 사용하면, target 요소가 보여지는 순간 콘솔에 "보여짐" 이라고 출력된다. 이를 응용해서 보여지는 클래스를 설정해서 해당하는 애니메이션을 재생 하는 식으로 응용할 수 있다.

## 4. 참고

[IntersectionObserver](https://developer.mozilla.org/ko/docs/Web/API/IntersectionObserver)

[IntersectionObserver MDN](https://developer.mozilla.org/ko/docs/Web/API/Intersection_Observer_API)

## 5. 결론

이렇게 간단하게 IntersectionObserver 를 배웠습니다. scroll 이벤트를 사용하게 된다면, 번거롭기도 하고 성능 이슈를 야기할 수도 있기 때문에 IntersectionObserver 를 사용하는 것이 좋다고 생각합니다.
게다가 콜백함수로 해당 하는 요소를 직접 컨트롤을 할 수 있기 때문에, IntersectionObserver 를 사용하는 것이 더 좋다고 생각합니다.
