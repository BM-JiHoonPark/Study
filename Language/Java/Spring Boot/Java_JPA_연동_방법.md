1. Maven OR Gradle을 이용하여 JPA 하이버네이트와 DB dependency를 추가한다.

    ```
    <!-- JPA 하이버네이트 --> 
    <dependency> 
        <groupId>org.hibernate</groupId> 
        <artifactId>hibernate-entitymanager</artifactId> 
        <version>5.3.10.Final</version> 
    </dependency> 
    <!-- H2 데이터베이스 --> 
    <dependency> 
        <groupId>com.h2database</groupId> 
        <artifactId>h2</artifactId> 
        <version>1.4.199</version> 
    </dependency> 
    ```

2. resources/META-INF 폴더 내부에 persistence.xml 설정 파일을 생성 및 작성한다.

    ```
    <?xml version="1.0" encoding="UTF-8"?> 
    <persistence version="2.2" 
                xmlns="http://xmlns.jcp.org/xml/ns/persistence" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
                xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/persistence http://xmlns.jcp.org/xml/ns/persistence/persistence_2_2.xsd"> 
        <persistence-unit name="hello"> 
            <properties> 
                <!-- 필수 속성 --> 
                <property name="javax.persistence.jdbc.driver" value="org.h2.Driver"/> 
                <property name="javax.persistence.jdbc.user" value="sa"/> 
                <property name="javax.persistence.jdbc.password" value=""/> 
                <property name="javax.persistence.jdbc.url" value="jdbc:h2:tcp://localhost/~/test"/> 
                <property name="hibernate.dialect" value="org.hibernate.dialect.H2Dialect"/> 

                <!-- 옵션 --> 
                <property name="hibernate.show_sql" value="true"/> 
                <property name="hibernate.format_sql" value="true"/> 
                <property name="hibernate.use_sql_comments" value="true"/> 
                <!--<property name="hibernate.hbm2ddl.auto" value="create" />--> 
            </properties> 
        </persistence-unit> 
    </persistence> 
    ```

3. EntityManager를 이용하여 JPA에 연동한다.

    ```
    EntityManagerFactory emf = Persistence.createEntityManagerFactory("hello");
    // 여기서 createEntityManagerFactory에 전달 될 변수는 persistenceUnitName으로
    // persistence.xml 작성 시 등록한 persistence-unit name을 입력한다.

    EntityManager em = emf.createEntityManager();

    // CODE

    em.close();

    emf.close();
    ```