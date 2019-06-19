# Embed files

docsify 4.6부터, 이제 어떤 종류의 파일이든 내장가능해졌습니다.
비디오, 오디오, iframes, 코드 블럭, 심지어 마크다운 파일들도 문서에 직접 내장될 수 있습니다.

예를 들어, 마크다운 파일을 내장하려면 다음과 같이 작성하면 됩니다.

```markdown
[filename](_media/example.md ':include')
```

 `example.md` 의 컨텐츠는 다음과 같이 보이게 될 것입니다.

[filename](_media/example.md ':include')

 [example.md](_media/example.md ':ignore') 의 원본을 확인해볼 수 있습니다.

일반적으로는 링크로 컴파일될테지만, docsify에서는 `:include` 가 포함된다면 내장 파일로 취급합니다.

## 내장 파일 타입

현재, 파일 확장자는 자동적으로 인식되며 각각 다른 방식으로 내장됩니다.

지원되는 타입은 다음과 같습니다.

* **iframe** `.html`, `.htm`
* **markdown** `.markdown`, `.md`
* **audio** `.mp3`
* **video** `.mp4`, `.ogg`
* **code** other file extension

물론, 강제로 변환시킬 수 있습니다. 예를 들어, 마크다운 파일을 코드블럭으로 내장시킬 수 있습니다.

```markdown
[filename](_media/example.md ':include :type=code')
```

다음과 같은 결과로 나타납니다.

[filename](_media/example.md ':include :type=code')

## 내장된 코드 조각
때로는 파일 전체를 담고 싶지 않을 때도 있습니다. 몇 줄만 있으면 CI에서 파일을 컴파일하고 테스트할 수 있기 때문일 것입니다.

```markdown
[filename](_media/example.js ':include :type=code :fragment=demo')
```

코드 파일에서 코드 일부분을 `/// [demo]`  로 둘러싸야 합니다.  (코드 앞 뒤로).  
또는 `### [demo]` 를 사용할 수 있습니다.

예를 들어:

[filename](_media/example.js ':include :type=code :fragment=demo')


## 태그 속성

파일을 `iframe`, `audio` 와 `video` 로 내장하게 된다면 다음과 같은 태그 속성들을 설정해야 할 수 있습니다.

```markdown
[cinwell website](https://cinwell.com ':include :type=iframe width=100% height=400px')
```

[cinwell website](https://cinwell.com ':include :type=iframe width=100% height=400px')

확인했나요? 직접 쓰기만하면 됩니다. [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) 에서 속성들에대해 확인해볼 수 있습니다.

## 코드 하이라이트

모든 유형의 소스 코드 파일을 포함시킨다면, 하이라이트된 언어를 지정하거나 자동으로 식별할 수 있습니다.

```markdown
[](_media/example.html ':include :type=code text')
```

⬇️

[](_media/example.html ':include :type=code text')

?> 하이라이트하는 방법을 알고싶다면 [여기](language-highlight.md) 를 확인해보세요.
