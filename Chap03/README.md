# Chapter 03. HTML5 기본 태그

<details>
<summary>Table of Contents</summary>

- [글자 태그](#글자-태그)
- [목록 태그](#목록-태그)
- [테이블 태그](#테이블-태그)

</details>

---

## 글자 태그

### 제목과 본문 글자 태그

- 제목 글자 태그에서 h1는 heading(제목)을 의미한다.
- p는 paragraph(단락), br은 break(줄 바꿈), hr은 horizontal rule(수평 줄)을 의미한다.

h1이 가장 큰 제목 태그이고, h6이 가장 작은 제목 태그이다.

```
<body>
    <h1>제목 글자 태그 1</h1>
    <h2>제목 글자 태그 2</h2>
    <h3>제목 글자 태그 3</h3>
    <h4>제목 글자 태그 4</h4>
    <h5>제목 글자 태그 5</h5>
    <h6>제목 글자 태그 6</h6>
</body>
```

### 본문 단락 구분

각 p 태그로 문단을 하나씩 만들 수 있다.

```
<body>
    <h1>제목 글자</h1>
    <p>Lorem Ipsum is simply dummy text of the printing and typesetting industry.</p>
    <p>Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a
        galley of
        type and scrambled it to make a type specimen book.</p>
</body>
```

### 앵커 태그

- a 태그는 anchor를 의미한다.
- 다른 웹 페이지나 웹 페이지 내부의 특정 위치로 이동할 때 사용한다.
- href는 hyper reference를 의미한다.

```
<body>
    <a href="#alpha">Alpha 부분</a>
    <a href="#beta">Beta 부분</a>
    <a href="#gamma">Gamma 부분</a>
    <hr>
    <h1 id="alpha">Alpha</h1>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
    <h1 id="beta">Beta</h1>
    <p>Vivamus elementum pretium tortor, in tincidunt mauris gravida et.</p>
    <h1 id="gamma">Gamma</h1>
    <p>Phasellus sem tortor, volutpat vitae euismod eget, sagittis sed</p>
</body>
```

### 글자 모양 태그

글자 모양 태그는 단독으로 사용하거나, 다른 글자 모양 태그도 넣을 수 있다.

- b (bold) : 굵은 글자
- i (italic) : 기울어진 글자
- small : 작은 글자
- sub (subscript) : 아래 첨자
- sup (superscript) : 위 첨자
- ins (insert) : 밑줄 글자
- del (delete) : 취소선이 그어진 글자

```
<body>
    <h1><b>Lorem ipsum dolor sit amet</b></h1>
    <h1><i>Lorem ipsum dolor sit amet</i></h1>
    <h1><small>Lorem ipsum dolor sit amet</small></h1>
    <h1>Lorem ipsum dolor<sub>sit amet</sub></h1>
    <h1>Lorem ipsum dolor<sup>sit amet</sup></h1>
    <h1><ins>Lorem ipsum dolor sit amet</ins></h1>
    <h1><del>Lorem ipsum dolor sit amet</del></h1>
    <hr>
    <b>Lorem ipsum dolor sit amet</b><br>
    <i>Lorem ipsum dolor sit amet</i><br>
    <small>Lorem ipsum dolor sit amet</small><br>
    Lorem ipsum dolor<sub>sit amet</sub><br>
    Lorem ipsum dolor<sup>sit amet</sup><br>
    <ins>Lorem ipsum dolor sit amet</ins><br>
    <del>Lorem ipsum dolor sit amet</del><br>
</body>
```

## 목록 태그

### 목록 태그 활용

내비게이션 메뉴를 만들 때는 주로 목록 태그를 사용한다.

- ul (unordered list) : 순서가 없는 목록 생성
- ol (ordered list) : 순서가 있는 목록 생성
- li (list item) : 목록 요소 생성

```
<body>
    <ul>
        <li>사과</li>
        <li>바나나</li>
        <li>오렌지</li>
    </ul>

    <ol>
        <li>사과</li>
        <li>바나나</li>
        <li>오렌지</li>
    </ol>

    <ul>
        <!-- 첫 번째 목록 -->
        <li>
            <b>과일</b>
            <ol>
                <li>사과</li>
                <li>바나나</li>
                <li>오렌지</li>
            </ol>
        </li>
        <!-- 두 번째 목록 -->
        <li>
            <b>채소</b>
            <ol>
                <li>상추</li>
                <li>치커리</li>
                <li>양배추</li>
            </ol>
        </li>
    </ul>
</body>
```

## 테이블 태그

표를 만들 때는 테이블 태그를 사용한다.

- table : 표 삽입
- tr (table row) : 표에 행 삽입
- th (table heading) : 표의 제목 셀 생성
- td (table data) : 표의 일반 셀 생성

### 시간표 만들기

테이블 태그는 아래와 같은 속성을 사용할 수 있다.

- table border : 표의 테두리 두께 지정
- th, td의 colspan, rowspan : 셀의 너비, 높이 지정

```
<body>
    <table border="1">
        <thead>
            <tr>
                <th></th>
                <th>월</th>
                <th>화</th>
                <th>수</th>
                <th>목</th>
                <th>금</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>1교시</td>
                <td>영어</td>
                <td>국어</td>
                <td>과학</td>
                <td>미술</td>
                <td>기술</td>
            </tr>
            <tr>
                <td>2교시</td>
                <td>도덕</td>
                <td>체육</td>
                <td>영어</td>
                <td>수학</td>
                <td>사회</td>
            </tr>
        </tbody>
    </table>
</body>
```

### 행렬 병합 표 생성

`colspan` 속성과 `rowspan` 속성을 사용하여 다음과 같이 표를 만들 수 있다.

```
<body>
    <table border="1">
        <tr>
            <th colspan="2">지역별 홍차</th>
        </tr>
        <tr>
            <th rowspan="3">중국</th>
            <td>정산소종</td>
        </tr>
        <tr>
            <td>기문</td>
        </tr>
        <tr>
            <td>운남</td>
        </tr>
        <tr>
            <th rowspan="4">인도 및 스리랑카</th>
            <td>아삼</td>
        </tr>
        <tr>
            <td>실론</td>
        </tr>
        <tr>
            <td>다질링</td>
        </tr>
        <tr>
            <td>닐기리</td>
        </tr>
    </table>
</body>
```

이들의 결과는 다음과 같다.

<html>
<body>
    <table border="1">
        <tr>
            <th colspan="2">지역별 홍차</th>
        </tr>
        <tr>
            <th rowspan="3">중국</th>
            <td>정산소종</td>
        </tr>
        <tr>
            <td>기문</td>
        </tr>
        <tr>
            <td>운남</td>
        </tr>
        <tr>
            <th rowspan="4">인도 및 스리랑카</th>
            <td>아삼</td>
        </tr>
        <tr>
            <td>실론</td>
        </tr>
        <tr>
            <td>다질링</td>
        </tr>
        <tr>
            <td>닐기리</td>
        </tr>
    </table>
</body>
</html>
