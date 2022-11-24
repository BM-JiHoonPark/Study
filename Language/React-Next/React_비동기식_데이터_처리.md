비동기식 데이터 처리

1. React에서는 비동기식 데이터 처리를 위해 Promise를 사용

2. Promise의 단점을 보완하기 위해 ES7에서 async와 await라는 키워드 추가

3. async 기본 문법

    ```
    async function() {

        const result = await fetch(url)

        .then(function (response) { return response.json() })

        .catch((error) => console.log("error:", error));

    }


    const users = async() => {

        const result = await fetch(url)

        .then(function (response) { return response.json() })

        .catch((error) => console.log("error:", error));
        
    }
    ```
