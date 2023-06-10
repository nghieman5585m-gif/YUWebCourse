# Chapter 03. HTML5 기본 태그의 연습 문제 풀이

---

### 01. 다음 괄호 안을 채우시오.

1. h는 `heading` 의 약자입니다.
2. p는 `paragraph` 의 약자입니다.
3. br은 `line break` 의 약자입니다.
4. hr은 `horizontal rule` 의 약어입니다.
5. a는 `anchor` 의 약자입니다.
6. href는 `hypertext reference` 의 약어입니다.
7. b는 `bold` 의 약자입니다.
8. i는 `italic` 의 약자입니다.
9. sub는 `subscript` 의 약자입니다.
10. sup는 `superscript` 의 약자입니다.
11. ins는 `insert` 의 약자입니다.
12. del은 `delete` 의 약자입니다.
13. ul은 `unordered list` 의 약어입니다.
14. ol은 `ordered list` 의 약어입니다.
15. li는 `list item` 의 약어입니다.
16. tr은 `table row` 의 약어입니다.
17. th는 `table header` 의 약어입니다.
18. td는 `table data` 의 약어입니다.
19. HTML 본문에 공백을 여러 번 넣고 싶을 때는 `&nbsp;` 를 사용합니다.
20. HTML 본문에 < 기호를 넣고 싶을 때는 `&lt;` 를 사용합니다.
21. HTML 본문에 > 기호를 넣고 싶을 때는 `&gt;` 를 사용합니다.

### 02. 다음 질문에 OX를 표시하시오.
1. h1 태그가 가장 큰 제목 태그고, h6 태그가 가장 작은 제목 태그입니다. `(O)`
2. a 태그의 링크를 지정할 때는 ~~link~~`href` 속성을 사용합니다. `(X)`
3. 목록은 ul 태그와 ol 태그 내부에 li 태그를 넣어서 만듭니다. `(O)`
4. 목록 내부에 목록을 중첩할 수도 있습니다. `(O)`
5. th 태그와 td 태그의 rowspan 속성과 colspan 속성을 사용하면 마이크로소프트 워드 등 스프레드시트에 있는 셀 병합 기능처럼 테이블의 셀을 병합할 수 있습니다. `(O)`
6. img 태그, audio 태그, video 태그는 모두 ~~텍스트~~`미디어` 등 내용물을 가질 수 ~~없습니다.~~`있습니다.` `(X)`
7. audio 태그, video 태그에 controls 속성을 지정할 때 표시되는 재생 제어 버튼들은 모든 웹 브라우저에서 모양, 형태가 ~~같습니다.~~`다르게 보일 수 있습니다.` `(X)`

### 03. 다음 중 이미지의 대체 문자를 지정할 때 사용하는 속성은?
1. text
2. alter
3. 정답 : __alt__ (`alt` 속성은 `alternative text`의 줄임말이다.)
4. imgtxt


### 04. 다음 중 a 태그로 빈 링크를 만들 때, href 속성에 일반적으로 사용되는 기호는?
1. 정답 : __\#__
2. @
3. \*
4. \+

### 05. 다음 중 HTML5 표준에 없는 태그는?
1. table (테이블의 시작과 끝을 나타내며, `tr` 태그를 통해 행을 만들고, `td` 태그를 통해 각 셀을 만들 수 있다.)
2. tfoot (테이블의 하단 부분을 나타낸다.)
3. thead (테이블의 상단 부분을 나타내며, `tr` 태그와 `th` 태그를 사용한다.)
4. 정답 : __tcontent__

### 06. 다음 중 HTML5 표준에 없는 태그는?
1. 정답 : __big__
2. small (작은 글씨를 나타낸다.)
3. b (굵은 글씨를 나타낸다.)
4. i (이탤릭 글씨를 나타낸다.)

### 07. 다음 중 audio 태그와 video 태그 내부에 넣어 웹 브라우저가 재생할 수 있는 파일 확장자 관련 문제를 해결할 때 사용하는 태그는?
1. src (`img`, `audio`, `video` 등의 태그에서 사용되는 외부 파일 경로 지정 속성이다.)
2. 정답 : __source__
3. content (웹 컨텐츠에서 제공하는 정보의 유형을 지정한다. `meta` 태그의 속성으로 사용된다.)
4. media (`link` 태그와 함꼐 사용되며 미디어 타입을 지정한다. `media="print"`를 지정하면 인쇄용으로 지정된다.)

### 08. 클릭하면 다음 링크로 이동하는 a 태그를 작성하시오.
1. 한빛미디어 웹 사이트(http://www.hanbit.co.kr)
>```<a href="http://www.hanbit.co.kr">한빛미디어 웹 사이트</a>```
>
><a href="http://www.hanbit.co.kr">한빛미디어 웹 사이트</a>
2. 네이버 메인 페이지(http://www.naver.com)
>```<a href="http://www.naver.com">네이버 메인 페이지</a>```
>
><a href="http://www.naver.com">네이버 메인 페이지</a>
3. 구글 메인 페이지(https://www.google.com)
>```<a href="http://www.google.com">구글 메인 페이지</a>```
>
><a href="http://www.google.com">구글 메인 페이지</a>
4. 자신의 대학 웹 사이트
>```<a href="http://csi.yu.ac.kr/">영남대학교 차세대컴퓨터시스템연구실</a>```
>
><a href="http://csi.yu.ac.kr/">영남대학교 차세대컴퓨터시스템연구실</a>

### 09. 다음과 같이 폴더를 구성했을 때, 클릭하면 한빛미디어 웹 사이트로 이동하도록 이미지가 포함된 a 태그를 작성하시오.
<img src="https://github.com/Toygoon/CookbookHTML5/raw/main/Chap03/practice/09_image.png"> <img src="https://github.com/Toygoon/CookbookHTML5/raw/main/Chap03/practice/09_file.png">
>```<a href="https://www.hanbit.co.kr/"><img src="./09_image.png"></a>```
>
><a href="https://www.hanbit.co.kr/"><img src="https://github.com/Toygoon/CookbookHTML5/raw/main/Chap03/practice/09_image.png"></a>

### 10. 다음과 같은 웹 페이지를 생성하시오.
<img src="https://github.com/Toygoon/CookbookHTML5/raw/main/Chap03/practice/10_image.png">

><h1>HTML5 Basic</h1>
><h3>ITCookbook - HanbitAcademy</h3>
><hr>
><p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard
>dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen
>book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially
>unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more
>recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.</p>

    ... 중략 ...

    <h1>HTML5 Basic</h1>
    <h3>ITCookbook - HanbitAcademy</h3>
    <hr>
    <p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard
    dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen
    book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially
    unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more
    recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.</p>

    ... 중략 ...

### 11. 다음 목록을 생성하시오.
<img src="https://github.com/Toygoon/CookbookHTML5/raw/main/Chap03/practice/11_image.png">

>    <ul>
>        <li>따뜻한 음료</li>
>        <ol>
>            <li>커피</li>
>            <li>녹차</li>
>            <li>둥굴레차</li>
>        </ol>
>        <li>차가운 음료</li>
>        <ol>
>            <li>커피</li>
>            <li>스무디</li>
>           <li>식혜</li>
>        </ol>
>    </ul>

    <ul>
        <li>따뜻한 음료</li>
        <ol>
            <li>커피</li>
            <li>녹차</li>
            <li>둥굴레차</li>
        </ol>
        <li>차가운 음료</li>
        <ol>
            <li>커피</li>
            <li>스무디</li>
            <li>식혜</li>
        </ol>
    </ul>

### 12. 다음 표를 생성하시오.
<img src="https://github.com/Toygoon/CookbookHTML5/raw/main/Chap03/practice/12_image.png">

<table border="1">
    <tr>
        <th colspan="6">한국의 차</th>
    </tr>
    <tr>
        <th rowspan="6">뿌리차</th>
        <td>인삼차</td>
        <th rowspan="9">과일차</th>
        <td>수정과</td>
        <th rowspan="5">잎차</th>
        <td>뽕잎차</td>
    </tr>
    <tr>
        <td>당귀차</td>
        <td>유자차</td>
        <td>감잎차</td>
    </tr>
    <tr>
        <td>생강차</td>
        <td>구기자차</td>
        <td>솔잎차</td>
    </tr>
    <tr>
        <td>칡차</td>
        <td>대추차</td>
        <td>국화차</td>
    </tr>
    <tr>
        <td>둥굴레차</td>
        <td>오미자차</td>
        <td>이슬차</td>
    </tr>
    <tr>
        <td>마차</td>
        <td>매실차</td>
        <th rowspan="4">기타</th>
        <td>두충차</td>
    </tr>
    <tr>
        <th rowspan="3">곡물차</th>
        <td>보리차</td>
        <td>모과차</td>
        <td>영지버섯차</td>
    </tr>
    <tr>
        <td>옥수수차</td>
        <td>산수유차</td>
        <td>귤강차</td>
    </tr>
    <tr>
        <td>현미차</td>
        <td>탱자차</td>
        <td>쌍화차</td>
    </tr>
</table>

    <table border="1">
        <tr>
            <th colspan="6">한국의 차</th>
        </tr>
        <tr>
            <th rowspan="6">뿌리차</th>
            <td>인삼차</td>
            <th rowspan="9">과일차</th>
            <td>수정과</td>
            <th rowspan="5">잎차</th>
            <td>뽕잎차</td>
        </tr>
        <tr>
            <td>당귀차</td>
            <td>유자차</td>
            <td>감잎차</td>
        </tr>
        <tr>
            <td>생강차</td>
            <td>구기자차</td>
            <td>솔잎차</td>
        </tr>
        <tr>
            <td>칡차</td>
            <td>대추차</td>
            <td>국화차</td>
        </tr>
        <tr>
            <td>둥굴레차</td>
            <td>오미자차</td>
            <td>이슬차</td>
        </tr>
        <tr>
            <td>마차</td>
            <td>매실차</td>
            <th rowspan="4">기타</th>
            <td>두충차</td>
        </tr>
        <tr>
            <th rowspan="3">곡물차</th>
            <td>보리차</td>
            <td>모과차</td>
            <td>영지버섯차</td>
        </tr>
        <tr>
            <td>옥수수차</td>
            <td>산수유차</td>
            <td>귤강차</td>
        </tr>
        <tr>
            <td>현미차</td>
            <td>탱자차</td>
            <td>쌍화차</td>
        </tr>
    </table>
