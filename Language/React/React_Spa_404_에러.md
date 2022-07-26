1. React 나 Vue 등 SPA 환경에서는 루트 경로에만 index.html 파일이 존재함

2. 루트 경로가 아닌 페이지에서 새로고침을 할 경우 해당 경로에 index.html 파일이 존재하지 않으므로 404 에러가 발생

3. nginx conf 파일의 location 부분에 try_files를 추가해준다.

    conf file

    ```
    location / {
        index  index.html index.htm;
        try_files $uri $uri/ /index.html;
    }
    ```