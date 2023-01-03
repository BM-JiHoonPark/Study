1. jsx 파일 내부 조건문은 삼항연산자, && 연산자, enum을 사용한다.

2. 삼항연산자 문법

    ```
    {조건문
        ?
        조건이 참일때
        :
        조건이 거짓일때
    }
    ```

3. && 연산자 문법

    ```
    {조건문 &&
        조건이 참일때
    }
    ```

4. enum 문법 (switch)

    ```
    {
        {
            Key1 : value1,
            Key2 : value2,
            Key3 : value3
        }[key]
    }
    ```

5. jsx 파일 내부 반복문은 map을 사용한다.

6. map 문법

    ```
    {array.map((element, index) => {})}
    ```