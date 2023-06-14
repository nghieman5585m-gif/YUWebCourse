# Chapter 08. 예외처리

<details>
<summary>Table of Contents</summary>

- [08-1 구문 오류와 예외](#08-1-구문-오류와-예외)
- [08-2 예외 처리 고급](#08-2-예외-처리-고급)

</details>

---

# 08-1 구문 오류와 예외

## 기본 예외처리

- 조건문을 사용해서 예외가 발생하지 않게 만드는 것을 `기본 예외 처리`라고 부른다.
- 아래는 단순히 `h1` 요소가 없을 경우 해당 작업을 수행하지 않는 예시이다.

```
<script>
    document.addEventListener('DOMContentLoaded', () => {
        const h1 = document.querySelector('h1');
        if (h1) {
            h1.textContent = 'test';
        } else {
            console.log('Element not found');
        }
    });
</script>
```

## 고급 예외처리

- `try catch finally` 구문으로 예외를 처리하는 방법을 `고급 예외 처리`라고 부른다.
- `finally`는 예외의 발생 여부와 상관없이 무조건 실행된다.

### `finally` 구문을 사용하는 이유

- 아래의 코드는 `A`, `B`, `C`가 모두 출력된다.

```
<script>
    function test() {
        try {
            alert('A');
            throw 'Exception';
        } catch (exception) {
            alert('B');
            return;
        } finally {
            alert('C');
        }
    }

    test();
</script>
```

- `finally` 구문은 `catch` 구문에서 `return`이나 `break` 혹은 `continue` 문을 만나면 결과가 달라지게 된다.
- `finally` 문을 사용하여 반드시 실행해야 할 상황에 코드를 실행할 수 있다.

## 4가지 키워드로 정리하는 핵심 포인트

- `구문 오류`는 프로그램 실행 전에 발생하는 코드의 문법적인 문제로 발생하는 오류를 의미합니다.
- `예외`는 프로그램 실행 중에 발생하는 모든 오류를 의미합니다.
- `예외 처리`는 예외가 발생했을 때 프로그램이 중단되지 않게 하는 처리입니다. 구문 오류는 예외 처리로 처리할 수 없습니다.
- `try catch finally 구문`은 `try` 구문 안에서 예외가 발생하면 `catch` 구무네서 처리하고, `finally` 구문은 예외 발생 여부와 상관없이 실행해야 하는 작업이 있을 때 사용합니다.

## 확인 문제

### 1. 다음 코드 중에서 구문 오류가 발생하는 코드를 고르세요.

- (작성자) `SyntaxError`를 `구문 오류`라고 한답니다. 이 문제 때문에 처음으로 정답지를 봤습니다.

1. 정답

```
<script>
    cons a = 10
    console.log(a * a)
</script>
```

- `Uncaught SyntaxError: Unexpected identifier 'a'`

2.

```
<script>
    console.llog('안녕하세요')
</script>
```

- `Uncaught TypeError: console.llog is not a function`

3.

```
<script>
    const number = 10
    consle.log(number() + number())
</script>
```

- `Uncaught ReferenceError: consle is not defined`

4.

```
<script>
    const number = 20
    console.log(number[20])
</script>
```

- `undefined`

### 2. 예외 처리 구문의 조합으로 옳지 않은 것을 고르세요.

- (작성자) 저자 분이 이 부분을 작성할 때 졸으셨나 봅니다. 1번과 4번 지문이 같습니다.

1. `try {} catch (exception) {}`
2. `try {} finally {}`
3. 정답 : `try {} finally {} catch (exception) {}`
4. `try {} catch (exception)`

### 3. 다음 코드 중에서 `try catch finally` 구문으로 처리할 수 없는 코드를 고르세요.

- (작성자) 여기서 또 `구문 오류`라는 단어가 등장합니다. 저자 분은 `구문 오류`라는 단어를 참 좋아하시는 것 같네요.

1.

```
<script>
    error.error.error()
</script>
```

2.

```
<script>
    let array = [1, 2, 3, 4, 5]
    console.log (array[-100])
</script>
```

3. 정답

```
<script>
    let number = NEW Number(10)
</script>
```

4.

```
<script>
    let number = 20
    number()
</script>
```

---

# 08-2 예외 처리 고급

- `throw new Error('Detailed error message')` 처럼 `Exception`을 발생시킬 수 있다.

## 2가지 키워드로 정리하는 핵심 포인트

- `예외 객체`는 예외와 관련한 정보를 담은 객체를 의미합니다.
- `throw 구문`은 예외를 강제로 발생시킬 때 사용하는 구문입니다.

## 확인 문제

### 1. 다음 중 예외를 강제로 발생시킬 때 사용하는 키워드는 무엇인가요?

1. `raise`
2. `exception`
3. `trigger`
4. 정답 : `throw`

### 2. 다음 중에서 예외 객체를 e라는 변수로서 추출하는 방법으로 옳은 것을 골라주세요.

- (작성자) ?????

1. 정답

```
<script>
    try {

    } catch (e) {

    }
</script>
```

2.

```
<script>
    try (e) {

    } catch {

    }
</script>
```

3.

```
<script>
    try {

    } catch {
        const e = this.exception
    }
</script>
```

4.

```
<script>
    try {

    } catch as e {

    }
</script>
```

### 3. 다음 코드의 실행 결과를 예측해주세요.

- 코드

```
<script>
    try {
        console.log('try 구문입니다')
        const array = ['사과', '바나나', '귤']
        array.forEach(() => {
            throw '예외를 강제로 발생시킵니다'
        })
    } catch (e) {
        console.log('catch 구문입니다')
    } finally {
        console.log('finally 구문입니다')
    }
</script>
```

- 결과

```
try 구문입니다
catch 구문입니다
finally 구문입니다
```
