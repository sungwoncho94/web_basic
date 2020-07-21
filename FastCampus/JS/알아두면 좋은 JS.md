# 알아두면 좋은 JS

> 2020.07.20 (월)

## Truthy and Falsy

```javascript
// JS에서 null, undefined.. 등의 값을 false값으로 간주한다 => falsy한 값

console.log(!null); // true
console.log(!undefined); // true
console.log(!0); // true
console.log(!" "); // false
console.log(!""); // true
console.log(!NaN); // true
console.log(!false); // true
// 이를 제외한 모든 값은 truthy한 값이다.
```



```javascript
const value = null;

const truthy = value ? true : false;
console.log(truthy);

const isTrue = !!value;
// 1. !value -> value가 true라면 false가 될 것이고, false라면 true가 될 것
// 2. !!value -> !value의 반대 결과가 나올 것 -> value의 결과와 같아질 것

```



### Falthy 한 값 5가지

- undifined
- null
- 0
- ''
- NaN
- false



### && (and연산자)의 활용

=> && 앞에 true || truthy한 값일 때는 뒤의 값이 반환되고, 아니라면 앞의 값이 반환됨
=> 결과가 true일 때(값이 있을 때), 어떤 값을 반환함

```javascript
// && 연산자 사용 시, 앞에가 true일 때 결과값은 뒤에꺼가 반환됨
console.log(true && 'hello');  // 'hello'
console.log('hello' && 'bye');  // 'bye'

// truthy한 값이 앞에 올 때도 뒤에 값이 반환됨
console.log(1 && 'hello') // hello

// 앞의 값이 falsy한 값일 경우, false가 아니라 앞에 온 falsy한 값이 반환됨
console.log(null && 'hello')  // null
console.log('' && 'hello') // ''
console.log(0 && 'hello') // 0
console.log(false && 'bye');  // false
```



### || (or 연산자)의 활용

=>  || 앞에 false나 falsy한 값일 때는 뒤의 값이 반환되고, 아니라면 앞의 값이 반환됨
=> 어떤 값이 없을 때, 대신 사용할 값을 || 뒤에 넣어줌

```javascript
// 앞의 값이 false일 때만 뒤의 값을 반환함
console.log(false || 'hello');
console.log('' || 'hello');

// 앞의 값이 true일 때는 뒤를 보지 않고 앞의 값을 반환함
console.log(1 || 'hello');
console.log(true || 'hello');
```

```javascript
const Dog = {
  name: ""
};

function getName(animal) {
  // animal이 true일 경우에 (이름이 있을 때) animal의 name을 name 변수에 저장함
  const name = animal && animal.name;
  if (!name) {
    return "이름이 정해지지 않았네요!";
  }
  return name;
}

const name = getName(Dog);
console.log(name);

```

위 코드를 더 간단하게 써보기

```javascript
const Dog = {
  name: ""
};

function getName(animal) {
  // animal이 true일 경우에 (이름이 있을 때) animal의 name을 name 변수에 저장함
  const name = animal && animal.name;
  // name이 없으면, 뒤의 문자열을 대신 반환함
  return name || "이름이 정해지지 않았네요!";
}

const name = getName(Dog);
console.log(name);
```



## 함수의 기본 파라미터

- 함수를 사용할 때 넣어야 할 파라미터를 넣지 않았을 때 기본값으로 사용하는 값 설정

```javascript
function calculateCircleArea(r) {
    // 만약, r의 값이 있으면 radius는 r이 되고, r값이 없으면 radius는 1이 된다.
    const radius = r || 1;
    return Math.PI * radius * radius;
}

const area = calculateCircleArea();
const area2 = calculateCircleArea(4);
console.log(area);  // 3.141592..
console.log(area2);  // 50.265...

```

```javascript
// r의 기본값을 지정하는 방법

function calculateCircleArea(r = 1) {
    return Math.PI * r * r;
}

const area = calculateCircleArea();
const area2 = calculateCircleArea(4);
console.log(area);  // 3.141592..
console.log(area2);  // 50.265...
```

```javascript
// 화살표함수로 함수 작성해보기

const calculateCircleArea = (r = 1) => Math.PI * r * r;

const area = calculateCircleArea();
const area2 = calculateCircleArea(4);
console.log(area);  // 3.141592..
console.log(area2);  // 50.265...
```



## 조건문

### include

```javascript
function isAnimal(text) {
    return (
        text === "고양이" || text === "개" || text === "거북이" || text === "너구리"
    );
}

console.log(isAnimal("개"));
console.log(isAnimal("책상"));
```

- js 내장함수 (includes) 사용해서 비교하기

```javascript
function isAnimal(text) {
  const animals = ["고양이", "개", "거북이", "너구리"];
  return animals.includes(text);
}

console.log(isAnimal("개"));
console.log(isAnimal("책상"));
```

- 화살표함수로 바꾸기

```javascript
const inAnimal = (text) => ['고양이', '개', '거북이', '너구리'].includes(text);

console.log(isAnimal("개"));
console.log(isAnimal("책상"));
```



```javascript
function getSound(animal) {
  if (animal === '개') return '멍멍';
  if (animal === '비둘기') return '9999';
  if (animal === '참새') return '짹쨱';
  if (animal === '고양이') return '야옹';
  return '고-요';
}

console.log(getSound('개'));  // 멍멍
console.log(getSound('사람'));  // 고-요
```

- switch문 사용 (비추)

```javascript
function getSound(animal) {
  switch(animal) {
    case '개':
      return '멍멍';
    case '비둘기':
      return '9999';
    default:
      return '고--요';
  }
}

console.log(getSound('개'));  // 멍멍
console.log(getSound('사람'));  // 고--요

```

- 객체 활용하기

```javascript
function getSound(animal) {
  // 객체 활용하기
  const sounds = {
    개 : '멍멍',
    고양이 : '야옹',
    비둘기 : '9999',
  };
  // key value 형태로 animal을 key로 받아와서 객체의 value값을 조회한다
  return sounds[animal] || '고..요';
}

console.log(getSound('개'));  // 멍멍
console.log(getSound('사람'));  // 고..요
```

- 조건에 따라 해야하는 작업이 달라질 때 => 객체에 함수를 넣어서 함수를 호출할 수도 있다.

```javascript
function makeSound(animal) {
  const tasks = {
    개: () => {
      console.log("멍멍");
    },
    비둘기() {
      console.log("99999");
    },
    // 익명함수를 사용할 때는 비둘기처럼 function을 생략해서 쓰는게 더 좋다.
    사람: function() {
      console.log("안녕?");
    }
  };

  const task = tasks[animal];

  if (!task) {
    console.log("...?");
    return;
  }
  task();
}

makeSound("개");
makeSound("비둘기");
makeSound("고양이");
// 멍멍 
// 99999 
// ...? 
```

