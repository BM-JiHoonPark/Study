1. REST API (GET, POST, PUT, DELETE) 를 구현하기 위해 Fetch를 사용

2. 비동기 데이터 처리를 지원하기 위해 async-await를 사용

3. 코드 재사용 및 관리를 위하여 API 파일에 Function으로 등록

    Api.js

    ```
    export async function getTestApi() {
        try {
            return await fetch(url)
            .then(function (response) { return response.json() })
            .catch((error) => console.log("error:", error));
        } catch (error) {
            console.log(error);
            return 0;
        }
    }
    ```

4. 데이터를 비동기 처리 후 변수에 담기 위해 setData를 사용

5. Promise 데이터 처리를 위해 then 함수 활용

6. 데이터를 불러온 후 페이지를 다시 렌더링 시키기 위해 빈 배열일 경우 useEffect를 실행

    Page.js

    ```
    const [data, setData] = useState([]);
    const getData = () => {
        api.getTestApi().then(function(data) {
            setData(data);
        });
    }

    useEffect(() => {
        getData();
    }, []);
    ```

7. useState와 useEffect를 사용을 위한 import

    ```
    import React, { useEffect, useState } from "react";
    ```