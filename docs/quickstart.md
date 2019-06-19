# 빠른시작

웹사이트를 초기화하고 미리 보는데 도움을 주는 `docsify-cli`를 설치하는 것을 권장합니다.

```bash
npm i docsify-cli -g
```

## 초기화

문서를 `./docs`의 하위 디렉토리에 쓰려면 `init` 커맨드를 사용하십시오.

```bash
docsify init ./docs
```

## 내용 작성

 `init` 이 완료되면,  `./docs` 의 하위 디렉토리에서 파일 목록을 볼 수 있습니다.

- `index.html` 은 설정파일입니다.
- `README.md` 는 홈페이지입니다.
- `.nojekyll` 은 깃헙 페이지가 밑줄로 시작하는 파일을 무시하지 않도록 막아줍니다.

여러분은 `./docs/README.md` 을 쉽게 업데이트할 수 있고, 또한 [더 많은 페이지](more-pages.md)를 만들 수도 있습니다.

## 사이트 미리보기

 `docsify serve` 명령어로 로컬서버를 실행시킵니다.  `http://localhost:3000` 에서 사이트를 미리 볼 수 있습니다.

```bash
docsify serve docs
```

?> `docsify-cli` 에 대해서 더욱 알고 싶다면,  [docsify-cli documentation](https://github.com/docsifyjs/docsify-cli)로 이동하세요.

## 직접 초기화하는 방법

만약 `npm`을 설치하기 싫거나 설치하는데 문제가 있다면, 직접 `index.html` 을 만들면 됩니다 :

```html
<!-- index.html -->

<!DOCTYPE html>
<html>
<head>
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <meta charset="UTF-8">
  <link rel="stylesheet" href="//unpkg.com/docsify/themes/vue.css">
</head>
<body>
  <div id="app"></div>
  <script>
    window.$docsify = {
      //...
    }
  </script>
  <script src="//unpkg.com/docsify/lib/docsify.min.js"></script>
</body>
</html>
```

만약 파이썬을 설치했다면, 스태틱서버를 실행함으로써 쉽게 사이트를 미리볼 수 있습니다

```bash
cd docs && python -m SimpleHTTPServer 3000
```

## 로딩메시지

원한다면 docsify가 문서를 렌더링하기전에 로딩메시지를 보여줄 수 있습니다.

```html
  <!-- index.html -->

  <div id="app">Please wait...</div>
```

만약 `el` 을 수정했다면 `data-app` 속성을 설정해줘야 합니다. :

```html
  <!-- index.html -->

  <div data-app id="main">Please wait...</div>

  <script>
    window.$docsify = {
      el: '#main'
    }
  </script>
```

[el configuration](configuration.md#el) 확인하기.

