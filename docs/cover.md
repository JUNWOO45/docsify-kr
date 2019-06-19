# Cover

 `coverpage` 를 **true** 로 설정하여 활성화시킬 수 있습니다. 자세한 사항은 [coverpage configuration](configuration.md#coverpage) 를 참조하세요.

## 기본 사용법

 `coverpage` 를 **true**로 설정하고, `_coverpage.md` 를 만드세요:

```html
<!-- index.html -->

<script>
  window.$docsify = {
    coverpage: true
  }
</script>
<script src="//unpkg.com/docsify/lib/docsify.min.js"></script>
```

```markdown
<!-- _coverpage.md -->

![logo](_media/icon.svg)

# docsify <small>3.5</small>

> A magical documentation site generator.

- Simple and lightweight (~21kB gzipped)
- No statically built html files
- Multiple themes

[GitHub](https://github.com/docsifyjs/docsify/)
[Get Started](#docsify)
```

!> 사이트는 오직 하나의 커버페이지만 가질 수 있습니다!

## Custom background

기본적으로 배경 색깔은 랜덤으로 생성되지만, 배경 색깔이나 배경 이미지를 커스터마이징 할 수 있습니다:

```markdown
<!-- _coverpage.md -->

# docsify <small>3.5</small>

[GitHub](https://github.com/docsifyjs/docsify/)
[Get Started](#quick-start)

<!-- background image -->

![](_media/bg.png)

<!-- background color -->

![color](#f0f0f0)
```

## Coverpage as homepage

일반적으로, 커버페이지와 홈페이지는 동시에 보여지게됩니다.  [onlyCover option](configuration.md#onlycover) 을 설정하여 분리 시킬 수 있습니다.

## Multiple covers

만약 당신의 사이트가 한개 이상의 언어로 이루어져 있다면, 커버를 나누는 것이 더 유용할 것입니다.

만약 문서 구조가 다음과 같다면,

```text
.
└── docs
    ├── README.md
    ├── guide.md
    ├── _coverpage.md
    └── zh-cn
        ├── README.md
        └── guide.md
        └── _coverpage.md
```

다음과 같이 설정할 수 있습니다.

```js
window.$docsify = {
  coverpage: ['/', '/zh-cn/']
};
```

또는 파일 이름으로 설정할 수 도 있습니다.

```js
window.$docsify = {
  coverpage: {
    '/': 'cover.md',
    '/zh-cn/': 'cover.md'
  }
};
```
