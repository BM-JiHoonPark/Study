React 다른 component function 호출

1. component 및 function 생성

    Api.js

    ```
    export function getFunctionA() {

        console.log(0);

    }


    export function getFunctionB() {

        console.log(1);

    }
    ```

2. function을 가지고 올 수 있도록 component import

    ```
    import * as api from './Api.js';
    ```

3. function 호출

    ```
    api.getFucntionA();
    
    api.getFucntionB();
    ```