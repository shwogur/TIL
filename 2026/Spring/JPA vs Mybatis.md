웹 애플리케이션을 위한 백엔드로 가장 많이 사용되는 프레임워크로는 **Java 기반의 Spring 또는 Springboot**를 사용한다. `Spring은 대규모 기업환경에서 안정성과 신뢰성이 검증된 프레임워크`이기 때문이며, 많은 기업에서 스프링을 사용하여 안정적인 서비스를 운영하고 있다.

이때, 백엔드에서 데이터를 저장하고 조회하려면 데이터베이스를 활용해야 하는데, 백엔드에서 데이터베이스를 사용하는 `프레임워크로 가장 많이 쓰이는 기술이 ‘Mybatis’와 ‘JPA’`이다. 

데이터 베이스 접속을 편하게 사용하기 위해 **SQL Mapper** 기술과, **ORM(Object Relational Mapping)** 기술을 제공한다. 둘 다 DB와의 연동, 저장을 위한 기술이며, SQL Mapper는 **‘개발자가 작성한 SQL 실행 결과를 객체에 매핑’**시켜주는 프레임워크이며, ORM은 객체와 DB의 데이터를 **‘자동으로 매핑’**시켜주는 프레임워크를 말한다.

**SQL Mapper** 기술을 제공하는 것이 `‘MyBatis’`이며, **ORM** 기술을 제공하는 것이 `‘JPA(Java Persistence Api)’`이다. 두 가지 기술은 모두 데이터를 관계형 데이터베이스에 저장, 즉 영속화(Persistence) 시킨다는 측면에서는 동일하지만, 서로 다른 접근 방식을 채택하고 있다.

## MyBatis란?
`MyBatis 프레임워크`는 반복적인 **JDBC 프로그래밍을 단순화하여, 불필요한 Boilerplate 코드를 제거하고, Java 소스코드에서 SQL 문을 분리하여 별도의 XML 파일로 저장하고, 이 둘을 서로 연결시켜주는 기능**을 제공한다.

## MyBatis의 특징

### Java 코드와 SQL 매핑
MyBatis를 사용하면, MyBatis 내부에서 그러한 Boilerplate 코드가 구현되어 있고, MyBatis에서 Java 메소드와 SQL 간에 매핑을 시켜서 `개발자는 Java 메소드 선언과 SQL 문만 만들면 MyBatis가 자동으로 그 둘 간을 연결시켜 주게 된다.`

SQL 문장이 Java 코드 내에 들어가 있어서 수정하기도 힘들고, 보기도 힘들었는데, **SQL 문을 별도로 Java 코드에서 분리해두어서 관리가 편하게 하였으며**, **분리된 SQL 문을 MyBatis가 찾아서 실행해 주는 기능**을 한다.

### 동적 SQL 생성 기능
`MyBatis 프레임워크`는 반복적인 JDBC 프로그래밍을 단순화하여, **불필요한 Boilerplate 코드를 제거**하고, **Java 소스코드에서 SQL 문을 분리하여 별도의 XML 파일로 저장**하고, 이 둘을 **서로 연결시켜주는 기능**을 제공해준다.

동적으로 SQL 문이 생성된다는 의미는 **검색 조건같이 사용자가 입력하는 값에 따라 서로 다른 SQL 문장이 생성되어 실행된다는 의미**이다. 예를 들어, 게시판 테이블을 검색할 때, 사용자가 작성자만 입력하여 검색하면 작성자가 WHERE 절에 있는 다음의 SQL이 생성되고,

- `SELECT * FROM BOARD WHERE AUTHOR = ‘파라미터’`

제목을 입력하여 검색하면 다음과 같이 제목을 검색하는 SQL이 만들어진다는 의미이다.

- `SELECT * FROM BOARD WHERE TITLE LIKE ‘%파라미터%’`

MyBatis 내에 if 문, choose, when, otherwise, foreach 등의 문법을 지원해서 동적인 SQL 문 생성이 가능하다. 아래 예시에서는 title 파라미터를 입력받게 되면 SQL 문이 아래와 같이 생성되고,

- `SELECT * FROM BLOG WHERE state = ‘active’ AND title like #{title}`

title 파라미터 없이 호출이 되는 경우엔, 아래와 같이 title 조건이 없는 SQL 문이 생성된다.

- `SELECT * FROM BLOG WHERE state = ‘active’`

JPA는 이보다 한발 더 나아가서 `SQL 문까지 자동으로 생성해 주고, DB 데이터와 Java 객체를 매핑 시켜주는 기술`이다. SQL 문장 작성이 필요 없으니 MyBatis보다 한 단계 더 자동화되어 더 편리함과 반복작업을 없애준다.

## JPA(Java Persistence API)란?
`JPA(Java Persistence API)`는 **Java 객체와 관계형 데이터베이스 간의 매핑을 위한 API다.** JPA는 ORM(Object-Relational Mapping)을 구현하는 자바 표준 스펙으로, 개발자가 객체지향 프로그래밍 언어에서 사용하는 객체 모델과 관계형 데이터베이스의 테이블 간의 매핑을 자동으로 처리해 준다.

## JPA가 생겨난 이유
그런데, MyBatis와 같이 SQL 문과 Java 코드를 연계하는 접근 방식이 아니라 `Java 객체와 DB 엔티티(테이블)` 자체를 그대로 매핑해서 처리할 수 있는 접근 방식을 채택한 새로운 기술표준이 등장했는데, 이것이 바로 **‘JPA(Java Persistence API)’**이다.

데이터베이스는 데이터 중심의 구조를 가지고 있고, Java는 객체지향적인 구조로 관리되기 때문에 둘 사이에 데이터를 직접적으로 쉽게 가져오거나 쉽게 저장하는 방법이 존재하지 않았다. 이 둘 사이를 손쉽게 변환이 된다면 개발이 용이해질 것이다.

**JPA**의 접근 방식은 이런 ORM(Object-Relational Mapping) 기술을 의미합니다. 즉, `객체와 데이터베이스 간의 매핑 기술`을 의미하며, Java 개발자가 좀 더 **객체지향 관점에서 개발할 수 있게 하고**, 개발을 용이하게 해주어서 `DB와 Java 간의 불일치를 해소`해준다.

아래 그림에서 보면 Java 객체인 Student 클래스가 ORM 매핑을 통해서 DB 테이블에 영속화(Persistence) 되고, 또다시 영속화된 데이터가 다시 Java 객체로 변환하는 과정을 나타내고 있다. ORM은 이렇게 Java객체를 DB 테이블로 자동으로 영속화 시켜주는 기술을 의미한다.
![image](/image/ORM매핑.jpg)

이러한 ORM 기술을 실제 구현해서 만들어진 프레임워크가 `Hibernate`이다. JPA 스펙을 구현한 기술은 Hibernate 외에도 EcliseLink, DataNucleus 등이 있지만, 현재 사실상 `표준(de facto standard)으로 널리 사용되는 것은 Hibernate`이다.

Java와 DB 데이터 간의 매핑을 자동화해주어서 개발자는 SQL 문을 작성할 필요가 없어지고, DB가 바뀌어도 DB에 따라 새로운 SQL을 작성할 필요가 없이 Hibernate에서 DB에 맞는 적합한 SQL 문을 생성해 준다.

## JPA 특징
MyBatis와 다르게 SQL 문의 작성이 불필요하며 ORM 내부적으로 java 메소드에 적합한 SQL 문이 자동으로 생성이 되어 실행되게 된다. Java 개발자는 클래스만 만들어서 사용하고, ORM 프레임워크가 자동으로 관련된 SQL을 만들어 준다.

즉, Java 개발자는 jpa.persist(member)라고 사용하면, Insert SQL 문이 자동으로 생성되어 DB에 저장이 된다.
![image](/image/JPA특징.jpg)

**MyBatis와 JPA 모두 DB를 사용할 때 번거로운 반복작업을 없애준다.** MyBatis는 SQL 문을 Java와 분리하여 별도 파일로 관리할 수 있어서, SQL 개발과 유지 보수에 용이하고, JPA는 SQL 문을 아예 만들 필요가 없기 때문에 더욱 자동화되고 반복작업을 더욱 줄여준다.

## Mybatis vs JPA 비교 및 장단점
전체적으로는 JPA가 MyBatis 보다 더 인기 있고, 더 많이 사용되는 기술이지만, 한국과 중국은 MyBatis가 JPA보다 더 많이 사용되고 있다.

그 이유는 **정부의 표준 프레임워크로 사용되는 전자정부 프레임워크**가 MyBatis를 사용하기 때문에 전통적으로 MyBatis가 DB 연동 기술로 많이 사용되어 왔다. 하지만, 최근에는 인터넷 서비스 기업과 스타트업 기업을 중심으로 `JPA 기술을 기반으로 서비스를 하는 기업이 늘어나고 있다.`