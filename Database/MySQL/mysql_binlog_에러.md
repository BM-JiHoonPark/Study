## MySQL "My disk is full of binlog files" 에러

### 에러 내용

/var/lib/mysql 디렉토리의 binlog 파일의 용량 초과로 발생


### 조치 사항

binlog 파일 삭제 (binlog.index 포함)

binlog 파일을 모두 삭제하면 MySQL이 새로운 binlog 파일을 생성

binlog.index 파일까지 제거해야 새로운 binlog를 생성하므로 binlog.index 파일도 같이 삭제