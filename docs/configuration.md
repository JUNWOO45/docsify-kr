# Configuration

 `window.$docsify` 를 설정할 수 있습니다.

```html
<script>
  window.$docsify = {
    repo: 'docsifyjs/docsify',
    maxLevel: 3,
    coverpage: true
  }
</script>
```

## el

- Type: `String`
- Default: `#app`

초기에 마운트 될 DOM 요소입니다. CSS선택자나 실제 HMLElement일 수 있습니다.

```js
window.$docsify = {
  el: '#app'
};
```

## repo

- Type: `String`
- Default: `null`

저장소 url이나  `username/repo` 를 오른쪽 상단 구석에  [GitHub Corner](http://tholman.com/github-corners/) 위젯에 추가할 수 있습니다.

```js
window.$docsify = {
  repo: 'docsifyjs/docsify',
  // or
  repo: 'https://github.com/docsifyjs/docsify/'
};
```

## maxLevel

- Type: `Number`
- Default: `6`

최대 목차 레벨.

```js
window.$docsify = {
  maxLevel: 4
};
```

## loadNavbar

- Type: `Boolean|String`
- Default: `false`

 값이 **true** 면 `_navbar.md` 이나 지정한 위치에서 네비게이션바를 로드합니다.

```js
window.$docsify = {
  // load from _navbar.md
  loadNavbar: true,

  // load from nav.md
  loadNavbar: 'nav.md'
};
```

## loadSidebar

- Type: `Boolean|String`
- Default: `false`

  값이 **true** 면, `_sidebar.md` 이나 지정한 위치에서 사이드바를 로드합니다.

```js
window.$docsify = {
  // load from _sidebar.md
  loadSidebar: true,

  // load from summary.md
  loadSidebar: 'summary.md'
};
```

## subMaxLevel

- Type: `Number`
- Default: `0`

커스텀 사이드바에 목차를 추가할 수 있습니다.

```js
window.$docsify = {
  subMaxLevel: 2
};
```

## auto2top

- Type: `Boolean`
- Default: `false`

라우트가 바뀌었을때 스크롤을 화면 최상단으로 올려줍니다.

```js
window.$docsify = {
  auto2top: true
};
```

## homepage

- Type: `String`
- Default: `README.md`

폴더내의 `README.md` 이 사이트의 홈페이지 역할을 하게 됩니다. 하지만 때로는 홈페이지가 될 다른 파일이 필요할 수도 있습니다.

```js
window.$docsify = {
  // Change to /home.md
  homepage: 'home.md',

  // Or use the readme in your repo
  homepage:
    'https://raw.githubusercontent.com/docsifyjs/docsify/master/README.md'
};
```

## basePath

- Type: `String`

웹사이트의 기본 주소입니다. 다른 디렉터리나 다른 도메인주소로 세팅할 수 있습니다.

```js
window.$docsify = {
  basePath: '/path/',

  // Load the files from another site
  basePath: 'https://docsify.js.org/',

  // Even can load files from other repo
  basePath:
    'https://raw.githubusercontent.com/ryanmcdermott/clean-code-javascript/master/'
};
```

## relativePath

- Type: `Boolean`
- Default: `false`

 **true**면, 현재 위치의 상대경로값으로 연결됩니다.

예를들어, 현재 디렉터리 구조가 다음과 같다면:

```text
.
└── docs
    ├── README.md
    ├── guide.md
    └── zh-cn
        ├── README.md
        ├── guide.md
        └── config
            └── example.md
```

상대경로를 **사용할 수 있습니다.** 현재 URL이 `http://domain.com/zh-cn/README`, 라면 다음처럼 사용할 수 있습니다.

```text
guide.md              => http://domain.com/zh-cn/guide
config/example.md     => http://domain.com/zh-cn/config/example
../README.md          => http://domain.com/README
/README.md            => http://domain.com/README
```

```js
window.$docsify = {
  // Relative path enabled
  relativePath: true,

  // Relative path disabled (default value)
  relativePath: false
};
```

## coverpage

- Type: `Boolean|String|String[]|Object`
- Default: `false`

 [커버 기능](cover.md) 을 사용하세요. 값이 true면, `_coverpage.md` 에서 커버페이지를 로드합니다.

```js
window.$docsify = {
  coverpage: true,

  // Custom file name
  coverpage: 'cover.md',

  // mutiple covers
  coverpage: ['/', '/zh-cn/'],

  // mutiple covers and custom file name
  coverpage: {
    '/': 'cover.md',
    '/zh-cn/': 'cover.md'
  }
};
```

## logo

- Type: `String`

사이드바에 표시되는 웹사이트 로고입니다.CSS로 사이즈조정이 가능합니다.

```js
window.$docsify = {
  logo: '/_media/icon.svg'
};
```

## name

- Type: `String`

사이드바에 보일 웹사이트 이름입니다.

```js
window.$docsify = {
  name: 'docsify'
};
```

## nameLink

- Type: `String`
- Default: `window.location.pathname`

링크의 이름입니다.

```js
window.$docsify = {
  nameLink: '/',

  // For each route
  nameLink: {
    '/zh-cn/': '/zh-cn/',
    '/': '/'
  }
};
```

## markdown

- Type: `Function`

 [Markdown configuration](markdown.md) 을 확인해 보세요.

```js
window.$docsify = {
  // object
  markdown: {
    smartypants: true,
    renderer: {
      link: function() {
        // ...
      }
    }
  },

  // function
  markdown: function(marked, renderer) {
    // ...
    return marked;
  }
};
```

## themeColor

- Type: `String`

테마 색상을 커스터마이징하세요. [CSS3 variables](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_variables) 기능을 사용하고, 오래된 브라우저에서는 폴리필을 사용하세요.

```js
window.$docsify = {
  themeColor: '#3F51B5'
};
```

## alias

- Type: `Object`

라우트명을 설정하세요. 자유롭게 라우팅규칙을 설정할 수 있습니다. RegExp를 지원합니다.

```js
window.$docsify = {
  alias: {
    '/foo/(+*)': '/bar/$1', // supports regexp
    '/zh-cn/changelog': '/changelog',
    '/changelog':
      'https://raw.githubusercontent.com/docsifyjs/docsify/master/CHANGELOG',
    '/.*/_sidebar.md': '/_sidebar.md' // See #301
  }
};
```

## autoHeader

- type: `Boolean`

 `loadSidebar` 와 `autoHeader` 를 모두 사용중인 경우,  `_sidebar.md` 의 각 링크에 대해, 헤더를 html로 변환하기 전에 페이지를 미리 확인할 수 있습니다.  [#78](https://github.com/docsifyjs/docsify/issues/78) 를 확인해보세요.

```js
window.$docsify = {
  loadSidebar: true,
  autoHeader: true
};
```

## executeScript

- type: `Boolean`

페이지에서 스크립트를 실행합니다. 첫번째 스크립트 태그만 해석가능합니다. 만약 Vue를 사용중이라면, 자동으로 활성화됩니다.

```js
window.$docsify = {
  executeScript: true
};
```

```markdown
## This is test

<script>
  console.log(2333)
</script>
```

jsfiddle데모와 같은 외부 스크립트를 돌리고 있다면, [외부 스크립트 플러그인](https://docsify.js.org/#/plugins?id=external-script)을 반드시 포함시키세요.

##noEmoji

## noEmoji

- type: `Boolean`

이모지 parse를 끕니다.

```js
window.$docsify = {
  noEmoji: true
};
```

## mergeNavbar

- type: `Boolean`

작은화면에서 네비게이션바를 사이드바에 합칩니다.

```js
window.$docsify = {
  mergeNavbar: true
};
```

## formatUpdated

- type: `String|Function`

 **{docsify-updated<span>}</span>** 변수를 통해 파일 업데이트 날짜를 표시할 수 있습니다.
 https://github.com/lukeed/tinydate#patterns 를 확인하세요.

```js
window.$docsify = {
  formatUpdated: '{MM}/{DD} {HH}:{mm}',

  formatUpdated: function(time) {
    // ...

    return time;
  }
};
```

## externalLinkTarget

- type: `String`
- default: `_blank`

외부링크를 열 수 있습니다. 기본값은 `'_blank'` 입니다.(new window/tab)

```js
window.$docsify = {
  externalLinkTarget: '_self' // default: '_blank'
};
```

## routerMode

- type: `String`
- default: `hash`

```js
window.$docsify = {
  routerMode: 'history' // default: 'hash'
};
```

## noCompileLinks

- type: `Array`

때때로, docsify가 링크처리를 하지 않길 원할 수 있습니다. [#203](https://github.com/docsifyjs/docsify/issues/203) 를 확인하세요.

```js
window.$docsify = {
  noCompileLinks: ['/foo', '/bar/.*']
};
```

## onlyCover

- type: `Boolean`

홈페이지를 방문했을때 커버페이지만 로드됩니다.

```js
window.$docsify = {
  onlyCover: false
};
```

## requestHeaders

- type: `Object`

리퀘스트헤더를 설정할 수 있습니다.

```js
window.$docsify = {
  requestHeaders: {
    'x-token': 'xxx'
  }
};
```

## ext

- type: `String`

파일 확장자를 요청할 수 있습니다.

```js
window.$docsify = {
  ext: '.md'
};
```

## fallbackLanguages

- type: `Array<string>`

페이지가 요청되었지만, 지정된 로컬에 존재하지않을때 기본 언어로 대체되는 언어 목록입니다.

예시:

-  `/de/overview` 를 가져오려고 합니다. 페이지가 있으면, 화면에 표시됩니다.
- 그 다음엔 `/overview` 페이지를 가져오려고 합니다.(기본 언어에 따라 다름). 페이지가 있으면, 화면에 표시됩니다.
- 그 다음에 404페이지를 보여줍니다.

```js
window.$docsify = {
  fallbackLanguages: ['fr', 'de']
};
```

## notFoundPage

- type: `Boolean` | `String` | `Object`

`_404.md` 을 로드합니다:

```js
window.$docsify = {
  notFoundPage: true
};
```

커스터마이징한 404페이지를 불러옵니다:

```js
window.$docsify = {
  notFoundPage: 'my404.md'
};
```

하위 디렉터리구분에 따른 적절한 404페이지를 로드합니다:

```js
window.$docsify = {
  notFoundPage: {
    '/': '_404.md',
    '/de': 'de/_404.md'
  }
};
```

> 주의:  fallbackLanguages 옵션은 `notFoundPage`  옵션과 함께 동작하지 않습니다.
