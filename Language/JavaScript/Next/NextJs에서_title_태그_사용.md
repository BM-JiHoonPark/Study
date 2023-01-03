1. _document.tsx 파일에서 Head 태그 내부에 title 태그 삽입 시 pre-render 될 때에만 title 태그가 렌더링되어 오류가 발생한다.

    ```
    // ErrorCode : <title> should not be used in _document.js's <Head>
    ```

2. _app.tsx 파일에 Head와 title 태그를 이동한다.

    ```
    import '../styles/globals.css'
    import type {AppProps} from 'next/app'
    // 'next/document' 가 아닌 'next/head' 를 import 한다.
    import Head from 'next/head';

    export default function App({Component, pageProps}: AppProps) {
        return (
            <>
                <Head>
                    <title>Create Next App</title>
                </Head>
                <Component {...pageProps} />
            </>
        )
    }
    ```

3. 참고자료 - Next.js 공식 문서

    ```
    https://nextjs.org/docs/messages/no-document-title
    ```