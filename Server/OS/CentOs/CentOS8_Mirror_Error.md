1. CentOS8 EOS로 인해 Mirror site가 vault로 전환되어 Mirror site를 찾지 못해 에러 발생

    ```
    Failed to download metadata for repo 'appstream'
    ```

2. 기존 Mirror site를 vault로 전환

    ```
    sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-Linux-*
    sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-Linux-*
    ```
    

CentOS8 버전은 2021년을 마지막으로 지원이 종료되었기 때문에 위의 임시 방편으로 에러 해결은 가능하지만 보안상 굉장히 취약하므로 가급적 CentOS Stream이나 rocky linux 등의 지원중인 OS로 변경하도록한다.