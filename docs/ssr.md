# Server-Side Rendering

https://docsify.now.sh를 확인해보세요

레포지토리 주소 : https://github.com/docsifyjs/docsify-ssr-demo

## 왜 SSR인가?
- 더 나은 SEO
- 멋있어서

## 빠른 시작

프로젝트에 `now` 와 `docsify-cli` 를 설치하세요.

```bash
npm i now docsify-cli -D
```

만약 문서가 `./docs` 의 하위 디렉터리 아래에 있다면, `package.json` 를 수정하세요. 

```json
{
  "name": "my-project",
  "scripts": {
    "start": "docsify start . -c ssr.config.js",
    "deploy": "now -p"
  },
  "files": [
    "docs"
  ],
  "docsify": {
    "config": {
      "basePath": "https://docsify.js.org/",
      "loadSidebar": true,
      "loadNavbar": true,
      "coverpage": true,
      "name": "docsify"
    }
  }
}
```

!>  `basePath` 는 webpack의 `publicPath` 와 같습니다. 로컬이나 원격 파일을 사용할 수 있습니다.

작동하는지 로컬에서 미리 볼 수 있습니다.

```bash
npm start

# open http://localhost:4000
```

Publish it!

```bash
now -p
```

이제 SSR에 대한 준비가 끝났습니다.

## 사용자 지정 템플릿

다음과 같은 전체 페이지의 HTML에 대한 템플릿은 제공할 수 있습니다.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>docsify</title>
  <meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
  <link rel="stylesheet" href="//unpkg.com/docsify/themes/vue.css" title="vue">
</head>
<body>
  <!--inject-app-->
  <!--inject-config-->
  <script src="//unpkg.com/docsify/lib/docsify.js"></script>
  <script src="//unpkg.com/docsify/lib/plugins/search.js"></script>
  <script src="//unpkg.com/prismjs/components/prism-bash.min.js"></script>
  <script src="//unpkg.com/prismjs/components/prism-markdown.min.js"></script>
  <script src="//unpkg.com/prismjs/components/prism-nginx.min.js"></script>
</body>
</html>
```

템플릿에는 렌더링된 앱 콘텐츠에 대한 설명이 포함되어야 합니다.
 - `<!--inject-app-->`
 - `<!--inject-config-->`

## 환경 설정

특수한 config 파일이나 `package.json` 에서 설정할 수 있습니다.

```js
module.exports = {
  template: './ssr.html',
  maxAge: 60 * 60 * 1000, // lru-cache config
  config: {
   // docsify config
  }
}
```

## VPS에 맞게 배포

 `docsify start` 를 Node 서버에서 직접 실행하거나,  `docsify-server-renderer` 를 이용해서 서버앱을 작성할 수 있습니다.

```js
var Renderer = require('docsify-server-renderer')
var readFileSync = require('fs').readFileSync

// init
var renderer = new Renderer({
  template: readFileSync('./docs/index.template.html', 'utf-8'),
  config: {
    name: 'docsify',
    repo: 'docsifyjs/docsify'
  }
})

renderer.renderToString(url)
  .then(html => {})
  .catch(err => {})
```
