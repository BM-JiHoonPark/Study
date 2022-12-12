1. NVM(Node Version Manager) 설치

    ```
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.2/install.sh | bash
    ```

2. NVM 설치 후 실행이 되지 않을 경우 수동으로 환경설정

    ```
    # ~/.bash_profile, ~/.zshrc, ~/.profile 또는 ~/.bashrc 파일에 아래 내용을 복사 후 저장

    vi ~/.bashrc

    export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
    [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm

    source ~/.bashrc
    ```

3. NVM을 이용하여 Node 설치

    ```
    nvm install [버전]

    # ubuntu 18.xx 버전 등 몇몇 OS에서 node 18버전을 지원하지 않으므로 18버전 이외의 버전을 사용
    ```


6. 참고자료 : NVM Github

    ```
    https://github.com/nvm-sh/nvm/blob/master/README.md
    ```