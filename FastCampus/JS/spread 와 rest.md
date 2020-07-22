## spread 와 rest   =>  ...



### spread  (= 펼치다, 흩뿌리다)

```javascript
const slime = {
  name: "슬라임"
};

const cuteSlime = {
  name: "슬라임",
  attr: "cute"
};

const purpleCuteSlime = {
  name: "슬라임",
  attr: "cute",
  color: "purple"
};

console.log(slime);
console.log(cuteSlime);
console.log(purpleCuteSlime);

// Object {name: "슬라임"}
// Object {name: "슬라임", attr: "cute"}
// Object {name: "슬라임", attr: "cute", color: "purple"}
```

- 위와 같이, 앞의 속성을 활용하여 새로운 개체를 만들어야한다면? (...연산자 사용)

```javascript
const slime = {
  name: "슬라임"
};

const cuteSlime = {
  ...slime,
  attr: "cute"
};

const purpleCuteSlime = {
  ...cuteSlime,
  color: "purple"
};

console.log(slime);
console.log(cuteSlime);
console.log(purpleCuteSlime);

// Object {name: "슬라임"}
// Object {name: "슬라임", attr: "cute"}
// Object {name: "슬라임", attr: "cute", color: "purple"}
```

- 만약, 이런 방법을 사용한다면?

```javascript
const slime = {
  name: "슬라임"
};

const cuteSlime = slime;
cuteSlime.attribute = 'cute';

const purpleCuteSlime = cuteSlime;
purpleCuteSlime.color = 'purple';

console.log(slime);
console.log(cuteSlime);
console.log(purpleCuteSlime);


// Object {name: "슬라임", attribute: "cute", color: "purple"}
// Object {name: "슬라임", attribute: "cute", color: "purple"}
// Object {name: "슬라임", attribute: "cute", color: "purple"}
```

=> slime, cuteSlime이 모두 변화되어 있다.
모든 객체가 한 곳을 보고 있기 때문이다.

but, ...연산자를 사용하면 모든 객체가 같지 않다.
서로 다른 객체를 가르키기 때문이다.

- ...연산자를 사용하여 새로운 객체 만든 후, 속성을 바꿔보자
  기존 자리에 새로운 속성이 들어오게 된다. 

```javascript
const slime = {
  name: "슬라임"
};

const cuteSlime = {
  ...slime,
  attr: "cute"
};

const purpleCuteSlime = {
  ...cuteSlime,
  color: "purple"
};

const greenCUteSlime = {
  ...purpleCuteSlime,
  color: "green",
}
console.log(slime);
console.log(cuteSlime);
console.log(purpleCuteSlime);
console.log(greenCUteSlime);

// Object {name: "슬라임"}
// Object {name: "슬라임", attr: "cute"}
// Object {name: "슬라임", attr: "cute", color: "purple"}
// Object {name: "슬라임", attr: "cute", color: "green"}
```



- spread연산자 여러번 사용하기

```javascript
const numbers = [1, 2, 3];
const spreadNUmbers = [...numbers, 1000, ...numbers];

console.log(spreadNUmbers);

// [1, 2, 3, 1000, 1, 2, 3]
```



### rest (객체, 배열, 함수의 파라미터에서 사용 가능)

- **객체**

```javascript
const purpleCuteSlime = {
  name: "슬라임",
  attr: "cute",
  color: "purple"
};

// 객체 비구조화할당을 하면서 ...rest넣어줌
const { color, ...cuteSlime } = purpleCuteSlime;

console.log(color);
console.log(cuteSlime);

// purple  ->  비구조화할당으로 color값이 추출됨
// Object {name: "슬라임", attr: "cute"}  ->  color를 제외한 나머지 값들이 cuteSlime에 들어감
```

```javascript
const purpleCuteSlime = {
  name: "슬라임",
  attr: "cute",
  color: "purple"
};

// 객체 비구조화할당을 하면서 ...rest넣어줌
const { color, ...cuteSlime } = purpleCuteSlime;

console.log(color);
console.log(cuteSlime);

// attr 요소를 추가적으로 빼줌
const { attr, ...slime } = cuteSlime;

console.log(slime);
// Object {name: "슬라임"}
```

- 비구조화할당 시, attr가 아니라 다른 값으로 뺀다면?

```javascript
const purpleCuteSlime = {
  name: "슬라임",
  attr: "cute",
  color: "purple"
};

// 객체 비구조화할당을 하면서 ...rest넣어줌
const { color, ...cuteSlime } = purpleCuteSlime;

console.log(color);
console.log(cuteSlime);

// attr 요소를 추가적으로 빼줌
const { asdf, ...slime } = cuteSlime;

console.log(slime);

// Object {name: "슬라임", attr: "cute"}
// asdf는 없기 떄문에 값이 제대로 추출되지 않음
```



- **배열**
  단, rest가 앞에 올 수 없다. (배열에서의 rest는 맨 마지막에 와야함)

```javascript
const numbers = [0, 1, 2, 3, 4, 5, 6];

const [one, ...rest] = numbers;
console.log(one);
console.log(rest);

// 0
// [1, 2, 3, 4, 5, 6]
```

```javascript
const numbers = [0, 1, 2, 3, 4, 5, 6];

const [one, two, ...rest] = numbers;
console.log(one);
console.log(two);
console.log(rest);

// 0
// 1
// [1, 2, 3, 4, 5, 6]
```



- **함수 파라미터**

```javascript
function sum(a, b, c, d) {
  return a + b + c + d;
}

console.log(sum(1, 2, 3))

// NaN  (4개의 파라미터를 받아야하는데, 3개밖에 안들어왔으므로 Not a Number가 된다.)
```

```javascript
// 해결하고싶다면....
function sum(a, b, c, d) {
  let result = 0;
  if (a) result += a;
  if (b) result += b;
  if (c) result += c;
  if (d) result += d;

  return result;
}

console.log(sum(1, 2, 3));
// 6
//but, 파라미터가 4개가 넘으면 그 수부터는 합에 포함되지 않는다.
```

- 파라미터 부분에서 ...rest사용

```javascript
// 파라미터 부분에서 ...rest를 사용하면, 함수에 넣어준 값들을 하나의 배열로 받아온다.

function sum(...nums) {
  return nums.reduce((acc, current) => acc + current, 0);
  // 내장함수인 reduce 사용
  // acc의 기본값은 0부터 시작. current는 파라미터로 받을 배열을 돌면서 하나씩 배정됨
  // current가 순서대로 acc에 더해진다.
}

console.log(sum(1, 2, 3, 1, 1, 4));
// 12
```



- **함수의 인자**

```javascript
function subtract(x, y) {
  return x - y;
}

const numbers = [1, 2];
// 인자에 ...numbers를 넣어도 결과가 나온다
const result = subtract(...numbers);

console.log(result);
// -1

function sum(...nums) {
  return nums.reduce((acc, current) => acc + current, 0);
}

const numbers = [1, 2, 3, 4, 5, 6, 7, 8];
console.log(sum(...numbers));
// 36
```



### Quiz

함수에 n 개의 숫자들이 파라미터로 주어졌을 때, 그 중 가장 큰 값을 알아내세요.

- **Q**

```javascript
function max() {
  return 0;
}

const result = max(1, 2, 3, 4, 10, 5, 6, 7);
console.log(result);
```

- **A**

```javascript
function max(...numbers) {
  return numbers.reduce((acc, cur) => cur > acc ? cur : acc, numbers[0]);
}

const result = max(1, 2, 3, 10, 5, 6, 7);
console.log(result);

```



## reduce함수

- reduce 메서드는 다음과 같이 사용합니다. 
  배열.reduce((누적값, 현잿값, [인덱스], [요소]) => { return 결과 }, 초깃값);
  return 결과는 한 줄로 이뤄져있어야 함(?)  (ex. 삼항연산자)