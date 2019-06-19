# 커스텀 네비게이션바

## HTML

커스텀 네비게이션바를 만드려면, HTML기반으로 만들어야핣니다.

!> 문서는 `#/` 로 시작합니다.

```html
<!-- index.html -->

<body>
  <nav>
    <a href="#/">EN</a>
    <a href="#/zh-cn/">中文</a>
  </nav>
  <div id="app"></div>
</body>
```

## 마크다운

또는, `loadNavbar`을**true**로 설정하고 `_navbar.md` 파일을 생성하여 마크다운 기반의 네비게이션 파일을 만들 수 있습니다. 자세한건 [loadNavbar configuration](configuration.md#loadnavbar) 을 참고하세요.

```html
<!-- index.html -->

<script>
  window.$docsify = {
    loadNavbar: true
  }
</script>
<script src="//unpkg.com/docsify/lib/docsify.min.js"></script>
```

```markdown
<!-- _navbar.md -->

* [En](/)
* [chinese](/zh-cn/)
```

!> GitHub Pages가 밑줄로 시작하는 파일을 무시하지 않도록 `.nojekyll` 을 `./docs` 안에 생성하세요.

`_navbar.md` 는 디렉터리 레벨에서 각각 로드됩니다. 만약 현재 디렉터리가 `_navbar.md` 를 가지고 있지 않다면, 상위 디렉터리의 navbar를 받습니다. 예를들어, 현재 위치가 `/guide/quick-start`, 라면, `_navbar.md` 는 `/guide/_navbar.md` 에서 로드됩니다.

## Nesting

특정 부모 밑의 아이템들을 들여써서 하위리스트로 만들 수 있습니다.

```markdown
<!-- _navbar.md -->

* Getting started

  * [Quick start](quickstart.md)
  * [Writing more pages](more-pages.md)
  * [Custom navbar](custom-navbar.md)
  * [Cover page](cover.md)

* Configuration
  * [Configuration](configuration.md)
  * [Themes](themes.md)
  * [Using plugins](plugins.md)
  * [Markdown configuration](markdown.md)
  * [Language highlight](language-highlight.md)
```

는 다음과같이 렌더링됩니다.

![Nesting navbar](_images/nested-navbar.png 'Nesting navbar')

## emoji 플러그인을 사용하여 네비게이션바 커스텀하기

 [emoji plugin](plugins#emoji) 를 사용한다면:

```html
<!-- index.html -->

<script>
  window.$docsify = {
    // ...
  }
</script>
<script src="//unpkg.com/docsify/lib/docsify.min.js"></script>
<script src="//unpkg.com/docsify/lib/plugins/emoji.min.js"></script>
```

커스텀 네비게이션 마크다운 파일안에서 이모지를 사용할 수 있습니다:

```markdown
<!-- _navbar.md -->

* [:us:, :uk:](/)
* [:cn:](/zh-cn/)
```
