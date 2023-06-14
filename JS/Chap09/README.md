# Chapter 09. 클래스

<details>
<summary>Table of Contents</summary>

- [09-1 클래스의 기본 기능](#09-1-클래스의-기본-기능)

</details>

---

# 09-1 클래스의 기본 기능

## 클래스 선언하기

- 클래스는 `Java`와 비슷하게, 다음과 같은 형태로 생성한다.

```
class className {

}
```

- 인스턴스 생성도 `Java`와 비슷하다.

```
new className();
```

- 다음은 `Student` 클래스의 생성 예시이다.

```
<script>
    class Student {

    }

    const student = new Student(), students = [];
    for (let i = 0; i < 5; i++)
        students.push(new Student());
</script>
```

## 생성자

- 생성자는 `constructor ()` 방식으로 생성한다.
- 아래는 해당 예시이다.

```
<script>
    class Student {
        constructor(name, kor, eng, math) {
            this.name = name;
            this.kor = kor;
            this.eng = eng;
            this.math = math;
        }
    }

    const students = [],
        getRandScore = () => {
            return Number(((Math.random() * 100) % 100).toFixed(0));
        }

    for (let i = 0; i < 5; i++) {
        students.push(new Student(`Student ${i + 1}`,
            getRandScore(), getRandScore(), getRandScore()));
    }
</script>
```

## 메소드

- `메소드`는 클래스 내부에 선언하면 된다.
- 아래는 그 예시이다.

```
<script>
    class Student {
        constructor(name, kor, eng, math) {
            this.name = name;
            this.kor = kor;
            this.eng = eng;
            this.math = math;
        }

        getSum() {
            return this.kor + this.eng + this.math;
        }

        getAvg() {
            return this.getSum() / 3;
        }

        toString() {
            return `${this.name} : Total ${this.getSum()}, Average ${this.getAvg().toFixed(0)}`;
        }
    }

    const students = [],
        getRandScore = () => {
            return Number(((Math.random() * 100) % 100).toFixed(0));
        };

    for (let i = 0; i < 5; i++) {
        students.push(new Student(`Student ${i + 1}`,
            getRandScore(), getRandScore(), getRandScore()));
    }

    for (const s of students) {
        console.log(s + '');
    }
</script>
```

## 5가지 키워드로 정리하는 핵심 포인트

- `객체 지향 패러다임`은 객체를 우선적으로 생각해서 프로그램을 만든다는 방법론을 의미합니다.
- `추상화`는 프로그램에서 필요한 요소만을 사용해서 객체를 표현하는 것을 의미합니다.
- `클래스`는 객체를 안전하고 효율적으로 만들 수 있게 해주는 문법입니다.
- `인스턴스`는 클래스를 기반으로 생성한 객체를 의미합니다.
- `생성자`는 클래스를 기반으로 인스턴스를 생성할 때 처음으로 호출되는 메소드입니다.

## 확인 문제

### 1. 다음 중에서 옳지 않은 것을 골라주세요.

1. 클래스 내부에서 `this` 키워드는 객체(인스턴스)를 의미합니다.
2. 정답 : 클래스 생성자를 만들 때는 클래스 이름과 같은 메소드를 사용합니다.
3. 객체(인스턴스)가 가진 속성과 메소드에 접근할 때는 온점(.)을 사용합니다.
4. 클래스는 `class` 키워드로 만듭니다.
