1. AWS 인스턴스 생성 시 키페어를 생성하면 pem 파일이 생성된다.

2. PuTTY를 이용하여 인스턴스에 SSH로 접속 시 ppk 키파일이 필요하다.

3. PuTTY 공식 홈페이지에 접속해서 latest 버전의 PuTTY 패키지를 다운로드 받는다.

```
https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html
```

4. PuTTYgen을 사용하여 프라이빗 키를 변환한다.

4-1. 키페어 생성 시 다운로드받은 pem 파일을 Load한다.

4-2. Save private Key 버튼을 선택해 ppk 파일을 다운로드받는다.

5. PuTTY를 열고 Category - Connection - SSH - Auth 탭에서 Private key file을 선택 후 실행한다.

6. 참고자료 : AWS 공식문서

    ```
    https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/putty.html
    ```