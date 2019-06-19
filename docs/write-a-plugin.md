# Write a plugin

플러그인은 `hook` 을 인자로 받는 간단한 함수입니다. hook은 비동기처리를 지원합니다.

## 전체 구성

```js
window.$docsify = {
  plugins: [
    function(hook, vm) {
      hook.init(function() {
        // 스크립트가 실행되기 시작할때 호출됨. 한번만 트리거되며 인자는 없음.
      });

      hook.beforeEach(function(content) {
        // 마크다운파일을 해석하기전에 매번 호출됨.
        // ...
        return content;
      });

      hook.afterEach(function(html, next) {
        // 마크다운파일을 해석하기전에 매번 호출됨.
        // beforeEach 와 afterEach 는 동기적인 상황을 지원。
        // ...
        // task가 끝나면 `next(html)`호출.
        next(html);
      });

      hook.doneEach(function() {
        // 데이터가 완전히 로드된 후 매번 호출됨. 인자는 없음
        // ...
      });

      hook.mounted(function() {
        // 초기 완료 후 호출됨. 한번만 트리거되고 인수는 없음.
      });

      hook.ready(function() {
        // 초기 완료 후 호출됨. 인수는 없음.
      });
    }
  ]
};
```

!>  `window.Docsify` 을 통해 내부 메소드를 얻을 수 있습니다. 두번째 인자를 통해 현재 인스턴스를 얻을 수 있습니다.

## 예시

#### footer

footer 컴포넌트를 모든 페이지에 더하기.

```js
window.$docsify = {
  plugins: [
    function(hook) {
      var footer = [
        '<hr/>',
        '<footer>',
        '<span><a href="https://github.com/QingWei-Li">cinwell</a> &copy;2017.</span>',
        '<span>Proudly published with <a href="https://github.com/docsifyjs/docsify" target="_blank">docsify</a>.</span>',
        '</footer>'
      ].join('');

      hook.afterEach(function(html) {
        return html + footer;
      });
    }
  ]
};
```

### Edit Button

```js
window.$docsify = {
  plugins: [
    function(hook, vm) {
      hook.beforeEach(function(html) {
        var url =
          'https://github.com/docsifyjs/docsify/blob/master/docs/' +
          vm.route.file;
        var editHtml = '[📝 EDIT DOCUMENT](' + url + ')\n';

        return (
          editHtml +
          html +
          '\n----\n' +
          'Last modified {docsify-updated} ' +
          editHtml
        );
      });
    }
  ]
};
```

## Tips

### docsify version 가져오기

```
console.log(window.Docsify.version)
```

Current version: <span id='tip-version'>loading</span>

<script>
document.getElementById('tip-version').innerText = Docsify.version
</script>
