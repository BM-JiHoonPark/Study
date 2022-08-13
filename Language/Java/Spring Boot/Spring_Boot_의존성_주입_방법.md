1. Spring 에서 의존성 주입 방법은 필드, 수정자, 생성자 주입으로 나누어진다.

2. 필드 주입 방법

    ```
    public class Controller {

        @Autowired
        private Service service;

        ...
    ```

3. 수정자 주입 방법

    ```
    public class Controller {

        private Service service;

        @Autowired
        public void setService(Service service) {
            this.service = service;
        }
    ```

4. 생성자 주입 방법

    ```
    public class Controller {

        private final Service service;

        private Controller(final Service service) {
            this.service = service;
        }
    ```