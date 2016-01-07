# React 튜토리얼 따라해보기
http://reactkr.github.io/react/docs/tutorial-ko-KR.html
0.14.0 alpha1 한글판을 읽으면서 하나씩 따라해보는 중... 따라하면서 느낌점을 적었으며, 기본 설명은 해당 사이트를 통해서 확인.

현재 0.14.5 버전이 있지만, 일단 0.14.0 으로 시작함.

0.14.0은 JSXTransformer-0.14.0-alpha.js을 사용하고 있고, 0.14.5는 babel을 사용하여 설명을 하고 있음.

현재 0.14.0은 다운로드 링크가 깨져 있어서 CDN 주소에서 다운 받아서 활용 (https://cdnjs.com/libraries/react/0.14.0-alpha1)

## 테스트 파일 설명

  직접따라 해보면서 느낌점과 한글판 문서의 내용을 참고해서 정리.

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

  추천하지 않는 이유( https://github.com/facebook/react/blob/master/docs/tips/19-dangerously-set-inner-html.ko-KR.md )는 해당 번역본에서 자세히 확인.

- tutorial-6.html (데이터 모델 연결하기)

  json 형태의 data객체를 this.props을 통해서 전달되는 과정 확인.

  그리고 this.props.data.map 에서 underscore에서 보던 .map을 보게 되었다. React.Children.map ( https://facebook.github.io/react/docs/top-level-api.html )과 같이 사용할 수 있다.

  **Each child in an array or iterator should have a unique "key" prop.** 발생 이슈 참고.

- tutorial-7.html (데이터 서버에서 가져오기(Fetching))

  state, componentDidMount에 대한 이해가 필요. (아래 설명은 번역글 내용 중 일부)

  지금까지, 각각의 컴포넌트는 props를 기반으로 한번 렌더되었습니다. props는 불변성을 갖습니다: 그것들은 부모에서 전달되어 부모에게 "소유" 되어 있습니다. 컴포넌트에 상호작용을 구현하기 위해서, 가변성을 갖는 state를 소개합니다. this.state는 컴포넌트에 한정(private)되며 this.setState()를 통해 변경할 수 있습니다. state가 업데이트 되면, 컴포넌트는 자신을 스스로 다시 렌더링합니다.

  render() 메소드는 this.props와 this.state를 위한 함수로 선언적으로 작성됩니다. 프레임워크에서 입력값에 따른 UI가 항상 일관성 있음을 보장해줍니다.

  여기서 componentDidMount는 컴포넌트가 렌더링 된 다음 React에 의해 자동으로 호출되는 메소드입니다. 동적 업데이트의 핵심은 this.setState()의 호출입니다. 우리가 이전의 댓글 목록을 서버에서 넘어온 새로운 목록으로 변경하면 자동으로 UI가 업데이트 될 것입니다. 이 반응성 덕분에 실시간 업데이트에 아주 작은 수정만 가해집니다. 우리는 여기선 간단한 폴링을 사용.

- tutorial-8.html (데이터 서버에서 가져오기(Fetching) - setInterval 적용)

  7번 예제에서 ajax 호출을 변도의 메소드로 분리하고, 2초마다 계속 호출하게 함. **주의 : {2000}을 "{2000}"으로 적용하면 Number가 아닌 String으로 받아서 2초마다가 아닌 계속 적용됨.**

- tutorial-9.html (새로운 댓글 추가하기)

  자식 컴포넌트의 이름을 지정하기 위해 **ref** 어트리뷰트를, 컴포넌트를 참조하기 위해 **this.refs**를 사용, .trim()으로 문자열 양쪽 끝의 공백을 제거

  props으로 콜백 처리 : CommentBox가 댓글목록의 state를 소유하고 있기 때문에 이 로직 또한 CommentBox에 있는것이 타당합니다. 자식 컴포넌트가 그의 부모에게 데이터를 넘겨줄 필요가 있습니다. 부모의 render 메소드에서 새로운 콜백(handleCommentSubmit)을 자식에게 넘겨주고, 자식의 onCommentSubmit 이벤트에 그것을 바인딩해주는 식으로 구현합니다. 이벤트가 작동될때(triggered)마다, 콜백이 호출됩니다:

- tutorial-10.html (새로운 댓글 추가시 조금 더 빠르게 느껴지게 하는 TIP??)

  POST를 하기 전에 this.setState를 이용하여 concat한 배열을 먼저 적용해서 빠른것 처럼 보이게 할 수는 있겠지만, ajax를 통해서 success가 아닌 경우에는 Front 오류... 이 방법이 왜 좋다고 설명하는지 잘 모르겠음.

  사이트 예제에서 2초후 적용되게 수정(이유 : 서버쪽 POST처리를 안해서 깜빡이는 느낌이 나서...)

## 작업중 발생한 이슈들 모음

### tutorial-2.html 내용

<pre>
return (
            &lt;h1&gt;댓글&lt;/h1&gt;
            &lt;CommentList /&gt;
            &lt;CommentForm /&gt;
       )
</pre>
이와 같이 return 하면 "**Adjacent JSX elements must be wrapped in an enclosing tag**" 의 오류가 발생함.

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

### tutorial-6.html 내용

<pre>
var commentNodes = this.props.data.map(function (comment){
    return (
        &lt;Comment author={comment.author}&gt;
            {comment.text}
        &lt;/Comment&gt;
    )
})
</pre>

위와 같이 작업을 했을 때는 **Warning: Each child in an array or iterator should have a unique "key" prop. Check the render method of CommentList. See https://fb.me/react-warning-keys for more information.** Warning이 발생했다.

key값을 다음과 같이 설정해줘서 해결했다.

<pre>
var commentNodes = this.props.data.map(function (comment, idx){
    return (
        &lt;Comment author={comment.author} key={idx}&gt;
            {comment.text}
        &lt;/Comment&gt;
    )
})
</pre>

## 기타

- 자동으로 HTML을 JSX로 변환해주는 Compiler( https://facebook.github.io/react/html-jsx.html )를 통해서 HTML이 JSX로 어떻게 변하는지 볼수 있었다.

- JSX Compiler Service ( https://facebook.github.io/react/jsx-compiler.html )를 검색해보니, **This tool has been removed as JSXTransformer has been deprecated.** 라고 되어있었고, Babel을 쓰라고 되어있다. 그래서 0.14.5에서는 JSX가 아닌 Babel을 사용한 듀토리얼을 제공하고 있는 것 같다.
