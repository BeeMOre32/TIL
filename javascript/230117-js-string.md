# JavaScript String

## String

- `string` 은 문자열을 나타내는 자료형이다.
- `string` 은 `''` 또는 `""` 로 감싸서 표현한다.
- `string`를 생성할때는 `new` 키워드를 통해서 생성할수도 있다. 하지만 `new` 키워드를 사용하지 않는것이 일반적이다.

```js
const str = 'hello';
const str2 = new String('hello'); 

console.log(typeof str); // string
console.log(typeof str2); // object
```

## String Property

- `string` 은 `length` 라는 프로퍼티를 가지고 있다.
- `length` 는 `string` 의 길이를 나타낸다.

```js
const str = 'hello';

console.log(str.length); // 5
```

## String Method

`string` 은 상당히 많은 메소드를 가지고 있는데 그중 자주 사용되며 유용한 메소드들을 소개한다.

### str.slice()

- `slice()` 는 `string` 의 일부분을 추출하는 메소드이다.
- `slice()` 는 `start` 와 `end` 를 인자로 받는데 `start` 부터 `end` 까지의 문자열을 추출한다.
- `slice()` 는 `start` 와 `end` 를 생략할수 있다. 만약 `start` 를 생략하면 `0` 부터 추출하고 `end` 를 생략하면 `string` 의 끝까지 추출한다.

```js
const str = 'hello';

console.log(str.slice(0, 2)); // he
console.log(str.slice(2)); // llo
console.log(str.slice(-2)); // lo
console.log(str.slice()); // hello
```

### str.split()

- `split()` 는 `string` 을 특정한 문자를 기준으로 나누어 배열로 반환하는 메소드이다.
- `split()` 의 인자로는 `separator` 를 받는데 `separator` 를 기준으로 `string` 을 나눈다.
- `separator` 를 생략하면 `string` 을 한글자씩 나누어 배열로 반환한다.

```js
const str = 'hello world';

console.log(str.split(' ')); // [ 'hello', 'world' ]
console.log(str.split('')); // [ 'h', 'e', 'l', 'l', 'o', ' ', 'w', 'o', 'r', 'l', 'd' ]
```

### str.replace()

- `replace()` 는 `string` 의 일부분을 다른 문자열로 대체하는 메소드이다.
- `replace()` 의 인자로는 `searchValue` 와 `replaceValue` 를 받는데 `searchValue` 를 `replaceValue` 로 대체한다.
- `searchValue` 는 `string` 이나 `RegExp` 를 받을수 있다
- `replaceValue` 는 `string` 이나 `function` 을 받을수 있다.

```js
const str = 'hello world';

console.log(str.replace('world', 'javascript')); // hello javascript
console.log(str.replace(/world/, 'javascript')); // hello javascript
```

### str.toUpperCase()

- `toUpperCase()` 는 `string` 을 대문자로 변환하는 메소드이다.

```js
const str = 'hello world';

console.log(str.toUpperCase()); // HELLO WORLD
```

### str.toLowerCase()

- `toLowerCase()` 는 `string` 을 소문자로 변환하는 메소드이다.

```js
const str = 'HELLO WORLD';

console.log(str.toLowerCase()); // hello world
```

### str.trim()

- `trim()` 는 `string` 의 앞뒤 공백을 제거하는 메소드이다.

```js
const str = ' hello world ';

console.log(str.trim()); // hello world
```

### str.includes()

- `includes()` 는 `string` 에 특정 문자열이 포함되어 있는지 확인하는 메소드이다.
- `includes()` 의 인자로는 `searchString` 을 받는데 `searchString` 이 포함되어 있으면 `true` 를 반환한다.

```js
const str = 'hello world';

console.log(str.includes('hello')); // true
console.log(str.includes('world')); // true
console.log(str.includes('javascript')); // false
```

### str.startsWith()

- `startsWith()` 는 `string` 의 시작이 특정 문자열로 시작하는지 확인하는 메소드이다.
- `startsWith()` 의 인자로는 `searchString` 을 받는데 `searchString` 으로 시작하면 `true` 를 반환한다.

```js
const str = 'hello world';

console.log(str.startsWith('hello')); // true
console.log(str.startsWith('world')); // false
```

### str.endsWith()

- `endsWith()` 는 `str.startsWith()` 와는 반대로 `string` 의 끝이 특정 문자열로 끝나는지 확인하는 메소드이다.
- `endsWith()` 의 인자로는 `searchString` 을 받는데 `searchString` 으로 끝나면 `true` 를 반환한다.

```js
const str = 'hello world';

console.log(str.endsWith('hello')); // false
console.log(str.endsWith('world')); // true
```

## 마치며

오늘은 간단하게 string과 관련된 메소드들을 알아보았다. 이를 활용한다면, 문자열을 다루는데 편하게 다룰수 있을 것 같다.