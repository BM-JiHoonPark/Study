1. React bulid 시 SourceMap 또한 같이 빌드되기 때문에 Chrom 개발 도구 등에서 소스 확인 가능

2. 보안을 위해 React 로컬에 .env 파일을 생성하여 SourceMap 숨김처리

    .env

    ```
    GENERATE_SOURCEMAP=false
    ```