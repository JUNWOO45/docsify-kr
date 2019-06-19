# Doc helper

docsify는 문서를 더 읽기 쉽게 만들기 위해 마크다운 구문을 확장합니다.

## important content

important content는 다음과같이 작성합니다:

```markdown
!> **Time** is money, my friend!
```

위 코드는 다음과같이 보여집니다:

!> **Time** is money, my friend!

## General tips

General tips는 다음과같이 작성합니다::

```markdown
?> _TODO_ unit test
```

위 코드는 다음과같이 보여집니다:

?> _TODO_ unit test

## 링크 컴파일 막기

가끔씩 상대경로를 링크에 넣을텐데, docsify에게 링크를 컴파일하지 말라고 알려줘야만한다. 예를들어,

```md
[link](/demo/)
```

위 코드는 `<a href="/#/demo/">link</a>` 로 컴파일될 것이고 `/demo/README.md` 를 불러올 것입니다. 

만약 `/demo/index.html` 로 이동하고 싶다면 다음과 같이 작성하면 됩니다.

```md
[link](/demo/ ':ignore')
```

 `<a href="/demo/">link</a>` html을 결과로 얻을 것입니다. 링크의 제목도 정할 수 있습니다.

```md
[link](/demo/ ':ignore title')

<a href="/demo/" title="title">link</a>
```

## 링크 속성 지정하기

```md
[link](/demo ':target=_blank')
[link](/demo2 ':target=_self')
```

## 링크 사용막기

```md
[link](/demo ':disabled')
```

## Github 할 일 리스트

```md
- [ ] foo
- bar
- [x] baz
- [] bam <~ 동작하지 않습니다
  - [ ] bim
  - [ ] lim
```

- [ ] foo
- bar
- [x] baz
- [] bam <~ 동작하지 않습니다
  - [ ] bim
  - [ ] lim

## 이미지 크기조정

```md
![logo](https://docsify.js.org/_media/icon.svg ':size=50x100')
![logo](https://docsify.js.org/_media/icon.svg ':size=100')

<!-- Support percentage -->

![logo](https://docsify.js.org/_media/icon.svg ':size=10%')
```

![logo](https://docsify.js.org/_media/icon.svg ':size=50x100')
![logo](https://docsify.js.org/_media/icon.svg ':size=100')
![logo](https://docsify.js.org/_media/icon.svg ':size=10%')

## headings에 ID값 지정하기

```md
### 你好，世界！ :id=hello-world
```

## html 태그 안의 Markdown

html과 Markdown 내용 사이에 공백을 넣어야 마크다운 컨텐츠의 렌더링이 가능해집니다.

```markdown
<details>
<summary>Self-assessment (Click to expand)</summary>

- Abc
- Abc

</details>
```

<details>
<summary>Self-assessment (Click to expand)</summary>

- Abc
- Abc

</details>

마크다운 컨텐츠를 html태그로 감쌀 수 있습니다.

```markdown
<div style='color: red'>

- listitem
- listitem
- listitem

</div>
```

<div style='color: red'>

- Abc
- Abc

</div>
