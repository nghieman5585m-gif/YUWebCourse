# Chapter 03. 조건문

<details>
<summary>Table of Contents</summary>

- [03-1 if 조건문](#03-1-if-조건문)
- [03-2 switch 조건문과 짧은 조건문](#03-2-switch-조건문과-짧은-조건문)

</details>

---

# 03-1 if 조건문

## 4가지 키워드로 정리하는 핵심 포인트

- `if 조건문`은 조건에 따라 코드를 실행하거나 실행하지 않도록 하기 위해 사용하는 구문입니다.
- `else 구문`은 if 조건문 뒤에 사용하며, if 조건문이 거짓일 때 사용합니다.
- `중첩 조건문`은 조건문을 중첩해서 사용하는 경우를 의미합니다.
- `if else if 조건문`은 중첩 조건문에서 중괄호를 생략한 형태로, 겹치지 않는 3가지 이상의 조건으로 나눌 때 사용합니다.

## 확인 문제

### 1. 다음 예제 중에서 '참입니다'를 출력하는 것은 몇 번일까요?

1.

```
<script>
    const x = 1
    if (x > 4) {
        console.log('참입니다')
    }
</script>
```

2.

```
<script>
    const x = 0
    if (x > 4) {
        console.log('참입니다')
    }
</script>
```

3. 정답

```
<script>
    const x = 10
    if (x > 4) {
        console.log('참입니다')
    }
</script>
```

### 2. 사용자로부터 숫자 2개를 입력받아 첫 번째 입력받은 숫자가 큰지, 두 번째 입력받은 숫자가 큰지를 구하는 프로그램을 다음 빈칸을 채워 완성해보세요.

```
<script>
    const a = Number(prompt('첫 번째 숫자', ''));
    const b = Number(prompt('두 번째 숫자', ''));

    if (a > b) {
        alert('첫 번째로 입력한 숫자가 더 큽니다.');
    } else if (a == b) {
        alert('두 숫자가 같습니다.');
    } else {
        alert('두 번째로 입력한 숫자가 더 큽니다.');
    }
</script>
```

### 3. 중첩 조건문은 2장에서 배운 논리 연산자를 적용해 하나의 if 조건문으로 만들 수 있습니다. 빈칸에 어떤 논리 연산자가 들어가야 할까요?

```
if (x > 10) {
    if (x < 20) {
        console.log('조건에 맞습니다.')
    }
}
```

```
if (x > 10 && x < 20) {
    console.log('조건에 맞습니다.')
}
```

### 4. 사용자에게 숫자를 입력받아 양수, 0, 음수를 구분하는 프로그램을 만들어보세요.

```
<script>
    const a = Number(prompt('숫자를 입력해주세요.', ''));

    if (a == 0) {
        alert('입력한 숫자는 0입니다.');
    } else if (a > 0) {
        alert('입력한 숫자는 양수입니다.');
    } else {
        alert('입력한 숫자는 음수입니다.');
    }
</script>
```

### 5. 사용자에게 숫자를 입력받아 홀수와 짝수를 구분하는 프로그램을 만들어보세요.

```
<script>
    const a = Number(prompt('숫자를 입력해주세요.', ''));

    if (a % 2) {
        alert('입력한 숫자는 홀수입니다.');
    } else {
        alert('입력한 숫자는 짝수입니다.');
    }
</script>
```

### 6. 현재가 몇 월인지 확인하고, 계절을 구분하는 프로그램을 만들어보세요.

```
<script>
    const a = Number(prompt('월을 입력해주세요.', ''));

    if (a >= 3 && a < 6) {
        alert('봄입니다.');
    } else if (a >= 6 && a < 9) {
        alert('여름입니다.');
    } else if (a >= 9 && a < 11) {
        alert('가을입니다.');
    } else {
        alert('겨울입니다.');
    }
</script>
```

---

# 02-2 switch 조건문과 짧은 조건문

## 3가지 키워드로 정리하는 핵심 포인트

- `switch 조건문`은 값에 따라서 조건 분기를 걸어주는 조건문입니다.
- `조건부 연산자`는 A ? B : C와 같은 형태로 피연산자 3개를 갖는 연산자입니다. 조건 분기에 사용할 수 있습니다.
- `짧은 조건문`은 논리 연산자의 특이한 성질을 사용해서 조건 분기에 활용하는 코드입니다.

## 확인 문제

### 1. 다음 코드가 어떤 형태로 실행될지 예측해보세요.

```
<script>
    const result = 100 > 200 ? prompt('값을 입력해주세요.', '') : confirm('버튼을 클릭해주세요.');
    alert(result);
</script>
```

### 2. [누적 예제: 태어난 연도를 입력받아 띠 출력하기] 예제에서 if 조건문을 switch 조건문으로 변경해서 구현해보세요.

```
<script>
    const rawInput = prompt('태어난 해를 입력해주세요.', ''),
        year = Number(rawInput), e = year % 12;

    let result;
    switch (e) {
        case 0:
            result = '원숭이';
            break;
        case 1:
            result = '닭';
            break;
        case 2:
            result = '개';
            break;
        case 3:
            result = '돼지';
            break;
        case 4:
            result = '쥐';
            break;
        case 5:
            result = '소';
            break;
        case 6:
            result = '호랑이';
            break;
        case 7:
            result = '토끼';
            break;
        case 8:
            result = '용';
            break;
        case 9:
            result = '뱀';
            break;
        case 10:
            result = '말';
            break;
        case 11:
            result = '양';
            break;
        default:
            result = '해당하는 동물을 찾을 수 없습니다.';
            break;
    }

    alert(`${year}년에 태어났다면, ${result}띠입니다.`)
</script>
```

### 3. '태어난 연도를 입력받아 띠 출력하기' 예제에서 동물 이름을 쥐부터 '자, 축, 인, 묘, 진, 사, 오, 미, 신, 유, 술, 해'로 변경하고, 입력한 연도의 '갑, 을, 병, 정, 무, 기, 경, 신, 임, 계'를 계산합니다. 이 둘을 합쳐 다음과 같이 출력하는 프로그램을 만들어보세요.

1. 정답

```
<script>
    const rawInput = prompt('태어난 해를 입력해주세요', ''),
        year = Number(rawInput) - 4,
        stems = ['갑', '을', '병', '정', '무', '기', '경', '신', '임', '계', '갑', '을'],
        zodiacs = ['자', '축', '인', '묘', '진', '사', '오', '미', '신', '유', '술', '해'];

    alert(`${year + 4}년은 ${stems[year % 10]}${zodiacs[year % 12]}년입니다.`)
</script>
```

```
태어난 해를 입력해주세요.
> 1991
1991년은 신미년입니다.
```

### 4. 다음 중에서 switch 조건문과 직접적인 관련이 없는 키워드를 고르세요.

1. `switch`
2. `case`
3. `default`
4. 정답 : `else`

### 5. 다음 중에서 다른 실행 결과를 나타내는 코드를 고르세요.

1. `true ? alert('출력A') : alert('출력B')`
2. `false ? alert('출력B') : alert('출력A')`
3. `true || alert('출력A')`
4. 정답 : `true && alert('출력A')`
