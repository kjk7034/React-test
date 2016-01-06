# React 튜토리얼 따라해보기
http://reactkr.github.io/react/docs/tutorial-ko-KR.html
0.14.0 alpha1 한글판을 읽으면서 하나씩 따라해보는 중... 따라하면서 느낌점을 적었으며, 기본 설명은 해당 사이트를 통해서 확인.

현재 0.14.5 버전이 있지만, 일단 0.14.0 으로 시작함.

0.14.0은 JSXTransformer-0.14.0-alpha.js을 사용하고 있고, 0.14.5는 babel을 사용하여 설명을 하고 있음.

현재 0.14.0은 다운로드 링크가 깨져 있어서 CDN 주소에서 다운 받아서 활용 (https://cdnjs.com/libraries/react/0.14.0-alpha1)

## 테스트 파일 설명

- helloworld.html (Helloworld)

기본적인 React.render 문법 이해

- tutorial-1.html (JSX 유,무 문법차이)

text/jsx 를 사용한 문법과 사용하지 않은 문법 비교

- tutorial-2.html (컴포넌트 조합)

React.createClass로 생성한 컴포넌트들의 조합

- tutorial-3.html (props / 컴포넌트 조합)

props를 이용하여 데이터를 전달 받는 샘플

- tutorial-4.html (Markdown 추가하기)

marked 라이브러리를 호출, React는 이런 식으로 XSS 공격을 예방합니다. 우회할 방법이 있긴 하지만 프레임워크는 사용하지 않도록 경고하고 있습니다.

- tutorial-5.html (Markdown 추가하기 - dangerouslySetInnerHTML API 활용)

추천하지 않는 이유(https://github.com/facebook/react/blob/master/docs/tips/19-dangerously-set-inner-html.ko-KR.md)는 해당 번역본에서 자세히 확인.

## 작업중 발생한 이슈들 모음

### tutorial-2.html 내용

<pre>
return (
            &lt;h1&gt;댓글&lt;/h1&gt;
            &lt;CommentList /&gt;
            &lt;CommentForm /&gt;
       )
</pre>
이와 같이 return 하면 "Adjacent JSX elements must be wrapped in an enclosing tag" 의 오류가 발생함.

<pre>
return (
        &lt;div&gt;
            &lt;h1&gt;댓글&lt;/h1&gt;
            &lt;CommentList /&gt;
            &lt;CommentForm /&gt;
        &lt;/div/&gt;
       )
</pre>
이와 같이 **&lt;div&gt;로 한번 감싸서 하나의 컴포넌트로 return!!**

참고 : http://stackoverflow.com/questions/31284169/uncaught-error-parse-error-line-38-adjacent-jsx-elements-must-be-wrapped-in-a





