1. Fetch 기본 문법

    ```
    fetch(url, [option])
    .then(function (response) { return response.json() })
    .then(function (json) { console.log(json) })
    .catch((error) => console.log("error:", error));
    ```

2. Fetch Option 문법

    ```
    fetch(url, {
        method: "POST",
        headers: {
            'Content-type': 'application/json'
        },
        body: JSON.stringify({
            dataA: "dataA",
            dataB: "dataB"
        })
    })

    # GET 방식일 경우 Option을 생략 할 수 있다.
    ```
    
3. Json 형식으로 DATA 전송 시 cros error 발생

4. URL 형식으로 DATA 전송 시 문법

    ```
    fetch(url, {
        method: "POST",
        headers: {
            'Content-type': 'application/x-www-form-urlencoded'
        },
        body: "dataA=dataA&dataB=dataB"
    })
    ```

5. FormData를 사용하여 DATA 전송 시 문법

    ```
    fetch(url, {
        method: "POST",
        body: FormData
    })
    ```