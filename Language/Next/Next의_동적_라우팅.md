1. Next.js에서는 페이지에 대괄호를 추가하여 동적 경로를 생성할 수 있다.

    ```
    /post/abc

    =>

    pages/post/[pid].js

    {"pid": "abc"}

    ---

    /post/abc?foo=bar

    =>

    pages/post/[pid].js

    {"pid": "abc", "foo": "bar"}
    ```

2. 경로 매개변수는 동일한 이름의 쿼리 매개변수를 재정의한다.

    ```
    /post/abc?pid=123
    
    =>

    pages/post/[pid].js

    {"pid": "123"}
    ```

3. 일치하는 경로의 매개변수는 페이지에 쿼리 매개변수로 전송된다.

    ```
    import { useRouter } from 'next/router'

    const Post = () => {
        const router = useRouter()
        const { pid } = router.query

        return <p>Post: {pid}</p>
    }

    export default Post
    ```

4. 복수의 매개변수 사용

    ```
    /post/a/b/c

    =>

    pages/post/[...slug].js

    {"slug": ["a", "b", "c"]}
    ```

5. 복수의 매개변수와 단일 매개변수 혼용 시

    ```
    /post
    /post/a
    /post/a/b/c

    =>

    pages/post/[[...slug]].js

    {}
    {"slug": ["a"]}
    {"slug": ["a", "b", "c"]}
    ```
    
6. 참고자료 : Next.js 공식문서

    ```
    https://nextjs.org/docs/routing/dynamic-routes
    ```