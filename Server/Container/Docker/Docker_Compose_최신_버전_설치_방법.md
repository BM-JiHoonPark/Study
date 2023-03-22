Docker Compose 최신 버전 설치 방법

1. Docker 설치

    ```
    yum install docker
    ```

2. Docker Compose 공식 Github에서 릴리즈 버전 확인 후 curl로 bin 파일 설치

    ```
    https://github.com/docker/compose/releases

    curl -L "https://github.com/docker/compose/releases/download/2.16.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
    ```

3. 참고 자료 - Docker Compose 공식 Github

    ```
    https://github.com/docker/compose
    ```