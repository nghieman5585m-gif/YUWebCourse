# Chapter 03. HTML5 기본 태그

<details>
<summary>Table of Contents</summary>

- [글자 태그](#글자-태그)

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

## 앵커 태그

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