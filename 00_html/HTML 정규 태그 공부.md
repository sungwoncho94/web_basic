# HTML 정규 태그 공부

> 20.06.22 (월)

## <a>  

- 상대 URL로 연결 가능
- `href="#id"` -> 해당 id단락으로 이동 가능
- 이메일, 전화번호 연결 가능 (디바이스에 따라 결과가 다르다)
- download 속성 -> 해당 이름/확장자로 다운로드 가능
- target 속성 -> 문서가 열리는 방식 선택 가능

## <abbr>

- title 속성과 함께 사용 (full name 설명)
- 밑줄이 표시되고, title의 내용이 툴팁으로 표현
- 준말임을 표시할 때 title 속성 없이 사용
- <dfn>과 함께 사용하여 완전한 <abbr> 사용 가능

```html
<p>Ashok's joke made me <abbr title="Laugh Out Loud">LOL</abbr> big
time.</p>
```

## <address>

- 사람, 단체, 조직 등에 대한 연락처 정보를 나타냄 (list와 비슷한 모양으로 나옴)
- <i> 나 <em>요소와 비슷하지만, 주소, 연락처 등을 나타낼 때는 <adress>를 사용

## <area>

- map 요소 안에서 사용
- coords 속성 : 하이퍼링크를 연결할 특정 영역의 좌표를 나타냄

![image-20200622153113786](C:\Users\조성원\Desktop\web_basic\00_html\images\area_coords.png)

```html
<map name="infographic">
    <area shape="rect" coords="184,6,253,27"
          href="https://mozilla.org"
          target="_blank" alt="Mozilla" />
    <area shape="circle" coords="130,136,60"
          href="https://developer.mozilla.org/"
          target="_blank" alt="MDN" />
    <area shape="poly" coords="207,241,54,241,72,217,189,217"
          href="https://developer.mozilla.org/docs/Web/JavaScript"
          target="_blank" alt="JavaScript" />
</map>
<img usemap="#infographic" src="/media/examples/mdn-info.png" alt="MDN infographic" />
```

## <article>

- 포럼의 글 하나, 잡지나 신문의 기사 하나, 블로그의 글 하나, 댓글 하나 등 사이트 내 독립적인 내용
- 블로그의 글 내 댓글 처럼 <article>을 겹쳐서 사용할 수 있다.







## <b>

- 굵은 글씨로 표현해줌. but, <b>를 이용하여 텍스트 꾸미기X -> **css**의 **font-weight** 속성  or  <strong> 사용
- <strong> : <strong>중요한 글</strong>
- <em> : <em>약간 강조가 필요한 글</em>
- <mark> : <mark>관련성이 있는 글</mark>
- <b> : <b>아무 의미 없음</b> -> 다른 요소가 적합하지 않을 때 사용

## <bdo>

- dir 속성으로 텍스트가 쓰여지는 방향 결정

```html
<p>이 글은 왼쪽에서 오른쪽으로 작성합니다.</p>
<p><bdo dir="rtl">이 글은 오른쪽에서 왼쪽으로 작성합니다.</bdo></p>
<p><bdo dir="ltr">이 글은 왼쪽에서 오른쪽으로 작성합니다.</bdo></p>

<!-- 결과
이 글은 왼쪽에서 오른쪽으로 작성합니다.
이 글은 오른쪽에서 왼쪽으로 작성합니다.
이 글은 왼쪽에서 오른쪽으로 작성합니다.
-->
```

## <b>

- 줄바꿈할 때 사용
- <mark>주의점</mark>
  - 문단 사이의 여백을 줄 때 사용X -> <p>태그로 감싼 후, margin 속성 사용
  - 줄 간격 조정하고 싶을 때, br태그 여러개 사용 X -> line-height 속성 사용