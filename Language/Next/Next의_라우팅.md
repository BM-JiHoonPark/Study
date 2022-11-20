1. Next.js에는 페이지 개념을 기반으로 구축된 파일 시스템 기반 라우터가 있다.

2. pages 디렉터리 내부에 파일이 추가되면 자동으로 경로로 사용할 수 있다.

3. 라우터는 이름이 index로 지정된 파일을 디렉터리의 루트로 자동 라우팅한다.

    ```
    pages/index.js → /
    pages/blog/index.js → /blog
    ```

4. 중첩된 폴더 구조를 생성하면 동일한 방식으로 자동 라우팅된다.

    ```
    pages/blog/first-post.js → /blog/first-post
    pages/dashboard/settings/username.js → /dashboard/settings/username
    ```

5. 참고자료 : Next.js 공식문서

    ```
    https://nextjs.org/docs/routing/introduction
    ```