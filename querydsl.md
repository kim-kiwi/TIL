# QueryDSL

자바 코드로 쿼리를 작성할 수 있게 해주는 라이브러리

엔티티 클래스를 바탕으로 Q클래스라는 걸 만듦. 이걸 기반으로 타입 검사 해줌

코드라서 컴파일타임에 타입검사 가능

JPQL은 문자열 기반이라서 문법 오류나 이런걸 잡기 어려워서 QueryDSL을 씀

JPQL보다 가독성도 향상됨

# JPQL

데이터베이스 테이블이 아니라 엔티티 객체를 대상으로 쿼리를 작성하는 객체지향 쿼리 언어

JPQL -> JPA -> SQL순으로 변환되어 결국엔 SQL이 됨

추상화를 통해 사용중인 데이터베이스가 달라져도 동일한 문법을 사용 가능함

```java
// JPQL
String qlString = "select m from Member m where m.name = :name";
Member result = em.createQuery(qlString, Member.class)
                  .setParameter("name", "kim")
                  .getSingleResult();
```

```java
// QueryDSL
QMember member = QMember.member;
Member result = queryFactory
                  .selectFrom(member)
                  .where(member.name.eq("kim"))
                  .fetchOne();
```
