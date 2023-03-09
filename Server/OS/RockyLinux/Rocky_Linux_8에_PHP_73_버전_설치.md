1. Docker로 pull 받은 Rocky Linux8 버전에는 dnf PHP module이 7.2 버전으로 설정되어있다.

2. dnf의 PHP module을 초기화 한다.

  ```
  dnf module reset php
  ```

3. dnf의 PHP module을 7.3 버전으로 설정한다.

  ```
  dnf module enable php:7.3
  ```

4. dnf로 PHP를 설치한다.

  ```
  dnf install php
  ```
