# 알아두면 좋은 JS

> 2020.07.20 (월)

### Truthy and Falsy

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