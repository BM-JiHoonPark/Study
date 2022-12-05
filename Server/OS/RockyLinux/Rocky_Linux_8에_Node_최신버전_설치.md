1. Rocky Linux 8의 기본 레포지토리에는 일정한 버전의 Node.js 버전이 존재한다. (v10.24.0)

2. dnf를 사용하여 이 버전을 사용할 수 있다.

    ```
    dnf install nodejs -y

    node -v
    v10.24.0
    ```

3. 다른 버전의 Node.js를 사용해야할 경우 NodeSource 저장소에서 스크립트를 다운로드 받는다.

    ```
    cd ~
    curl -sL https://rpm.nodesource.com/setup_18.x -o nodesource_setup.sh
    // 18.x 버전의 Node.js를 사용
    ```

4. 다운로드 받은 스크립트를 실행한다.

    ```
    bash nodesource_setup.sh
    ```

5. 이전에 설치한 Node.js 버전이 있다면 삭제한다.

    ```
    dnf remove nodejs npm -y
    ```

6. Node.js를 설치하고 버전을 확인한다.

    ```
    dnf install nodejs -y

    node -v10
    v18.11.0
    ```