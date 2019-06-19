# 페이지 추가

페이지를 추가하고 싶다면, docsify 디렉터리 아래에 마크다운 파일만 생성하면 됩니다. 파일 이름을 `guide.md` 로 생성한다면, `/#/guide` 로 접근할 수 있습니다.

만약 디렉터리 구조가 다음과 같다면:

```text
.
└── docs
    ├── README.md
    ├── guide.md
    └── zh-cn
        ├── README.md
        └── guide.md
```

다음과같이 연결됩니다

```text
docs/README.md        => http://domain.com
docs/guide.md         => http://domain.com/guide
docs/zh-cn/README.md  => http://domain.com/zh-cn/
docs/zh-cn/guide.md   => http://domain.com/zh-cn/guide
```

## 사이드바

사이드바를 만들기위해서는 `_sidebar.md` 를 만들어야합니다. ([사이드바 문서](https://github.com/docsifyjs/docsify/blob/master/docs/_sidebar.md)를 확인하세요):

우선, `loadSidebar`를 **true**로 설정합니다. 자세한사항은  [configuration paragraph](configuration.md#loadsidebar) 를 확인하세요.

```html
<!-- index.html -->

<script>
  window.$docsify = {
    loadSidebar: true
  }
</script>
<script src="//unpkg.com/docsify/lib/docsify.min.js"></script>
```

 `_sidebar.md` 를 만드세요:

```markdown
<!-- docs/_sidebar.md -->

* [Home](/)
* [Guide](guide.md)
```

GitHub Pages가 밑줄로 시작하는 파일을 무시하지 않도록 `.nojekyll` 을 `./docs` 안에 생성하세요.

## Nested 사이드바

사이드바를 현재 디렉터리가 어디에 위치해있는지 보여주는 역할을 하길 원할지도 모릅니다.  각각의 파일에`_sidebar.md`.를 넣어주면 됩니다.

`_sidebar.md` 는 디렉토리레벨에서 각각 로드됩니다 . 현재 디렉터리가 `_sidebar.md` 를 가지고 있지 않다면, 부모 디렉터리에 속하게 됩니다. 예를들어, 현재 디렉터리가 `/guide/quick-start` 라면,  `_sidebar.md` 는  `/guide/_sidebar.md` 로 로드될 것입니다.

 `alias` 를 구체적으로 작성하여 이러한 동작을 막을 수 있습니다.

```html
<script>
  window.$docsify = {
    loadSidebar: true,
    alias: {
      '/.*/_sidebar.md': '/_sidebar.md'
    }
  }
</script>
```

!> `README.md` 를 하위 디렉터리에 작성하면 해당 라우트의 랜딩페이지로써 동작하게 됩니다

## 사이드바에서 제목 설정하기

페이지의 `title` 태그는 선택한 사이드바 아이템의 이름으로 생성됩니다. 더 나은 SEO를 위해, 파일이름 다음에 문자열을 작성하여 커스터마이징할 수 있습니다.

```markdown
<!-- docs/_sidebar.md -->
* [Home](/)
* [Guide](guide.md "The greatest guide in the world")
```

## 목차

일단 `_sidebar.md` 를 만들면, 마크다운파일의 헤더를 기반으로 사이드바 내용이 자동으로 생성됩니다.

 `subMaxLevel` 을 설정하면 목차를 자동으로 생성할 수 있습니다.  [subMaxLevel configuration](configuration.md#submaxlevel) 를 확인해보세요.

```html
<!-- index.html -->

<script>
  window.$docsify = {
    loadSidebar: true,
    subMaxLevel: 2
  }
</script>
<script src="//unpkg.com/docsify/lib/docsify.min.js"></script>
```

## 서브헤더 생략하기

 `subMaxLevel`가 설정되면, 기본적으로 각각의 헤더는 자동으로 목차에 생성됩니다. 만약 특정 헤더를 생략하길 원한다면,  `{docsify-ignore}` 를 뒤에 붙이면 됩니다.

```markdown
# Getting Started

## Header {docsify-ignore}

이 헤더는 사이드바 목차에 나타나지 않을 것입니다.
```

특정 페이지의 모든 목차를 생략하고 싶다면,  `{docsify-ignore-all}` 를 페이지의 첫번째 헤더에 추가하세요.

```markdown
# Getting Started {docsify-ignore-all}

## Header

이 헤더는 사이드바 목차에 나타나지 않을 것입니다.
```

 `{docsify-ignore}` 와 `{docsify-ignore-all}` 는 페이지에 렌더링되지 않습니다.
