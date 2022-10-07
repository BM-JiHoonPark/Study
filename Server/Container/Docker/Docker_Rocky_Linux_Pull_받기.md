1. docker에서 rocky linux image를 latest 버전으로 pull 받을 시 not found error 발생

2. docker - rocky linux 공식 문서 상 latest 태그를 의도적으로 누락

    https://hub.docker.com/_/rockylinux

3. rocky linux 설치 시 버전 태그를 추가하여 pull 받는다.

    ```
    docker pull rockylinux:8
    ```