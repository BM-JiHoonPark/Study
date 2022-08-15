1. Spring Boot에서 콘솔창에 로그를 찍을 때 slf4j를 사용

2. slf4j import

    ```
    import org.slf4j.Logger;
    import org.slf4j.LoggerFactory;
    ```

3. Class에서 공통으로 사용하기 위해 필드에서 선언

    ```
    private static final Logger logger = LoggerFactory.getLogger(Controller.class);
    ```

4. Logger 문법

    ```
    logger.trace(String);
    logger.debug(String);
    logger.info(String);
    logger.warn(String);
    logger.error(String);
    ```