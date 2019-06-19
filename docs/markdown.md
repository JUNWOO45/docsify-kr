# Markdown configuration

**docsify** 는 마크다운 해석기인 [marked](https://github.com/markedjs/marked) 를 사용합니다. `renderer` 를 커스터마이징하여 HTML로 마크다운 컨텐츠를 렌더링하는 방법을 커스터마이징할 수 있습니다:

```js
window.$docsify = {
  markdown: {
    smartypants: true,
    renderer: {
      link: function() {
        // ...
      }
    }
  }
}
```

?>  [marked documentation](https://marked.js.org/#/USING_ADVANCED.md) 을 확인해보세요.

심지어 해석하는 룰까지 커스터마이징할 수 있습니다.

```js
window.$docsify = {
  markdown: function(marked, renderer) {
    // ...

    return marked
  }
}
```

## Supports mermaid

```js
// Import mermaid
//  <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/mermaid/dist/mermaid.min.css">
//  <script src="//cdn.jsdelivr.net/npm/mermaid/dist/mermaid.min.js"></script>

var num = 0;
mermaid.initialize({ startOnLoad: false });

window.$docsify = {
  markdown: {
    renderer: {
      code: function(code, lang) {
        if (lang === "mermaid") {
          return (
            '<div class="mermaid">' + mermaid.render('mermaid-svg-' + num++, code) + "</div>"
          );
        }
        return this.origin.code.apply(this, arguments);
      }
    }
  }
}
```
