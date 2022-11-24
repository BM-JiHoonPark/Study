1. form-input HTML 코드 작성

    Form.js

    ```
    <form id="formData">
      <input type="text" name="dataA" defaultValue="dataA"/>
      <input type="text" name="dataB" defaultValue="dataB"/>
    </form>
    <button onClick={pushData}>전송</button>
    ```

2. 비동기 통신을 위한 컴포넌트 및 함수 생성

    Api.js

    ```
    export async function pushApi(request) {
        try {
            return await fetch(URL,{
                method: "POST",
                body: request
            })
            .then(function (response) { 
                return response;
            })
            .catch((error) => console.log("error:", error));
        } catch (error) {
            console.log(error);
        }
    }
    ```

3. 비동기 통신 컴포넌트를 이용하여 비동기 통신

    Form.js

    ```
    const pushData = () => {
        const form = document.getElementById("formData");
        const formData = new FormData(form);
        api.pushApi(formData).then(function(data) {
          console.log(data);
        });
    }
    ```