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

3. webpack config 파일 생성

    ```
    const path = require('path');

    module.exports = {
        mode: 'development',
        entry: {
            main: './app.js'
        },
        output: {
            path: path.resolve(./dest),
            filename: '[name].js'
        }
    }
    ```

4. package.json에 등록

    ```
    {
        ...

        "scripts": {
           "build": "webpack", 
        }

        ...
    }
    ```

5. 번들링 실행

    ```
    npm run build
    ```

5. html파일에 번들링된 파일을 추가

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