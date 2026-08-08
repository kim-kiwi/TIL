# EveryGSM 코드베이스 분석

main 브랜치 기준

## Server-v2

Spring Boot를 이용해 개발중이다

slf4j를 이용해 로깅하는듯

```
.
|
+-+src/ --> 실제 서비스 코드
| |
| +--...
|
+-+scripts/ --> 서버 시작, 종료, 헬스 체크 스크립트. bash로 작성
| |
| +--...
|
+-+deploy/ --> docker 배포 코드, compose 설정, mysql 설정
| |
| +--...
|
+--cloud-diagram.py --> 내부->외부, 외부->내부 트래픽 흐름, CI/CD 배포 흐름을 시각화 해주는 도구인 것 같다
```

이제 서비스 코드쪽을 자세히 봐보자

```
src/
|
+-+domain/ --> 실제 요청을 처리하는 부분들이 있는 곳인 것 같다
| |
| +-+(domain 이름)/ --> 자주 보던 controller, dto, service 구조
|   |
|   +--controller/
|   +--service/
|   +-+dto/ --> 이름에도 ResDto, ReqDto를 붙여 응답, 요청 Dto를 구분하지만, 폴더 구조로도 구분해놓은 것 같다
|     |
|     +--request/
|     +--response/
+-+global/ --> 여러 domain들이 공유하는 모듈이나 기능들을 모아둔 것 같다
  |
  +-+(이름)/ --> 대부분 이 형식으로 되어있다. common, thirdparty 같이 예외도 있는 걸 보면 특별한 형식이 정해진건 아닌듯
    |
    +--*.java

global에는 로깅 모듈, config, 예외, 공유모듈, Spring Security Filter, 서드파티 api dto 등이 있다.
domain에는 실제 서비스를 구성하는 코드들이 있다.
admin, auth, image, project, user 정도로 나뉘어 있다.

admin domain에서 approve project와 reject project를 두 서비스로 나눴는데, 합쳐도 되지 않을까... 싶다
approve는 업데이트, reject는 삭제를 수행하기 때문에 나눠놓은건가
```

## Client-v2

nextjs를 이용해 개발중이다

husky라는걸로 git hook 관리를 한다는데.. 아직 잘 모르겠다

```
.
|
+--.husky/ --> husky 설정파일들
|
+-+docs/ --> 말그대로 문서 모음
| |
| +--CodeConvention.md --> 코드 컨벤션을 정리해놓았다.
|
+--src/ --> 실제 서비스 구현
|
+-+public/ --> static 파일들인듯
  |
  +--fonts/
  +--images/
```

여기도 src를 한 번 살펴보자

```
src/
|
+--app/ --> 프레임워크 자체에서 이쪽을 라우트로 해석해준다. 여기가 서비스 표면이라는 뜻. api 구조만 있고 페이지 구성같은 나머지는 다른 곳에 분리되어있다
+--views/ --> 여기에 실제 페이지 컴포넌트들이 모여있는 듯 하다. 어쩐지 app쪽이 간결하더라니
+--shared/ --> 여러 페이지에서 쓰는 컴포넌트, 타입, api url, 라이브러리, 상수 등등이 모여있다
+--features/ --> 특정 기능을 담당하는 컴포넌트가 있는듯
+--entities/ --> api 쿼리를 담당하는 부분인듯
+--widgets/ --> 자주쓰는 컴포넌트들이 있는듯 하다
+--proxy.ts --> Spring Security의 Filter같은 역할을 수행중인 듯 하다. 쿠키에서 토큰 읽어서 비로그인 상태면 퍼블릭 라우트만 이용 가능

model/
ui/
이 두 디렉토리로 나눠서 구조화를 한듯 하다
model은 백엔드에서 받아올 데이터의 구조를 뜻한다고 한다
기능별로 model과 ui를 나눠둔듯 하다

entities -> features -> views
widgets -> views
views -> app

이런 구조가 아닐까 추측중
```
