# Chapter 07. 문서 객체 모델

<details>
<summary>Table of Contents</summary>

- [07-1 문서 객체 모델](#07-1-문서-객체-모델)
- [07-2 이벤트 활용](#07-2-이벤트-활용)

</details>

---

# 07-1 문서 객체 모델

- 문서 객체를 조합해서 만든 전체 형태를 `문서 객체 모델 (DOM, Document Objects Model)`이라고 부른다.

## DOMContentLoaded 이벤트

- `DOMContentLoaded` 이벤트를 사용하여 문서 객체를 조작할 수 있다.

```
document.addEventListener("DOMContentLoaded",, () => {
});
```

- 아래는 `DOMContentLoaded` 이벤트를 사용하지 않은 예시이다.

```
<head>
    <script>
        const h1 = (text) => `<h1>${text}</h1>`;
    </script>
    <script>
        document.body.innerHTML += h1('first script');
    </script>
</head>

<body>
    <script>
        document.body.innerHTML += h1('second script');
    </script>
    <h1>first</h1>
    <script>
        document.body.innerHTML += h1('third script');
    </script>
    <h1>second</h1>
</body>
```

- 위의 코드를 실행하면, 다음과 같은 결과가 나타난다.

```
second script
first
third script
second
```

- 그 이유는 `<head>`에서 `<body>` 태그가 생성되기 이전에 `document.body.innerHTML`을 사용하여 객체를 조작했기 때문에, `<body>` 영역이 아직 생성되지 않아 반영되지 않은 것이다.
- `const h1`은 `<head>`에서 생성되었기 때문에, `<script>`를 통해서 참조할 수 있다. `<body>`에서 생성한 `h1` 스크립트는 모두 동작하여 순서대로 출력된다.
- `DOMContentLoaded` 이벤트는 웹 문서가 문서 객체를 모두 읽고 나서 실행하는 이벤트이기 때문에, 다음과 같이 사용하면 `DOMContentLoaded` 상태가 되었을 때 콜백 함수를 호출한다.

```
<head>
    <script>
        document.addEventListener("DOMContentLoaded", () => {
            const h1 = (text) => `<h1>${text}</h1>`;
            document.body.innerHTML = h1('DOMContentLoaded event');
        });
    </script>
</head>
```

- `DOMContentLoaded`는 `HTML5`부터 추가된 이벤트이며, 구버전은 `document.onload`를 사용한다.

## 문서 객체 가져오기

- `document.body` 코드를 사용하면 문서의 `body` 요소를 읽어들일 수 있다.
- 이외에도 `HTML` 문서에 있는 `head` 요소와 `title` 요소 등은 다음과 같은 방법으로 읽어들일 수 있다.
- `document.querySelector(query)`, 혹은 `document.querySelectorAll(query)`를 통해 `body` 요소의 다른 요소에 접근할 수 있다.

```
<header>
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const header = document.querySelector('h1');

            header.textContent = 'HEADERS';
            header.style.color = 'white';
            header.style.backgroundColor = 'black';
            header.style.padding = '10px';
        });
    </script>
</head>

<body>
    <h1></h1>
</body>
```

## 요소 조작하기

### 글자 조작하기

- `element.textContent`는 문자열을 그대로 넣어주고, `element.innerHTML`은 입력된 문자열을 `HTML` 형식으로 추가한다.

```
<head>
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const a = document.querySelector('#a'),
                b = document.querySelector('#b');

            a.textContent = '<h1>textContent</h1>';
            b.innerHTML = '<h1>innerHTML</h1>';
        })
    </script>
</head>

<body>
    <div id="a"></div>
    <div id="b"></div>
</body>
```

### 속성 조작하기

- 문서 객체의 속성을 조작할 때는 다음과 같은 메소드를 사용한다.
- `element.setAttribute(attr, value)`, `element.getAttribute(attr)`
- 아래는 그 예시이다.

```
<head>
    <script>
        document.addEventListener("DOMContentLoaded", () => {
            const rects = document.querySelectorAll(".rect");

            rects.forEach((rect, index) => {
                const width = (index + 1) * 100,
                    src = `https://placekitten.com/${width}/250`;

                rect.setAttribute('src', src);
            });
        });
    </script>
</head>

<body>
    <img class="rect">
    <img class="rect">
    <img class="rect">
    <img class="rect">
</body>
```

- 혹은, 그냥 `rect.src`를 사용할 수도 있다.

### 스타일 조작하기

- 문서 객체의 스타일을 조작할 때는 `style` 속성을 사용한다.
- `style` 속성은 객체이며, 내부에는 속성으로 `CSS`를 사용해서 지정할 수 있는 스타일이 있다.
- 이러한 속성은 `CSS`로 입력할 때 사용하는 값과 같은 값을 입력한다.

```
<head>
    <script>
        document.addEventListener("DOMContentLoaded", () => {
            const divs = document.querySelectorAll('body > div');

            divs.forEach((div, index) => {
                console.log(div, index);

                const val = index * 10;
                div.style.height = '10px';
                div.style.backgroundColor = `rgba(${val}, ${val}, ${val})`;
            });
        });
    </script>
</head>

<body>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
</body>
```

## 문서 객체 생성하기

- 문서 객체를 생성하고 싶을 때에는 `document.createElement()` 메소드를 사용한다.

```
<head>
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const header = document.createElement('h1');

            header.textContent = 'Document';
            header.setAttribute('data-custom', 'data');
            header.style.color = 'white';
            header.style.backgroundColor = 'black';

            document.body.appendChild(header);
        });
    </script>
</head>

<body>

</body>
```

## 문서 객체 이동하기

- `appendChild()` 메소드는 문서 객체를 이동할 때도 사용할 수 있다.
- 다음은 `setTimeOut()` 메소드를 사용하여 `h1` 요소가 1초마다 `div`을 전환하도록 하는 코드이다.

```
<head>
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const divA = document.querySelector('#first'),
                divB = document.querySelector('#second'),
                h1 = document.createElement('h1');

            h1.textContent = 'h1';

            const toFirst = () => {
                divA.appendChild(h1);
                setTimeout(toSecond, 1000);
            };

            const toSecond = () => {
                divB.appendChild(h1);
                setTimeout(toFirst, 1000);
            }

            toFirst();
        });
    </script>
</head>

<body>
    <div id="first">
        <h1>first div</h1>
    </div>

    <div id="second">
        <h1>second div</h1>
    </div>
</body>
```

## 문서 객체 제거하기

- 문서 객체를 제거할 때는 `removeChild()` 메소드를 사용한다.
- `appendChild()` 메소드 등으로 부모 객체와 이미 연결이 완료된 문서 객체의 경우는 `parentNode` 속성으로 부모 객체에 접근할 수 있다.

```
element.parentNode.removeChild(h1);
```

- 일반적으로 위와 같이 사용한다.
- 또한, `h1`은 `document.body` 요소의 자식이므로 아래와 같이 사용할 수도 있다.

```
document.body.removeChild(h1);
```

## 이벤트 설정하기

- 모든 문서 객체는 생성되거나, 클릭되거나, 마우스를 위에 올리거나 할 때 `event`가 발생한다.
- 그리고, 이 이벤트가 발생할 때 실행할 함수는 `addEventListener()` 메소드를 사용한다.

```
document.addEventListener(eventName, callbackFunc);
```

- 이벤트가 발생할 때 실행할 함수를 `Event Listener`, 혹은 `Event Handler`라고 부른다.
- 아래는 `h1` 태그를 클릭할 때 `Event Listener`를 호출하는 예시이다.

```
<head>
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            let counter = 0;
            const h1 = document.querySelector('h1');

            h1.addEventListener('click', (event) => {
                counter++;
                h1.textContent = `clicked : ${counter}`;
            });
        });
    </script>
</head>

<body>
    <h1>clicked : 0</h1>
</body>
```

- 이벤트를 제거할 때는 `removeEventListener()` 메소드를 사용한다.
- 아래는 해당 예시이다.

```
<head>
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            let counter = 0, isConnect = false;

            const h1 = document.querySelector('h1'),
                p = document.querySelector('p'),
                connectButton = document.querySelector('#connect'),
                disconnectButton = document.querySelector('#disconnect'),
                listener = (event) => {
                    h1.textContent = `clicked : ${counter++}`;
                };

            connectButton.addEventListener('click', () => {
                if (!isConnect) {
                    h1.addEventListener('click', listener);
                    p.textContent = 'event connected';
                    isConnect = true;
                }
            });

            disconnectButton.addEventListener('click', () => {
                if (isConnect) {
                    h1.removeEventListener('click', listener);
                    p.textContent = 'event disconnected';
                    isConnect = false;
                }
            });
        })
    </script>

    <style>
        h1 {
            user-select: none;
        }
    </style>
</head>

<body>
    <h1>clicked : 0</h1>
    <button id="connect">connect</button>
    <button id="disconnect">disconnect</button>
    <p>event disconncted</p>
</body>

```

## 6가지 키워드로 정리하는 핵심 포인트

- `DOMContentLoaded` 이벤트는 HTML 페이지의 모든 문서 객체(요소)를 웹 브라우저가 읽어들였을 때 발생시키는 이벤트입니다.
- `querySelector()` 메소드 문서 객체를 선택할 때 사용하는 메소드입니다.
- `textContent` 속성 `innerHTML` 속성은 문서 객체 내부의 글자를 조작할 때 사용하는 속성입니다.
- `style` 속성은 문서 객체의 스타일을 조작할 때 사용하는 속성입니다.
- `Event Listener (Event Handler)`는 이벤트가 발생할 때 실행하는 함수를 의미합니다.

## 확인 문제

### 1. 다음 중에서 웹 브라우저가 문서 객체를 모두 읽어들였을 때 실행되는 이벤트를 골라주세요.

1. `DomContentLoaded`
2. 정답 : `DOMContentLoaded`
3. `ContentLoaded`
4. `Loaded`

### 2. 다음과 같은 요소를 `querySelector()` 메소드로 선택할 때 사용할 수 있는 선택자를 2개 이상 적어주세요.

1. `<h1 id="header">제목<h1>`

- 정답 : `#header`, `h1`

2. `<span class="active">선택</span>`

- 정답 : `.active`, `span`

3. `<input id="name-input" type="text" name="name">`

- 정답 : `#name-input`, `#name-input[type="text"]`, `input[name="name"]`, `input`

### 3. 다음 중에서 문서 객체 내부의 글자를 조작하는 속성이 아닌 것을 골라주세요.

1. 정답 : `innerText`
2. `textContent`
3. `innerHTML`
4. 정답 : `htmlContent`

### 4. 다음 CSS에서 사용하는 스타일 속성들을 자바스크립트 문서 객체에서 점을 찍고 곧바로 사용할 수 있는 형태의 식별자로 변경해주세요.

```
예: background-color -> backgroundColor
```

1. `border-radius` -> `borderRadius`
2. `font-family` -> `fontFamily`
3. `line-height` -> `lineHeight`
4. `width` -> `width`
5. `box-sizing` -> `boxSizing`

---

# 07-2 이벤트 활용

## 이벤트 모델

- 이벤트를 연결하는 방법을 `Event Model`이라고 부른다.
- `addEventListener()` 모세도는 현재 표준으로 사용하고 있는 방법이므로, `표준 이벤트 모델`이라고 부른다.
- 과거에는 `onXXX`와 같이 `on`으로 시작하는 속성에 함수를 할당해서 이벤트를 연결했는데, 이를 `고전 이벤트 모델`이라고 부른다.
- `고전 이벤트 모델`을 `HTML` 요소에 직접 넣어서 이벤트를 연결하는 것을 `인라인 이벤트 모델`이라고 부른다.
- 모든 이벤트 모델의 이벤트 리스너는 첫 번째 매개변수로 `Event Object`를 받는다.

## 키보드 이벤트

- `키보드 이벤트`는 다음과 같은 3가지 이벤트가 있다.
- `keydown` : 키가 눌릴 때 실행되며, 연속 입력 또한 처리된다.
- `keypress` : 키가 입력됐을 때 실행된다. 하지만, 브라우저에 따라 아시아권의 문자를 제대로 처리하지 못하는 경우가 있다.
- `keyup` : 키보드에서 키가 떨어질 때 실행된다.
- `keydown` 이벤트와 `keypress` 이벤트는 브라우저에 따라 실행 결과가 다를 수 있어서, 일반적으로는 `keyup` 이벤트를 사용한다.
- 아래는 글자 수를 세는 예시이다.

```
<head>
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const textarea = document.querySelector('textarea'),
                h1 = document.querySelector('h1');

            textarea.addEventListener('keyup', (event) => {
                const length = textarea.value.length;
                h1.textContent = `words count : ${length}`;
            })
        });
    </script>
</head>

<body>
    <h1>words count : 0</h1>
    <textarea></textarea>
</body>
```

## 키보드 키 코드 사용하기

- 키보드 이벤트가 발생할 때는 이벤트 객체로 어떤 키를 눌렀는지와 관련된 속성들이 따라온다.
- 다음과 같은 속성 등을 사용할 수 있다.

| 이벤트 속성 이름 | 설명                      |
| ---------------- | ------------------------- |
| code             | 입력한 키                 |
| keyCode          | 입력한 키를 나타내는 숫자 |
| altKey           | `Alt` 키를 눌렀는지       |
| ctrlKey          | `Ctrl` 키를 눌렀는지      |
| shiftKey         | `Shift` 키를 눌렀는지     |

- 다음 코드는 `Alt`, `Ctrl`, `Shift` 키와 `C` 키를 누르면 텍스트를 출력하는 코드 예시이다.

```
<head>
    <script>
        document.addEventListener('DOMContnetLoaded', () => {
            const h1 = document.querySelector('h1'),
                print = (event) => {
                    let output = '';

                    output += `alt: ${event.altKey}<br>`;
                    output += `ctrl: ${event.ctrlKey}<br>`;
                    output += `shift: ${event.shiftKey}<br>`;
                    output += `code: ${typeof (event.code) !== 'undefined'
                        ? event.code : event.keyCode}`;

                    h1.innerHTML = output;

                    document.addEventListener('keydown', print);
                    document.addEventListener('keyup', print);
                }
        });
    </script>
</head>

<body>
    <h1></h1>
</body>

```

- 다음 코드는 `keyCode`를 활용한 예시이다.

```
<head>
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const star = document.querySelector('h1');
            star.style.position = 'absolute';

            let [x, y] = [0, 0];
            const block = 20,
                print = () => {
                    star.style.left = `${x * block}px`;
                    star.style.top = `${y * block}px`;
                };

            print();

            const [left, up, right, down] = [37, 38, 39, 40];
            document.body.addEventListener('keydown', (event) => {
                switch (event.keyCode) {
                    case left:
                        x -= 1;
                        break;
                    case up:
                        y -= 1;
                        break;
                    case right:
                        x += 1;
                        break;
                    case down:
                        y += 1;
                        break;
                }
                print();
            });
        });
    </script>
</head>
<body>
    <h1>*</h1>
</body>
```

## 이벤트 발생 객체

- 이벤트 리스너 내부에서 변수에 접근할 수 없는 경우가 있는데, 두 가지 방법으로 문제를 해결할 수 있다.

1. `event.currentTarget` 속성을 사용한다.

- 이는 `() => {}`와 `function () {}` 형태 모두 사용 가능하다.

2. `this` 키워드를 사용한다.

- 화살표 함수가 아닌 `function () {}` 형태에서 사용한다.

## 3가지 키워드로 정리하는 핵심 포인트

- `이벤트 모델`은 이벤트를 연결하는 방법을 의미합니다.
- `이벤트 객체`는 이벤트 리스너의 첫 번째 매개변수로 이벤트와 관련된 정보가 들어가있습니다.
- `이벤트 발생 객체`는 이벤트를 발생시킨 객체를 의미합니다. 이벤트 객체의 `currentTarget` 속성을 사용해서 확인할 수 있습니다.

## 확인 문제

### 1. 다음 이벤트 모델의 이름과 코드를 연결해주세요. 식별자 `listener`는 이벤트 리스너입니다.

- 표준 이벤트 모델 : `document.body.addEventListener('load', listener);`
- 인라인 이벤트 모델 : `<body onload="listener()"></body>`
- 고전 이벤트 모델 : `document.body.onload = listener;`

### 2. 다음 중에서 체크 박스와 라디오 버튼 등 입력 양식의 체크 상태를 확인할 때 사용하는 속성을 골라주세요.

1. `selected`
2. `isChecked`
3. 정답 : `checked`
4. `isSelected`

### 3. 다음 이벤트 이름과 이벤트가 발생하는 상황을 연결해주세요.

- `contextmenu` : 마우스 오른쪽 클릭 등으로 컨텍스트 메뉴를 출력할 때
- `change` : 입력 양식의 값이 변경될 때
- `keyup` : 키보드 키가 떨어질 때
- `blur` : 입력 양식의 초점이 해제될 때

### 4. 다음 중 기본 이벤트를 막는 메소드 이름을 골라주세요.

1. 정답 : `preventDefault()`
2. `prevent()`
3. `removeDefault()`
4. `default(false)`

### 5. 다음 중 이벤트 리스너 내부에서 이벤트 발생 객체를 찾는 코드로 알맞은 것을 모두 골라주세요. (이벤트 객체를 event라고 가정합니다.)

1. `event.current`
2. 정답 : `event.currentTarget`
3. 정답 : `this`
4. `this.currentTarget`
