webpack은 모듈로 연결된 파일들을 배포용으로 병합하고 포장하는 작업인 번들링을 수행하는 번들러이다.

webpack에는 --mode, --entry --output 총 세가지의 필수 옵션이 존재한다.

--mode -> 개발용일 경우 "development", 운영용일 경우 "production"

--entry -> 번들링의 시작 파일을 지정

--output -> 번들링이 완료된 결과물의 경로를 지정


1. webpack 설치

    ```
    npm install -D webpack webpack-cli
    ```

2. 번들링할 모듈을 생성
 
    ```
    // math.js
    export defalut function sum(a, b) {
        return a + b;
    }

    // app.js
    import { sum } from './math.js';
    console.log(sum(1 + 2));
    ```

3. webpack을 이용하여 번들링 실행

    ```
    node_modules/.bin/webpack --mode development --entry ./app.js --output dist/main.js
    ```

4. html파일에 번들링된 파일을 추가

    ```
    // index.html
    <!DOCTYPE html>
    <html lang="en">
    .
    .
    .
        <body>
            <script src="dist/main.js"></script>
        </body>
    </html>
    ```