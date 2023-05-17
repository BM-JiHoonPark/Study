1. systemd는 rockylinux 기본 컨테이너에 포함되지만 기본적으로 활성화되어 있지는 않다.

2. rockylinux image 확인

    ```
    docker images

    # rockylinux image가 없다면 먼저 image를 pull 받는다.

    docker pull rockylinux:8
    ```

3. systemd 활성화용 dockerfile 생성

    ```
    vi Dockerfile

    FROM rockylinux:8
    ENV container docker
    RUN (cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == \
    systemd-tmpfiles-setup.service ] || rm -f $i; done); \
    rm -f /lib/systemd/system/multi-user.target.wants/*;\
    rm -f /etc/systemd/system/*.wants/*;\
    rm -f /lib/systemd/system/local-fs.target.wants/*; \
    rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
    rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
    rm -f /lib/systemd/system/basic.target.wants/*;\
    rm -f /lib/systemd/system/anaconda.target.wants/*;
    VOLUME [ "/sys/fs/cgroup" ]
    CMD ["/usr/sbin/init"]
    ```

4. 생성한 dockerfile 빌드

    ```
    docker build --rm -t local/r8-systemd .
    ```

5. local/r8-systemd image가 빌드 되었는지 확인

    ```
    docker images

    local/r8-systemd    latest   IMAGE ID   CREATED   SIZE
    ```

6. 컨테이너 실행

    ```
    docker run -ti --privileged -v /sys/fs/cgroup:/sys/fs/cgroup:ro -p 80:80 local/r8-systemd
    
    Failed to allocate manager object: Read-only file system 에러 발생 시
    docker run -ti --privileged -v /sys/fs/cgroup:/sys/fs/cgroup:rw --cgroupns=host -p 80:80 local/r8-systemd
    ```

7. 컨테이너 접속

    ```
    docker exec -it IMAGE ID /bin/bash
    ```

8. dnf update 시 systemd가 비활성화되니 주의

9. 공식문서
    ```
    https://hub.docker.com/r/rockylinux/rockylinux
    ```
