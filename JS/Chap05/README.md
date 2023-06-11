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

## 콜백을 활용하는 함수

### forEach()

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

### map()

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

### filter()

- `filter` 메소드도 배열이 가지고 있는 함수이다.
- 리턴하는 값이 `true`인 것만 모아서 새로운 배열을 만든다.

```
<script>
    const nums = [0, 1, 2, 3, 4, 5],
        even = nums.filter(function (value) {
            return !(value % 2);
        });

    console.log(even);
</script>
```

## 화살표 함수

- 콜백 함수를 쉽게 표현하고자 `화살표 함수` 방법을 앞서 `map()`, `filter()` 함수에서도 사용하였다.
- 화살표 함수는 `function` 키워드 대신 화살표 `=>`를 사용하며, 다음과 같은 형태로 생성하는 간단한 함수이다.
- Lambda Expression과 유사한 방식이다.

```
(param) => {
    statement;
}
```

- 또한, 다음과 같이 간단하게 사용할 수 있다.

```
(param) => value;
```

- 내부에서 `this` 키워드가 지칭하는 대상이 다르다는 등의 미세한 차이가 있다.
- 만약, 배열의 `map()` 메소드에 이를 사용한다면 다음과 같이 된다.

```
const array = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

array.map((value) => value * value);
```

- 이를 아래와 같이 연속적으로 사용하는 것을 `Method Chaining`이라고 부른다.

```
<script>
    let numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

    numbers
        .filter((value) => !(value % 2))
        .map((value) => value * value)
        .forEach((value) => {
            console.log(value);
        });
</script>
```

## 타이머 함수

- `setTimeout(function, time)` : 특정 시간 후에 함수를 한 번 호출
- `setInterval(function, time)` : 특정 시간마다 함수를 호출
- 아래는 사용 예시이다.

```
<script>
    setTimeout(() => {
        console.log('1s');
    }, 1 * 1000);

    let count = 0;
    setInterval(() => {
        console.log(`count : ${count}`);
        count++;
    }, 1 * 1000);
</script>
```

- 이렇게 설정된 타이머를 종료하고 싶을 때는 아래와 같은 메소드를 사용할 수 있다.
- `clearTimeout(timerID)` : `setTimeout()`으로 설정한 타이머를 제거
- `clearInterval(timerID)` : `setInterval()`으로 설정한 타이머를 제거

```
<script>
    let count = 0,
        id = setInterval(() => {
            console.log(`count : ${count++}`);
        }, 1 * 1000);

    setTimeout(() => {
        console.log(`Terminating timer id ${id}`);
        clearInterval(id);
    }, 5 * 1000);
</script>
```

## 블록과 함수 블록을 이용한 이름 충돌 문제 해결 (즉시 호출 함수)

- JavaScript는 대부분 HTML 내부에 여러 스크립트를 포함하는 형태로 사용하게 되는데, `Identifier`가 충돌할 가능성이 있다.
- 이를 방지하기 위해, `scope`를 분리할 수 있다.
- 또한, <u>**`즉시 호출 함수 (IIFE)`**</u>를 이용하는 방법도 있다.
- 즉시 호출 함수는 `(function () {}) ()`와 같이 이름 없이 사용한다.
- 아래는 그 예시이다.

```
<script>
    // scope 분리
    let pi = 3.14;
    console.log(`pi : ${pi}`);

    {
        let pi = 3.141592;
        console.log(`pi : ${pi}`);
    }

    function sample() {
        let pi = 3.14;
        console.log(`pi : ${pi}`);
    }

    sample();
    console.log(`pi : ${pi}`);

    // IIFE
    (function () {
        console.log('IIFE');
    })();
</script>
```

## 엄격 모드

- `strict mode`는 `use strict` 키워드를 사용하여 설정한다.
- 문자열을 읽어들인 순간부터 코드를 엄격하게 검사하게 된다.
- `data = 10`과 같이 변수를 선언할 수 있지만, `use strict` 아래에선 이러한 부분에 오류가 발생한다.

## 선언적 함수와 익명 함수의 조합

- `익명 함수`는 <u>**순차적인 코드 실행에서 코드가 해당 줄을 읽을 때 생성**</u>되는데, 같은 이름의 익명 함수가 두 번 이상 선언된다면 순차적으로 실행되는 원리에 의해 맨 마지막의 익명 함수가 호출된다.
- 아래의 상황에선 `second`가 출력된다.

```
<script>
    func = function () {
        console.log('first');
    }

    func = function () {
        console.log('second')
    }

    func();
</script>
```

- `선언적 함수`는 <u>**순차적인 코드 실행이 일어나기 전에 생성**</u>되므로, 함수가 선언되기 전 선언된 함수를 호출해도 실행된다. 다만, 선언적 함수 또한 순차적으로 실행되므로 같은 이름의 순차적 함수가 두 번 이상 선언된다면 맨 마지막의 선언적 함수가 호출되게 된다.
- 마찬가지로 아래의 상황에선 `second`가 출력된다.

```
<script>
    func();

    function func() {
        console.log('first');
    }

    function func() {
        console.log('second');
    }
</script>
```

- 만약 2가지 상황을 조합한다면, 같은 이름의 선언적 함수와 익명 함수가 존재할 때 <u>**`선언적 함수`가 먼저 `JIT Runtime`의 `Hoisting`에 의해 생성되고, `익명 함수`가 이를 덮어쓰게**</u> 된다.
- 아래는 두 가지를 조합한 예시인데, `first`가 출력된다.

```
<script>
    func = function () {
        console.log('first');
    }

    function func() {
        console.log('second');
    }

    func();
</script>
```

- 각각 다른 블록에서 같은 이름의 함수를 호출하면, 호출 순서를 예측하기 더욱 힘들어진다.
- 다만, 아래의 결과는 `first` `second`이다. 이렇게 실행되는 이유는, `first`가 있는 `<script>`의 블록이 `Hoisting`에 의해 먼저 적재된다. 따라서, `first`가 먼저 호출된다. 다음으로, `second`가 있는 `<script>`의 블록이 `Hoisting`되게 되는데, 이는 `func()` 함수를 덮어쓰게 된다. 그러므로, 맨 마지막에 있는 `func()` 호출은 `second`를 출력하게 된다.

```
<script>
    func()

    function func() {
        console.log('first');
    }
</script>

<script>
    function func() {
        console.log('second');
    }
</script>

<script>
    func();
</script>
```

## `let` 사용의 의미

- 과거 JavaScript는 `var`이라는 키워드를 사용하여 변수를 선언했다.
- 하지만, `var` 키워드는 이전 코드처럼 덮어쓰는 문제가 발생한다.
- 현대의 JavaScript는 `let` 키워드와 `const` 키워드를 사용해서 변수와 상수를 선언하도록 한다.
- 이러한 키워드는 위와 같은 위험을 원천적으로 차단하기 위해서 사용한다.
- 아래는 해당 예시인데, 오류를 발생시킨다.

```
<script>
    let func = function () {
        console.log('first');
    }

    function func() {
        console.log('second');
    }

    func();
</script>
```

```
Uncaught SyntaxError: Identifier 'func' has already been declared
```

## 4가지 키워드로 정리하는 핵심 포인트

- `콜백 함수`란 매개변수로 전달하는 함수를 의미합니다.
- `화살표 함수`란 익명 함수를 간단하게 사용하기 위한 목적으로 만들어진 함수 생성 문법입니다. `() => {}` 형태로 함수를 만들고, 리턴값만을 가지는 함수라면 `() => value` 값 형태로 사용할 수 있습니다.
- `즉시 호출 함수`란 변수의 이름 충돌을 막기 위해서 안전하게 사용하는 방법입니다.
- 자바스크립트의 문법 오류를 더 발생시키는 `엄격 모드`는 실수를 줄일 수 있는 방법입니다. `use strict`라는 문자열을 블록 가장 위쪽에 배치해서 사용할 수 있습니다.

## 확인 문제

### 1. filter 함수의 콜백 함수 부분을 채워서 (1) 홀수만 추출, (2) 100 이하의 수만 추출, (3) 5로 나눈 나머지가 0인 수만 추출해주세요. 그리고 코드의 실행 결과를 적어보세요.

```
<script>
    let numbers = [273, 25, 75, 52, 103, 32, 57, 24, 76];

    numbers = numbers.filter((value) => value % 2 && value <= 100 && !(value % 5));

    console.log(numbers);
</script>
```

```
[25, 75]
```

### 2. 이전에 반복문에서 살펴보았던 다음과 같은 코드를 배열의 forEach 메소드를 사용하는 형태로 변경해주세요.

- 문제

```
<script>
    const array = ['사과', '배', '귤', '바나나'];

    console.log('# for in 반복문');
    for (const i in array) {
        console.log(i);
    }

    console.log('# for of 반복문');
    for (const i of array) {
        console.log(i);
    }
</script>
```

- 정답

```
<script>
    const array = ['사과', '배', '귤', '바나나'];

    console.log('# for in 반복문');
    array.forEach((value, index, array) => {
        console.log(index);
    });

    console.log('# for of 반복문');
    array.forEach((value, index, array) => {
        console.log(value);
    });
</script>
```

- 출력 결과

```
# for in 반복문
0
1
2
3
# for of 반복문
사과
배
귤
바나나
```

