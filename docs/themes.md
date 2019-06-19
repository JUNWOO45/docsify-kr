# Themes

현재 3개의 테마를 사용할 수 있습니다.  [Vue](//vuejs.org) 와 [buble](//buble.surge.sh)사이트를 따라한 커스텀 주제와 [@liril-net](https://github.com/liril-net) 의 컨트리뷰션으로 사용할 수 있는 블랙 테마가 있습니다.

```html
<link rel="stylesheet" href="//unpkg.com/docsify/themes/vue.css">
<link rel="stylesheet" href="//unpkg.com/docsify/themes/buble.css">
<link rel="stylesheet" href="//unpkg.com/docsify/themes/dark.css">
<link rel="stylesheet" href="//unpkg.com/docsify/themes/pure.css">
```

!> 압축된 파일은 `/lib/themes/` 로 제공됩니다.

```html
<!-- compressed -->

<link rel="stylesheet" href="//unpkg.com/docsify/lib/themes/vue.css">
<link rel="stylesheet" href="//unpkg.com/docsify/lib/themes/buble.css">
<link rel="stylesheet" href="//unpkg.com/docsify/lib/themes/dark.css">
<link rel="stylesheet" href="//unpkg.com/docsify/lib/themes/pure.css">
```

좋은 아이디어를 가지고 있거나 좋은 테마를 개발했다면, [pull request](https://github.com/docsifyjs/docsify/pulls) 를 해주세요.

#### 미리보기

<div class="demo-theme-preview">
  <a data-theme="vue">vue.css</a>
  <a data-theme="buble">buble.css</a>
  <a data-theme="dark">dark.css</a>
  <a data-theme="pure">pure.css</a>
</div>

<style>
  .demo-theme-preview a {
    padding-right: 10px;
  }
  .demo-theme-preview a:hover {
    cursor: pointer;
    text-decoration: underline;
  }
</style>

<script>
  var preview = Docsify.dom.find('.demo-theme-preview');
  var themes = Docsify.dom.findAll('[rel="stylesheet"]');

  preview.onclick = function (e) {
    var title = e.target.getAttribute('data-theme')

    themes.forEach(function (theme) {
      theme.disabled = theme.title !== title
    });
  };
</script>

## 다른 테마

- [docsify-themeable](https://jhildenbiddle.github.io/docsify-themeable/#/) docsify를 위한 아주 간단한 테마입니다.
