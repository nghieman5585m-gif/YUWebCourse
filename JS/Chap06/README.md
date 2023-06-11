# Chapter 06. 객체

<details>
<summary>Table of Contents</summary>

- [06-1 객체의 기본](#06-1-객체의-기본)
- [06-2 객체의 속성과 메소드 사용하기](#06-2-객체의-속성과-메소드-사용하기)
- [06-3 객체와 배열 고급](#06-3-객체와-배열-고급)

</details>

---

# 06-1 객체의 기본

## 객체의 선언

- 객체는 `Key`와 `Value`로 이루어진 쌍이며, `Python`의 `dict`와 유사하다.
- `C 언어`의 `struct`처럼 `.`을 사용해서 접근할 수 있고, `Python`의 `dict`처럼 `['key']`를 통해 접근할 수도 있다.

```
<script>
    let person = {
        name: 'John',
        age: 30,
        city: 'New York'
    };

    console.log(person.name); // 출력: 'John'
    console.log(person['age']); // 출력: 30
</script>
```

## 속성과 메소드

- 배열 내부에 있는 값을 `요소(element)`라고 한다.
- 객체 내부에 있는 값은 `속성(property)`라고 한다.
- 배열의 요소와 마찬가지로, 객체의 속성도 모든 형태의 자료형을 가질 수 있다.

```
<script>
    const data = {
        number: 42,
        string: "Hello",
        boolean: true,
        array: [1, 2, 3],
        object: { name: "John", age: 30 },
        function: function () {
            console.log("data");
        }
    };

    // 객체 내의 속성 값 변경 가능
    data.number = 99;
    data.string = "Goodbye";
    data.boolean = false;
    data.array.push(4);
    data.object.name = "Jane";
    data.function = function () {
        console.log("Modified function");
    };

    console.log(data);
</script>
```

## 속성과 메소드 구분하기

- 객체의 속성 중 함수 자료형인 속성을 특별히 `메소드(method)`라고 부른다.
- 즉, 객체 내부에 함수 자료형을 가지고 있으며, 파라미터를 입력받아 어떠한 과정을 수행한다면 이는 특별히 `method`라고 부를 수 있다.

## 메소드 내부에서 `this` 키워드 사용하기

- 메소드 내에서 자기 자신이 가진 속성을 출력하고 싶을 때는 자신이 가진 속성임을 분명하게 표시해야 한다.
- Java처럼 `this` 키워드를 사용할 수 있다.

## 동적으로 객체 속성 변경하기

- 객체를 선언하고, 동적으로 객체 속성을 추가할 수 있다.
- 또한, `delete` 키워드를 사용하면 객체의 속성을 삭제할 수 있다.
- 아래는 속성을 동적으로 추가하고, 삭제한 예시이다.

```
<script>
    const person = {};

    person.name = 'John';
    person.age = 30;
    person.city = 'New York';
    console.log(JSON.stringify(person));

    delete person.age;
    console.log(JSON.stringify(person));
</script>
```

## 메소드 간단 선언 구문

- 객체를 생성할 때, 굳이 메소드의 이름과 분리해서 선언할 필요가 없도록 함수 이름을 통해 자동으로 객체 이름을 지정할 수 있다.
- 아래는 해당 예시이다.

```
<script>
    const data = {
        number: 42,
        print (text) {
            console.log(text);
        }
    };

    data.print('sample');
</script>
```

## 화살표 함수를 사용한 메소드

- `function () {}` 형태로 선언하는 `익명 함수`와, `() => {}` 형태로 선언하는 `화살표 함수`는 객체의 메소드로 사용될 때 <u>**`this` 키워드를 다루는 방식이 다르다.**</u>

```
<script>
    const test = {
        a: function () {
            console.log(this);
        },
        b: () => {
            console.log(this);
        }
    }

    console.log('a');
    test.a();

    console.log('b');
    test.b();
</script>
```

```
a
Object
a: ƒ ()
b: ()
[[Prototype]]: Object

b
Window
```

- `a`는 `function` 안에서 실행되기에, `test` 객체를 가리키지만 `b`는 `화살표 함수`가 전체 `scope`에서 실행된다.
- `function` 키워드로 함수를 선언하면 `test` 내부의 객체를 나타내지만, `b`의 경우는 `화살표 함수`가 `C언어`에서 `#define` 개념과 같이 치환되는 개념이랑 유사하다.

## 5가지 키워드로 정리하는 핵심 포인트

- `요소`란 배열 내부에 있는 값을 말합니다.
- `속성`은 객체 내부에 있는 값을 의미합니다.
- `메소드`는 속성 중에 함수 자료형인 것을 의미합니다.
- `this` 키워드는 객체 내부의 메소드에서 객체 자신을 나타내는 키워드입니다.
- 객체 생성 이후에 속성을 추가하거나 제거하는 것을 `동적 속성 추가, 동적 속성 제거`라고 합니다.

## 확인 문제

### 1. 다음과 같은 대상을 자바스크립트 객체로 선언해주세요. 자료형은 알맞다고 생각하는 것으로 지정해주세요.

| 속성 이름 | 속성 값              |
| --------- | -------------------- |
| name      | 혼자 공부하는 파이썬 |
| price     | 18000                |
| publisher | 한빛미디어           |

```
const obj = {
    name: '혼자 공부하는 파이썬',
    price: 18000,
    publisher: '한빛미디어'
};
```

### 2. 다음 객체에 동적으로 속성을 추가하는 문법을 고르세요.

1. `add 객체[속성] = 값`
2. `객체.add('속성', 값)`
3. 정답 : `객체[속성] = 값`
4. `객체[속성].add 값`

### 3. 다음 중 객체에 동적으로 속성을 제거하는 문법을 고르세요.

1. 정답 : `delete 객체[속성]`
2. `객체.delete('속성')`
3. `delete 객체 from 속성`
4. `delete 속성 from 객체`

---

# 06-2 객체의 속성과 메소드 사용하기

## 객체 자료형

- 속성과 메소드를 가질 수 있는 것은 `객체`이다. 예를 들면 `배열`도 객체이다.
- 다음과 같이 `a`라는 배열을 선언하고 배열에 속성을 지정한 후 확인하면 배열이 속성을 가질 수 있다는 것을 알 수 있다.

```
const a = [];
a.sample = 10;
```

- `함수`도 객체이다.

```
function b() {}
b.sample = 10;
```

- `typeof` 연산자를 사용해서 배열의 자료형을 확인하면 `object`라고 객체가 출력된다.
- 그래서, 배열인지 확인하려면 `Array.isArray()` 메소드를 사용한다.
- 함수는 `실행 가능한 객체`라는 특이한 자료로, `typeof` 연산자를 사용해서 자료형을 확인하면 `function`을 출력한다. 함수는 객체의 특성을 완벽하게 가지고 있으므로 함수를 `일급 객체(first-class object, 혹은 first-class citizen)`에 속한다고 표현하기도 한다.

## 기본 자료형

- `string`, `number`, `boolean`은 Literal에 해당하는 기본 자료형이다.
- 이는 `const`에 할당되었을 때 수정할 수 없다.
- `const`는 변수에 할당한 포인터를 수정할 수 없는 개념이다.

- 기본 자료형은 아래와 같이 객체로 선언될 수 있다.

```
const obj = new Number(10);
```

- 이렇게 되면, 객체의 특성을 사용할 수 있다.

## 기본 자료형의 일시적 승급

- 기본 자료형은 해당 자료형에 해당하는 `object` 클래스에 내장된 메소드를 호출할 경우, `object`로 잠시 승급시킨다.
- 즉, 기본 자료형을 객체처럼 사용하면 잠시 작동은 하나 이후 소멸된다.

```
const h = 'hello';
h.sample = 10;
h.sample // undefined
```

## 프로토타입으로 메소드 추가하기

- 어떤 객체의 `prototype`이라는 속성이 객체의 전용 틀이라 할 수 있다. `prototype` 객체에 속성과 메소드를 추가하면 모든 객체에서 해당 속성과 메소드를 사용할 수 있다.
- 아래 예제에서는 객체 내부에서 값을 꺼내쓰는 것처럼 보이기 위해 `valueOf()` 메소드를 사용했다.

```
Number.prototype.power = function (n = 2) {
    return this.valueOf() ** n;
}

const a = 12;
console.log(`a.power() : ${a.power()}`);
console.log(`a.power(3) : ${a.power(3)}`);
console.log(`a.power(4) : ${a.power(4)}`);
```

- 아래의 예시는 `prototype`으로 `contain()` 메소드를 구현한 예시이다.
- `화살표 함수`를 사용할 경우, `this` 객체가 상위 `scope`의 객체를 그대로 사용하기 때문에, `익명 함수`를 통해 생성했다.

```
<script>
    String.prototype.contain = function (str) {
        return this.indexOf(str) >= 0;
    }

    Array.prototype.contain = function (item) {
        return this.indexOf(item) >= 0;
    }

    const a = 'hello';
    console.log('a :', a.contain('a'));

    const b = [1, 2, 3, 4];
    console.log('5 :', b.contain(5));
</script>
```

## Number 객체

### 숫자 N번째 자릿수까지 출력하기 : `toFixed()`

- 소수점 이하 몇 번째 자리까지만 출력하고 싶다면 `toFixed()` 메소드를 사용한다.
- 소수점 아래 2자리까지 출력하고 싶다면 `toFixed(2)`, 3자리까지 출력하고 싶다면 `toFixed(3)` 형태로 사용한다.

### `NaN`과 `Infinity` 확인하기 : `isNaN()`, `isFinite()`

- 어떤 숫자가 `NaN(Not a Number)`인지, 또는 `Infinity(무한)`인지 확인할 때는 `Number.isNaN()` 메소드와 `Number.isFinite()` 메소드를 사용한다.
- 이 메소드들은 숫자 자료 뒤에 온점을 찍고 사용하는 것이 아니라, `Number` 뒤에 점을 찍고 사용한다.

```
const m = Number('asdf'), n = 10 / 0;
Number.isNaN(m);
Number.isFinite(n);
```

## JSON 객체

- `JSON.stringify()` 메소드를 사용하면 객체를 JSON 문자열로 변환한다.
- 역으로, JSON 문자열을 JavaScript 객체로 전개할 때는 `JSON.parse()` 메소드를 사용한다.

## 4가지 키워드로 정리하는 핵심 포인트

- 실체가 있는 것 중에서 객체가 아닌 것을 `기본 자료형`이라고 하며, 숫자, 문자열, 불 자료형이 대표적인 예입니다.
- 객체를 기반으로 하는 자료형을 `객체 자료형`이라고 하며, `new` 키워드를 활용해서 생성합니다.
- `기본 자료형의 승급`이란 기본 자료형이 일시적으로 객체 자료형으로 변화하는 것을 의미합니다.
- `prototype`에서 객체란 객체의 틀을 의미하며, 이곳에 속성과 메소드를 추가하면 해당 객체 전체에서 사용할 수 있습니다.

## 확인 문제

### 1. 다음 코드의 실행 결과를 예측해보세요. 예측과 다른 결과가 나온다면 왜 그런지 생각해보세요.

- 문제

```
<script>
    const num = 52000;

    num.won = function () {
        return this.valueOf() + won;
    }

    console.log(num.won());
</script>
```

- 수정된 코드

```
<script>
    const num = new Number(52000);

    num.won = function () {
        return this.valueOf() + ' won';
    }

    console.log(num.won());
</script>
```

- 정답

1. `const num`에서 `52000`은 기본 자료형이므로, `new Number(52000)`으로 변경하여 객체 자료형으로 변경해주어야 한다.
2. `return this.valueOf() + won;`에서 `won`은 키워드가 정해져있지 않기 때문에, 문자열인 `' won'` 형식으로 바꿔주어 문자열이 concatenation되게 해주어야 한다.

### 2. 다음 코드의 실행 결과를 예측해보세요.

```
<script>
    function printLang(code) {
        return printLang._lang[code]
    }
    printLang._lang = {
        ko: '한국어',
        en: '영어',
        ja: '일본어',
        fr: '프랑스어',
        es: '스페인어'
    }
    console.log('printLang("ko"):', printLang('ko'))
    console.log('printLang("en"):', printLang('en'))
</script>
```

```
printLang("ko"): 한국어
printLang("en"): 영어
```

### 3. 모질라 문서에서 Math 객체와 관련된 내용을 읽고 사인 90도의 값을 구해보세요. 참고로 사인 90도는 1입니다. 아주 단순하게 생각해서 구현하면 0.8939966636005579라는 결과가 나옵니다. 0.8939966636005579가 나왔다면 왜 그런지, 그리고 이를 어떻게 해야 제대로 사용할 수 있는지 구글 검색 등을 활용해서 알아보고 코드를 수정하세요.

```
<script>
    const degree = 90;

    console.log(degree * (Math.PI / 180));
</script>
```

### 4. 다음 중 어떤 종류의 객체들이 모두 공유하는 속성과 메소드를 추가할 때 사용하는 객체의 이름을 골라주세요.

1. `classProp`
2. 정답 : `prototype`
3. `sample`
4. `frame`

### 5. 다음과 같은 배열을 이름(name)으로 오름차순 정렬해주세요.

```
<script>
    const books = [{
        name: '혼자 공부하는 파이썬',
        price: 18000,
        publisher: '한빛미디어'
    }, {
        name: 'HTML5 웹 프로그래밍 입문',
        price: 26000,
        publisher: '한빛아카데미'
    }, {
        name: '머신러닝 딥러닝 실전 개발 입문',
        price: 30000,
        publisher: '위키북스'
    }, {
        name: '딥러닝을 위한 수학',
        price: 25000,
        publisher: '위키북스'
    }];

    console.log(_.orderBy(books, (book) => book.name));
</script>
```

---

# 06-3 객체와 배열 고급

## 속성 존재 여부 확인

```
<script>
    const person = {
        name: 'John',
        age: 30,
        city: 'New York'
    };

    if (person.name !== undefined) {
        console.log('name exists');
    } else {
        console.log('name not exists');
    }

    if (person.name) {
        console.log('name exists');
    } else {
        console.log('name not exists');
    }

    person.name || console.log('name not exists');

    person.hobby = object.hobby !== undefined ? object.hobby : 'unknown hobby';
</script>
```

## 배열 기반의 다중 할당

- `Python`과 비슷한 방법으로 배열의 내용을 다중 할당할 수 있다.

```
let [a, b] = [1, 2];
[a, b] = [b, a];
```

- 그리고, 아래와 같이 할당하면 `a, b, c`만 할당된다.

```
let array = [1, 2, 3, 4, 5];
const [a, b, c] = array; // a: 1, b: 2, c: 3
```

## 전개 연산자를 활용한 Deep Copy

- `[...array]`를 이용하면 배열의 깊은 복사가 가능하다.
- 객체 전개 연산자인 `{...object}`를 이용하면 객체 또한 깊은 복사가 가능하다.
- 객체의 경우, 연산자를 전개하고 변경하고 싶은 속성을 다시 정의하면 이를 오버라이드한다.
- 전개 연산자의 위치를 조정하여 전개하고자 하는 객체의 순서를 변경할 수 있다.

## 4가지 키워드로 정리하는 핵심 포인트

- `속성 존재 여부 확인`은 객체 내부에 어떤 속성이 있는지 확인하는 것을 의미합니다. 객체에 없는 속성은 접근하면 `undefined`가 나오는데, 이를 활용하면 됩니다.
- `다중 할당`은 배열과 객체 하나로 여러 변수에 값을 할당하는 것을 의미합니다.
- `얕은 복사(참조 복사)`는 복사 행위가 단순하게 다른 이름을 붙이는 형태로 동작하는 복사를 의미합니다.
- `깊은 복사`는 복사 후 두 객체를 완전하게 독립적으로 사용할 수 있는 복사를 의미합니다.
