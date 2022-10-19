1. JPA에서 생성 및 수정을 위해 Transaction을 이용한다.

2. JPA에서 생성 시 EntityManager의 persist 메소드를 이용한다.

    ```
    EntityManagerFactory emf = Persistence.createEntityManagerFactory("hello");
    EntityManager em = emf.createEntityManager();

    EntityTransaction tx = em.getTransaction();
    tx.begin();

    try {
        EntityClass ec = new EntityClass();
        ec.setColumnA(1);
        ec.setColumnB("Hello");

        em.persist(ec);

        tx.commit();
    } catch (Exception e) {
        tx.rollback();
    } finally {
        em.close();
    }

    emf.close();
    ```

3. JPA에서 수정 시 Entity를 이용해 데이터를 매핑한 후 Setter 함수만으로 수정이 가능하다.

    ```
    EntityManagerFactory emf = Persistence.createEntityManagerFactory("hello");
    EntityManager em = emf.createEntityManager();

    EntityTransaction tx = em.getTransaction();
    tx.begin();

    try {
        EntityClass findEc = em.find(EntityClass.class, 1);
        findEc.setColumnB("HelloJPA");

        tx.commit();
    } catch (Exception e) {
        tx.rollback();
    } finally {
        em.close();
    }

    emf.close();
    ```