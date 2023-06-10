# Chapter 04. HTML5 입력 양식 태그와 구조화 태그

<details>
<summary>Table of Contents</summary>

- [입력 양식 태그](#입력-양식-태그)

</details>

---

## 입력 양식 태그

### 입력 양식 개요

- 입력 양식은 `form` 태그로 영역을 생성하고, 내부에 `input` 태그를 넣어 만든다.
- 다음은 간단한 양식을 만드는 코드와 실행 결과이다.

```
<body>
    <form>
        <input type="text" name="search">
        <input type="submit">
    </form>
</body>
```

<body>
<form>
<input type="text" name="search">
<input type="submit">
</form>
</body>

<br>

- 위의 코드에서 데이터를 입력하고 제출 버튼을 누르면 지정된 방식으로 지정된 장소에 데이터를 전달한다.
- ```<form action="전송 위치" method="전송 방식">``` 형식으로 이를 지정할 수 있다.
- 전송 방식에서, `GET` 방식은 주소에 데이터를 입력해서 전달하고, `POST` 방식은 별도로 데이터를 전송한다.

### 입력 양식 종류

HTML5는 다양한 입력 양식 태그를 지원한다.

- `input` 태그에 `type` 속성을 지정해서 다양한 종류의 기본 임력 양식을 생성할 수 있다.
```
<form>
    <!-- 사용자가 입력하는 입력 양식 -->
    <input type="text" name="text" value="text"><br>
    <input type="password" name="password” value=" password"><br>
    <input type="file" name="file" value="file"><br>
    <input type="checkbox" name="checkbox" value="checkbox"><br>
    <input type="radio" name="radio" value="radio"><br>

    <!-- 보이지 않는 입력 양식 -->
    <input type="hidden" name="hidden" value="hidden"><br>
    
    <!-- 버튼 -->
    <input type="button" value="button"><br>
    <input type="reset" value="reset"><br>
    <input type="submit" value="submit"><br>
    <input type="image" src="http://placehold.it/100x100">
</form>
```

- `label` 태그를 이용하면 `input` 태그의 설명을 지정할 수 있다.
```
<label for="name">이름</label>
<input id="name" type="text">
```