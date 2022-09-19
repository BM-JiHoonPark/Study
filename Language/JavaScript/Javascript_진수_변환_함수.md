1. Javascript에서 진수 변환을 지원하는 toString, perseInt 함수가 존재

2. toString 함수는 숫자를 진수로 변환

    ```
    let intNum = 3;
    intNum.toString(2);	// 숫자를 2진수로 변환 = 11
    ```

3. perseInt 함수는 진수를 숫자로 변환

    ```
    let stringNum = 11;
    stringNum.parseInt(2);	// 2진수를 숫자로 변환 = 3
    ```