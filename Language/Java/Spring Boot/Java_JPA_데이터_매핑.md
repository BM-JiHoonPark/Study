1. JPA에서 DTO 객체는 Entity로 대체된다.

    ```
    @Entity // Entity 어노테이션을 사용해야 JPA 로딩 시 인식한다.
    public class ClassName {

        @Id // JPA에게 PK 값을 알려주기 위한 어노테이션
        private int columnA;
        private String columnB;

        public int getColumnA() {
            return columnA;
        }

        public void setColumnA(int columnA) {
            this.columnA = columnA;
        }

        public String getColumnB() {
            return columnB;
        }

        public void setColumnB(String columnB) {
            this.columnA = columnA;
        }
    }
    ```