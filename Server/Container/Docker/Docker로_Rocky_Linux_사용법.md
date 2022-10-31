1. Docker 설치 확인

    ```
    systemctl status docker
    ```
    
2. Docker 설치 및 실행

    ```
    yum install docker
    systemctl start docker
    ```

3. Rocky Linux Pull

    ```
    docker pull rockylinux:8

    Rocky Linux의 latest 버전은 도커에서 지원하지 않기 때문에 버전을 명시해준다.
    Rocky Linux 9버전의 경우 일부 서버에서 기동되지 않는 문제가 있어 8버전으로 설치함
    ```

4. Container 실행 및 접속

    ```
    docker run -i -t rockylinux:8 /bin/bash
    ```

5. 공식문서

    ```
    https://hub.docker.com/_/rockylinux
    ```