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