1. error 내용

    ```
    react add a fallback 'resolve.fallback crypto require.resolve( crypto-browserify )'
    ```

2. webpack4버전 이하에는 브라우저 호환성을 위해 Node.js 모듈에 대한 polyfill을 자동으로 제공했지만 대부분의 polyfill이 불필요하게 적용되어 bundle size를 증가시키기 때문에 5버전 이상에서 제거됨

3. webpack 파일 추출

    ```
    npm run eject

    # 저장이나 git commit을 하지 않았을 경우 에러
    # Remove untracked files, stash or commit any changes, and try again error
    ```

4. crypto-browserify 설치

    ```
    npm install crypto-browserify
    ```

5. webpack.config.js 파일에 fallback 수동 등록

    ```
    module.exports {
        ...
        resolve: {
            ...
            fallback: {
                "crypto": require.resolve( crypto-browserify )
            }
        }
    }
    ```