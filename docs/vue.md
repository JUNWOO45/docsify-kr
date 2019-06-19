# Compatible with Vue

마크다운 파일안에 직접적으로 Vue 컴포넌트를 작성할 수 있습니다. 이 기능을 사용해서 Vue 데모 및 설명서를 함께 쓸 수 있습니다.

## 기본 사용법

`./index.html` 에서 Vue를 불러옵니다.

```html
<script src="//unpkg.com/vue"></script>
<script src="//unpkg.com/docsify"></script>

<!-- Or use the compressed files -->
<script src="//unpkg.com/vue/dist/vue.min.js"></script>
<script src="//unpkg.com/docsify/lib/docsify.min.js"></script>
```

이제 마크다운파일에서 Vue 코드를 즉시 작성할 수 있습니다. `new Vue({ el: '#main' })` 스크립트는 실행되어서 인스턴스를 생성합니다.

*README.md*

````markdown
# Vue 가이드

`v-for` 사용법.

​```html
<ul>
  <li v-for="i in 10">{{ i }}</li>
</ul>
```

<ul>
  <li v-for="i in 10">{{ i }}</li>
</ul>
````

Vue 인스턴스를 수동으로 초기화할 수 있습니다.

*README.md*

​```markdown
# Vue demo

<div id="main">hello {{ msg }}</div>

<script>
  new Vue({
    el: '#main',
    data: { msg: 'Vue' }
  })
</script>
```

!> 마크다운 파일에서, 오직 첫번째 스크립트 태그만 실행됩니다.

## Combine Vuep to write playground

[Vuep](https://github.com/QingWei-Li/vuep) 는 라이브 편집기와 미리보기를 사용하여 Vue 컴포넌트를 렌더링해주는 컴포넌트입니다. Vue 컴포넌트 spec 및 JSX를 지원합니다.

*index.html*

```html
<!-- Inject CSS file -->
<link rel="stylesheet" href="//unpkg.com/vuep/dist/vuep.css">

<!-- Inject JavaScript file -->
<script src="//unpkg.com/vue"></script>
<script src="//unpkg.com/vuep"></script>
<script src="//unpkg.com/docsify"></script>

<!-- or use the compressed files -->
<script src="//unpkg.com/vue/dist/vue.min.js"></script>
<script src="//unpkg.com/vuep/dist/vuep.min.js"></script>
<script src="//unpkg.com/docsify/lib/docsify.min.js"></script>
```

*README.md*
```markdown
# Vuep

<vuep template="#example"></vuep>

<script v-pre type="text/x-template" id="example">
  <template>
    <div>Hello, {{ name }}!</div>
  </template>

  <script>
    module.exports = {
      data: function () {
        return { name: 'Vue' }
      }
    }
  </script>
</script>
```

?>  [Vuep documentation](https://qingwei-li.github.io/vuep/) 에서 다른 예시들을 찾아보세요.
