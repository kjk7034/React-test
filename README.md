
React 한글 번역본 따라해보기 !!
http://reactkr.github.io/react/docs/getting-started-ko-KR.html

다운로드 관련 파일은 이곳 CDN에서 확인
https://cdnjs.com/libraries/react/0.14.0-alpha1

/*
먼저 커맨드라인 도구를 설치합니다. (npm 필요):
npm install -g react-tools
*/

 1. helloworld.html
 2. tutorial-1.html
 3. tutorial-2.html
 4. tutorial-3.html
 5. tutorial-4.html

작업중
return (
            <h1>댓글</h1>
            <CommentList />
            <CommentForm />
       )

       이와 같이 return 하면 "Adjacent JSX elements must be wrapped in an enclosing tag" 의 오류가 발생함.

return (
        <div>
            <h1>댓글</h1>
            <CommentList />
            <CommentForm />
        </div>
       )
       이와 같이 <div>로 한번 감싸서 하나의 객체를 return 해서 해결!!
참고 : http://stackoverflow.com/questions/31284169/uncaught-error-parse-error-line-38-adjacent-jsx-elements-must-be-wrapped-in-a



