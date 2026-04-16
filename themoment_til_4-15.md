# 4월 15일 과제

## IoC(Inversion of Control)
개발자가 제어하던 객체의 생성, 삭제등의 관리를 프레임워크가 대신 수행하는 것

### DI(Dependency Injection)
IoC의 일종으로, 객체가 필요로하는 의존성(다른 외부 객체같은거)을 외부에서 주입하는 것
`@Autowired` 같은거임.
new 키워드를 줄이고, 결합도를 낮춤.

## AOP(Aspect-Oriented Programming)
핵심 비즈니스 로직(실질적 로직. 자료구조나 알고리즘 이런것 보단 실제로 행하는 행위.. 느낌?)과 공통 기능(로깅, DB접근 등)을 분리하여 모듈화하는 것.
코드의 중복이 줄어들고 비즈니스 로직에 집중할 수 있게 됨.


## PSA(Portable Service Abstraction)
환경 변화와 관계없이 일관된 기술 접근 방식을 제공하는 추상화 계층.
DB가 SQLite에서 MySQL로 바뀐다거나 운영체제가 윈도우에서 리눅스가 된다거나 하는 환경 변화로 부터 독립되게 하는 것
JDBC, JPA 같은 것들이 예시임.


## SOLID
유지보수와 확장을 더 용이하게 하기 위한 원칙

### S: **S**ingle **R**esponsibility **P**rinciple(단일 책임 원칙)
클래스는 하나의 책임(기능)만을 가진다.

### O: **O**pen-**C**losed **P**rinciple(개방-폐쇄 원칙)
확장(기능 추가)에는 열려있어야 하고, 변경(기존 코드 변경)에는 닫혀있어야 한다.
(레거시 지원을 고려한건가..?)

### L: **L**iskov **S**ubstitution **P**rinciple(리스코프 치환 원칙)
자식 클래스는 부모 클래스의 책임을 준수하며, 부모 객체를 자식 객체로 대체해도 프로그램이 문제없이 작동해야 한다.

### I: **I**nterface **S**egregation **P**rinciple(인터페이스 분리 원칙)
클라이언트가 사용하지 않는 메서드에 의존하지 않도록, 인터페이스를 구체적으로 분리해야 한다.

### D: **D**ependency **I**nversion **P**rinciple(의존성 역전 원칙)
구체적인 클래스가 아닌 추상화된 클래스(Java의 경우 Interface인듯?)에 의존해야 한다.

## Annotation
클래스, 메서드, 필드 위에 `@`기호를 붙여 특별한 의미를 부여하는 기술
코드에 정보를 추가하는 방법이다.(예: @ResponseBody의 경우 "이 코드는 Json을 받습니다."라는 정보를 추가)