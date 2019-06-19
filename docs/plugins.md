# List of Plugins

## 전체 문자 검색

기본적으로, 현재페이지의 하이퍼링크는 인식되며 내용은 `localStorage` 에 저장됩니다. 파일의 경로를 지정할 수도 있습니다.

```html
<script>
  window.$docsify = {
    search: 'auto', // default

    search : [
      '/',            // => /README.md
      '/guide',       // => /guide.md
      '/get-started', // => /get-started.md
      '/zh-cn/',      // => /zh-cn/README.md
    ],

    // complete configuration parameters
    search: {
      maxAge: 86400000, // Expiration time, the default one day
      paths: [], // or 'auto'
      placeholder: 'Type to search',

      // Localization
      placeholder: {
        '/zh-cn/': '搜索',
        '/': 'Type to search'
      },

      noData: 'No Results!',

      // Localization
      noData: {
        '/zh-cn/': '找不到结果',
        '/': 'No Results'
      },

      // Headline depth, 1 - 6
      depth: 2,

      hideOtherSidebarContent: false, // whether or not to hide other sidebar content

      // To avoid search index collision
      // between multiple websites under the same domain
      namespace: 'website-1',
    }
  }
</script>
<script src="//unpkg.com/docsify/lib/docsify.min.js"></script>
<script src="//unpkg.com/docsify/lib/plugins/search.min.js"></script>
```

## Google Analytics

플러그인을 설치하고 track id를 설정하세요.

```html
<script>
  window.$docsify = {
    ga: 'UA-XXXXX-Y'
  }
</script>
<script src="//unpkg.com/docsify/lib/docsify.min.js"></script>
<script src="//unpkg.com/docsify/lib/plugins/ga.min.js"></script>
```

 `data-ga` 로 설정합니다.

```html
<script src="//unpkg.com/docsify/lib/docsify.min.js" data-ga="UA-XXXXX-Y"></script>
<script src="//unpkg.com/docsify/lib/plugins/ga.min.js"></script>
```

## emoji

기본적으로 이모지의 해석을 지원합니다. 예를 들어 `:100:` 는 :100: 로 해석됩니다. 그러나 일치하는 이모지가 없을 수 있기에 정확하지 않습니다. 정확한 이모지 해석을 원한다면, 이 플러그인을 설치해야 합니다.

```html
<script src="//unpkg.com/docsify/lib/plugins/emoji.min.js"></script>
```

## External Script

페이지의 스크립트가 외부 스크립트인 경우(src 속성을 통해 js 파일을 가져오기) 이 플러그인이 있어야 제대로 작동할 수 있다.

```html
<script src="//unpkg.com/docsify/lib/plugins/external-script.min.js"></script>
```

## Zoom image

Medium의 이미지 zoom.medium-zoom](https://github.com/francoischalifour/medium-zoom) 을 확인해보세요.

```html
<script src="//unpkg.com/docsify/lib/plugins/zoom-image.min.js"></script>
```

특수 이미지는 제외합니다.

```markdown
![](image.png ":no-zoom")
```

## Edit on github

 `Edit on github` 버튼을 모든 페이지에 넣습니다.  [@njleonzhang](https://github.com/njleonzhang) 가 만들었습니다. [document](https://github.com/njleonzhang/docsify-edit-on-github) 를 확인해 보세요.

## Demo code with instant preview and jsfiddle integration

이 플러그인을 사용하여, 미리보기를 볼 수 있는 샘플코드를 페이지에 즉시 렌더링할 수 있습니다.
데모박스를 확장하면 소스코드와 설명이 나타납니다. `Try in Jsfiddle` 버튼을 누르면,
`jsfiddle.net` 은 코드를 수정할 수 있도록 샘플코드가 열릴 것입니다.

[Vue](https://njleonzhang.github.io/docsify-demo-box-vue/) 와 [React](https://njleonzhang.github.io/docsify-demo-box-react/)  둘 다 지원됩니다.

## Copy to Clipboard

문서에서 예제 코드를 쉽게 복사할 수 있도록 간단한 `Click to copy` 버튼을 생성할 수 있습니다.   [@jperasmus](https://github.com/jperasmus) 가 제공했습니다.

```html
<script src="//unpkg.com/docsify-copy-code"></script>
```

See [here](https://github.com/jperasmus/docsify-copy-code/blob/master/README.md) for more details.

## Disqus

Disqus 댓글기능입니다. https://disqus.com/

```html
<script>
  window.$docsify = {
    disqus: 'shortname'
  }
</script>
<script src="//unpkg.com/docsify/lib/plugins/disqus.min.js"></script>
```

## Gitalk

[Gitalk](https://github.com/gitalk/gitalk) 은 깃헙 이슈에 기반을 둔 최신 댓글 컴포넌트입니다.

```html
<link rel="stylesheet" href="//unpkg.com/gitalk/dist/gitalk.css">

<script src="//unpkg.com/docsify/lib/plugins/gitalk.min.js"></script>
<script src="//unpkg.com/gitalk/dist/gitalk.min.js"></script>
<script>
  const gitalk = new Gitalk({
    clientID: 'Github Application Client ID',
    clientSecret: 'Github Application Client Secret',
    repo: 'Github repo',
    owner: 'Github repo owner',
    admin: ['Github repo collaborators, only these guys can initialize github issues'],
    // facebook-like distraction free mode
    distractionFreeMode: false
  })
</script>
```

## Pagination

Pagination for docsify. By [@imyelo](https://github.com/imyelo)

```html
<script src="//unpkg.com/docsify/lib/docsify.min.js"></script>
<script src="//unpkg.com/docsify-pagination/dist/docsify-pagination.min.js"></script>
```

## codefund

 [codefund](https://codefund.io/) 을 할 수 있는 [plugin](https://github.com/njleonzhang/docsify-plugin-codefund) 입니다.

> codefund 는 "codesponsor" 라는 이름으로 잘 알려져있습니다.

```
<script src="//unpkg.com/docsify/lib/docsify.min.js"></script>

window.$docsify = {
  plugins: [
    DocsifyCodefund.create('xxxx-xxx-xxx') // change to your codefund id
  ]
}
```

## Tabs

마크다운에서 탭으로 표시된 컨텐츠들을 표시해줍니다.

- [Documentation & Demos](https://jhildenbiddle.github.io/docsify-tabs)

 [@jhildenbiddle](https://github.com/jhildenbiddle/docsify-tabs) 가 제공해주었습니다.

## More plugins

 [awesome-docsify](awesome?id=plugins) 를 확인해보세요.
