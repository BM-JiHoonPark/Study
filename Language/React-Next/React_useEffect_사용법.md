1. useEffect란 컴포넌트가 렌더링 될 때 특정 작업을 실행하는 Hook

3. useEffect를 사용하기 위해 useEffect import

    ```
    import React, { useEffect } from "react";
    ```

4. useEffect 기본 문법

    ```
    useEffect(() => {

        console.log("마운트 될 때만 실행");

    }, []);

    
    useEffect(() => {

        console.log("렌더링 될 때 마다 실행");
        
    });
    ```