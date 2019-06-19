# Deploy

 [GitBook](https://www.gitbook.com) 과 비슷하게, GitHub Pages, GitLab Pages 또는 VPS 에 배포할 수 있습니다..

## GitHub Pages

Github 레포지토리에 문서를 넣는 방법은 세가지가 있습니다:

- `docs/` folder
- master branch
- gh-pages branch

저장소의  `master` 브랜치의 `./docs` 하위폴더에 파일을 저장하는 것을 추천합니다. 그 다음 레포지토리 설정 페이지에서 `master branch /docs folder` 를 Github Pages 소스로 선택하세요.

![github pages](/Users/junwoo/Documents/study/docsify/docs/_images/deploy-github-pages.png)

!> 루트 데릭터리에 파일을 저장하고 `master branch` 를 선택할 수 있습니다.
 `.nojekyll` 파일을 배포위치에 위치시켜야합니다. (예를 들어 `/docs` 또는 the gh-pages branch)

## GitLab Pages

당신의 master 브랜치를 배포하려한다면, `.gitlab-ci.yml`을 다음 스크립트 안에 포함시켜야 합니다:

?> The `.public` workaround is so `cp` doesn't also copy `public/` to itself in an infinite loop.

```YAML
pages:
  stage: deploy
  script:
  - mkdir .public
  - cp -r * .public
  - mv .public public
  artifacts:
    paths:
    - public
  only:
  - master
```

!>  `./docs` 가 Docsify의 하위폴더라면,  `- cp -r docs/. public` 를 교체해야 합니다.

## Firebase Hosting

!> 구글 계정을 이용해서 [Firebase Console](https://console.firebase.google.com) 에 가입한 후에는, `npm i -g firebase-tools` 을 사용해서 Firebase CLI를 설치해야합니다.

터미널을 사용해서  `~/Projects/Docs` 등의 Firebase 프로젝트의 디렉터리를 확인하고 탐색하세요  이 곳에서 `firebase init`, 명령어를 실행하고 메뉴에서 `Hosting` 을 선택하세요 (선택에는 **space** 를 누르고, **arrow keys** 로 옵션을 변경하고 **enter** 로 확정을 합니다). setup instructions을 따르세요.

당신은 다음과 비슷한 `firebase.json` 파일을 가지고 있을 것입니다.( `public` 에서 `site` 로 배포 디렉터리를 변경해놓은 상태입니다):

```json
{
  "hosting": {
    "public": "site",
    "ignore": ["firebase.json", "**/.*", "**/node_modules/**"]
  }
}
```

완료되면,  `docsify init ./site` ( `firebase init` 을 실행할 때 당신이 결정한 배포 디렉터리로 대체 - 기본적으로 공용)을 실행하여 시작 템플릿을 빌드하세요. 문서를 추가/편집한 이후, 프로젝트 기본 디렉터리에서 `firebase deploy` .를 실행하세요.

## VPS

nginx 구성을 따르세요.

```nginx
server {
  listen 80;
  server_name  your.domain.com;

  location / {
    alias /path/to/dir/of/docs/;
    index index.html;
  }
}
```

## Netlify

1. [Netlify](https://www.netlify.com/) 계정으로 로그인하세요.
2. [dashboard](https://app.netlify.com/) 페이지에서,  **New site from Git** 를 누르세요.
3. 문서를 저장한 저장소를 누르고,  **Build Command** 공간은 공백으로 남겨둔 채,  Publish directory 를 `index.html` 의 디렉터리로 채웁니다. 예를 들어,  `docs/index.html` 로 지정하려는 경우 docs가 되어야 합니다.

### HTML5 router

HTML5 router를 사용하려는 경우, 모든 요청을 `index.html` 로 리디렉션하는 리디렉션 규칙을 설정해야하며, Netlify를 사용한다면 매우 간단합니다. docs directory에 `\redirects` 파일을 채우면 됩니다:

```sh
/*    /index.html   200
```

## AWS Amplify

1. Docsify 프로젝트의 `index.html` 에 있는 routerMode를 *history* 로 설정합니다.

```html
<script>
    window.$docsify = {
      loadSidebar: true,
      routerMode: 'history'
    }
</script>
```

2. [AWS Console](https://aws.amazon.com) 에 로그인 합니다.
3. [AWS Amplify Dashboard](https://aws.amazon.com/amplify) 로 이동합니다.
4. 프로젝트를 설정하기위해 **Deploy** route를 선택합니다.
5. 루트 디렉터리 내에서 문서를 서비스하는 경우에 빌드 설정을 비워두라는 메세지가 표시되면 이 설정을 비워두세요. 
6. 다른 디렉터리에서 문서를 서비스하는 경우, amplify.yml을 커스터마이징 하세요.

```yml
version: 0.1
frontend:
  phases:
    build:
      commands: 
        - echo "Nothing to build"
  artifacts:
    baseDirectory: /docs
    files:
      - '**/*'
  cache:
    paths: []

```

6. 표시된 순서대로 리디렉션 규칙을 추가하세요.

| Source address | Target address | Type          |
| -------------- | -------------- | ------------- |
| /<*>.md        | /<*>.md        | 200 (Rewrite) |
| /<*>           | /index.html    | 200 (Rewrite) |

