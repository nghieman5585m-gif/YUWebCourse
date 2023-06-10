# Chapter 05. 함수

<details>
<summary>Table of Contents</summary>

- [05-1 함수의 기본 형태](#05-1-함수의-기본-형태)
- [05-2 함수 고급](#05-2-함수-고급)

</details>

---

# 05-1 함수의 기본 형태

## 익명 함수

- 함수를 호출했을 때 별다른 이름이 붙어 있지 않은 함수를 `익명 함수(anonymous function)`라고 한다.

```
const func = function () {
    console.log('function');
}
```

## 나머지 매개변수

- 호출할 때 매개변수의 개수가 고정적이지 않은 함수를 `가변 매개변수 함수`라고 부른다.
- JavaScript에서 이러한 함수를 구현할 때는 `나머지 매개변수(rest parameter)`라는 특이한 형태의 문법을 사용한다.
- 기본적인 사용 방법은 다음과 같다.

```
function funcName(... restParameters) { }
```

- 함수의 매개변수 앞에 마침표 3개를 입력하면 매개변수들이 배열로 들어오게 된다.

```
<script>
    function sample(...items) {
        console.log(items);
    }

    sample(1, 2);
    sample(1, 2, 3);
    sample(1, 2, 3, 4);
</script>
```

위 코드를 실행하면, 아래와 같이 배열로 만들어진다.

```
(2) [1, 2]
0: 1
1: 2
length: 2
[[Prototype]]: Array(0)

(3) [1, 2, 3]
0: 1
1: 2
2: 3
length: 3
[[Prototype]]: Array(0)

(4) [1, 2, 3, 4]
0: 1
1: 2
2: 3
3: 4
length: 4
[[Prototype]]: Array(0)
```

- 이를 활용하여, `나머지 매개변수`를 활용한 `min()` 함수를 만들 수 있다.

```
<script>
    // 나머지 매개변수를 사용한 함수 만들기
    function min(...items) {
        // 매개변수 items는 배열처럼 사용한다.
        let result = items[0];

        for (const item of items) {
            if (result > item)
                result = item;
        }

        return result;
    }
</script>
```

## 나머지 매개변수와 일반 매개변수 조합하기

- 다음 패턴과 같이 일반 매개변수와 조합해서 사용할 수 있다.

```
function funcName(param1, param2, ...params) { }
```

- 매개변수로 들어온 자료형이 배열인지, 숫자인지 확인할 수 있어야 하는데, 자료형은 `typeof` 연산자를 활용하여 쉽게 확인할 수 있다.
- 배열에 `typeof` 연산자를 사용하면 `object` 자료형임을 알 수 있는데, 정확한 배열인지 확인하려면 `Array.isArray()` 메소드를 활용해야 한다.

## 전개 연산자

- JavaScript는 배열을 전개해서 함수의 매개변수로 전달해주는 `전개 연산자(spread opeator)`가 있다.

```
<script>
    function sample(...items) {
        console.log(items);
    }

    const array = [1, 2, 3, 4];

    sample(array);
    sample(...array);
</script>
```

```
[Array(4)]
0: (4) [1, 2, 3, 4]
0: 1
1: 2
2: 3
3: 4
length: 4
[[Prototype]]: Array(0)


(4) [1, 2, 3, 4]
```

- 실행 결과를 보면 전개 연산자를 사용하지 않은 경우에는 배열이 매개변수로 들어오고, 전개 연산자를 사용한 경우에는 숫자가 하나하나 전개되어 매개변수로 들어오는 것을 알 수 있다.
- 즉, 아래와 같은 역할을 한다.

```
const array = [1, 2, 3, 4];

sample(array[0], array[1], array[2], array[3]);
sample(...array);
```

## 구 버전 JavaScript

### arguments

- 가변 매개변수는 `arguments` 키워드를 사용해서 매개변수와 관련된 정보를 확인할 수 있다.

```
function sample() {
    console.log(arguments);

    for (let i = 0; i < arguments.length; i++) {
        console.log(arguments[i]);
    }
}
```

### 전개 연산자

- 전개 연산자는 `apply()` 함수를 사용할 수 있다.

```
function sample(...items) {
    console.log(items);
}

const array = [1, 2, 3, 4];
console.log(sample.apply(null, array));
```

### 기본 매개변수

- 기본 매개변수는 매개변수의 값이 `undefined`인지 확인하여 값을 할당할 수 있다.

```
function earnings(wage, hours) {
    wage = typeof(wage) != undefined ? wage : 8590;
    hours = typeof(hours) != undefined ? hours : 52;

    return wage * hours;
}
```

## 7가지 키워드로 정리하는 핵심 포인트

- `익명 함수`란 이름이 없는 함수로, `function () {}` 형태로 만듭니다.
- `선언적 함수`란 이름이 있는 함수로, `function funcName () {}` 형태로 만듭니다.
- 함수의 괄호 안에 넣는 변수를 `매개변수`라고 합니다. 매개변수를 통해 함수는 외부의 정보를 입력받을 수 있습니다.
- 함수의 최종적인 결과를 `리턴값, 반환값`이라고 합니다. 함수 내부에 `return` 키워드를 입력하고 뒤에 값을 넣어서 생성합니다.
- `가변 매개변수 함수`란 매개변수의 개수가 고정되어 있지 않은 함수를 의미합니다. 나머지 매개변수(...)를 활용해서 만듭니다.
- `기본 매개변수`란 매개변수에 기본이 들어가게 하고 싶을 때 사용하는 매개변수입니다.

## 확인 문제

### 1. A부터 B까지 범위를 지정했을 때 범위 안의 숫자를 모두 곱하는 함수를 만들어보세요.

```
<script>
    function multiplyAll(begin, end) {
        let result = 1;

        for (let i = begin; i <= end; i++) {
            result *= i;
        }

        return result;
    }

    console.log(multiplyAll(1, 2));
    console.log(multiplyAll(1, 3));
</script>
```

### 2. 다음 과정에 따라 최대값을 찾는 `max()` 함수를 만들어보세요.

- 매개변수로 `max([1, 2, 3, 4])`와 같은 배열을 받는 `max()` 함수를 만들어보세요.

```
<script>
    const max = function (array) {
        let output = array[0];

        for (const i of array) {
            if (output < i)
                output = i;
        }

        return output;
    }

    console.log(max([1, 2, 3, 4]));
</script>
```

- 매개변수로 `max(1, 2, 3, 4)`와 같이 숫자를 받는 `max()` 함수를 만들어보세요.

```
<script>
    const max = function (...array) {
        let output = array[0];

        for (const i of array) {
            if (output < i)
                output = i;
        }

        return output;
    }

    console.log(max(1, 2, 3, 4));
</script>
```

- `max([1, 2, 3, 4])` 형태와 `max(1, 2, 3, 4)` 형태를 모두 입력할 수 있는 `max()` 함수를 만들어보세요.

```
<script>
    const max = function (...array) {
        let items = array;

        if (Array.isArray(array[0])) {
            items = array[0];
        }

        let output = items[0];

        for (const i of items) {
            if (output < i)
                output = i;
        }

        return output;
    }

    console.log(max(1, 2, 3, 4));
    console.log(max([1, 2, 3, 4]));
</script>
```

---

# 05-2 함수 고급

## 콜백 함수

- JavaScript에서는 함수도 하나의 자료형이므로, 매개변수로 전달할 수 있다.
- 이렇게 매개변수로 전달하는 함수를 `callback 함수`라고 부른다.
- 다음은 선언적 함수를 사용한 예시이다.

```
<script>
    function callThreeTimes(callback) {
        for (let i = 0; i < 3; i++) {
            callback(i);
        }
    }

    function print(i) {
        console.log(`${i}`)
    }

    callThreeTimes(print);
</script>
```

- 혹은, 익명 함수를 사용해 표현할 수 있다.

```
<script>
    function callThreeTimes(callback) {
        for (let i = 0; i < 3; i++) {
            callback(i);
        }
    }

    callThreeTimes(function (i) {
        console.log(`${i}`)
    });
</script>
```

## 콜백 함수를 활용하는 함수: forEach()

- 콜백 함수를 활용하는 가장 기본적인 함수는 `forEach()` 메소드이다.
- `forEach()` 메소드는 배열이 갖고 있는 함수로써 단순하게 배열 내부의 요소를 사용해서 콜백 함수를 호출해준다.
- 다음과 같은 형식으로 사용할 수 있다.

```
function (value, index, array) {}
```

- 아래는 예시이다.

```
<script>
    const numbers = [273, 52, 103, 32, 57];

    numbers.forEach(function (value, index, array) {
        console.log(`${array} : ${index} = ${value}`);
    });
</script>
```

## 콜백 함수를 활용하는 함수: map()

- `map()` 메소드는 콜백 함수에서 리턴한 값을 기반으로 새로운 배열을 만드는 함수이다.
- 또한, 아래는 매개변수로 `forEach()`에 `console.log` 메소드 자체를 넘긴 예시이다.

```
<script>
    let numbers = [273, 52, 103, 32, 57];

    numbers = numbers.map(function (value, index, array) {
        return value * value;
    })

    numbers.forEach(console.log);
</script>
```
