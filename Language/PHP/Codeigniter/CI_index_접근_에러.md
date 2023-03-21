1. PHP7.3 + Nginx1.22.1 사용 시 Nginx가 index.php를 인식하지 못해 404 에러 발생

2. index.php 인식을 위해 nginx.conf에 try_files를 추가

    ```
    try_files $uri $uri/ /index.php?/$request_uri;
    ```

3. try_files 추가 시 Nginx가 index.php를 거치지 않고 router의 default_controller에 직접 접근하여 403 에러 발생

4. try_files를 수정

    ```
    try_files $uri $uri/ /index.php?/$request_uri;

    =>

    try_files $uri /index.php?/$request_uri;
    ```
