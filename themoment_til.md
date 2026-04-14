# 전공별 역할
 - 프론트엔드: 사용자가 직접 보는 화면을 만드는 역할(예: 로그인 ID, PW 입력창)
 - 백엔드: 보이지 않는 곳을 만드는 역할(예: ID와 PW를 받아서 유저를 로그인 시키는 서버)
 - 클라우드: 서버를 인터넷 상에서 운영하고 관리하는 역할(예: AWS를 이용하여 서버 배포)
 - 디자인: UI와 UX(유저 경험)을 사용자에 맞춰 설계

# HTTP
**H**yper**T**ext **T**ransfer **P**rotocol

Hypertext를 주고받기 위한 통신 규약(약속)

## 특징 
 - 클라이언트가 요청하면, 서버가 
 응답하는 방식
 - Stateless. 클라이언트의 이전 상태를 저장하지 않음. 로그인 상태를 유지할 수 있는 건 Session과 Cookie를 이용했기 때문.

## Stateless
클라이언트의 이전 상태를 저장하지 않는다.
네이버 같은 곳에서 로그인 정보가 유지되는 건 매번 클라이언트가 Session과 Cookie를 서버에 전달하기 때문이다.

## 클라이언트-서버 구조
클라이언트가 요청을 보내면 서버가 응답하는 방식.
UI/UX등은 클라이언트에서, 비즈니스 로직등은 서버에서 분리하여 관리 가능하다.

## Methods
 - GET: 리소스 접근
 - POST: 데이터 보내기
 - PUT: 리소스 교체
 - DELETE: 리소스 삭제

## Status Codes
 - 1XX: 정보제공
 - 2XX: 성공
   - 201: 자원 생성됨
 - 3XX: Redirect 
 - 4XX: 클라이언트 에러
   - 400: 잘못된 요청
   - 401: 미인증
   - 403: Forbidden
   - 404: Not Found
 - 5XX: 서버 에러
   - 500: 내부 서버 에러

## 구조
### Header
 - Method
 - Host: 요청 대상 서버
 - User-Agent: 브라우저 / 클라이언트 정보
 - Content-Type: 보낼 형식
 - Content-Length: Body 크기
 - Accept: 받을 형식
 - Authorization: 인증 정보
### Body
 - 요청 데이터가 들어간다