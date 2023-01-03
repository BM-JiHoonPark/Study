1. Next.js 사용 시 시스템 요구사항

    ```
    Node.js 12.22.0 이상
    MacOS, Windows(WSL 포함) 및 Linux 지원
    ```

2. npx를 이용하여 next-app을 TypeScript 프로젝트로 시작

    ```
    npx create-next-app@latest --typescript
    ```

3. next 설치 후 react-dom 설치

    ```
    npm install next react react-dom
    ```

4. package.json 내부 scripts 수정

    ```
    "scripts": {
        "dev": "next dev",
        "build": "next build",
        "start": "next start",
        "lint": "next lint"
    }
    ```

5. 참고자료 - Next.js 공식문서

    ```
    https://nextjs.org/docs/getting-started
    ```