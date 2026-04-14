# Spring

## Spring MVC 패턴
M: Model
 - View에서 렌더링할 정보를 담은 컨테이너.
V: View
 - Model을 사용하여 클라이언트에 보여줄 화면 렌더.
C: Controller
 - 비즈니스 로직 호출 후 결과를 Model에 담아 View를 선택하여 DispatcherServlet에 반환.

DispatcherServlet: 모든 클라이언트 요청을 받아 적절한 컨트롤러에 넘겨주고 결과를 View에 전달하는 핵심 컨트롤러.

## Spring 게시판에 쓰인 기술
 - JPA
   - DB 조작을 SQL구문 없이 함수로 할 수 있게 해줌.
 - Thymeleaf
   - View 역할. 서버 사이드 렌더링 함.
 - MySQL
   - 관계형 DB. 동시성 처리에 강하다.

## Spring에 쓰인 개념
 - Entity
   - DB의 Record를 표현한 java 객체.
 - Controller
   - 서버로 온 요청을 처리하는 역할.
 - Service
   - 비즈니스 로직(대충 내부 로직과 비슷한 말인듯)을 처리하는 역할.
 - Repository
   - DB 접근용 인터페이스.
 - DTO
   - Data Transfer Object. 통신용 데이터 객체. DB구조를 외부에 노출하지 않기 위함. 
