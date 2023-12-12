# 미션 - 출석 체크 기록 API 구현
## 🔍 진행 방식

- 미션은 **기능 요구 사항, 프로그래밍 요구 사항, 과제 진행 요구 사항** 세 가지로 구성되어 있다.
- 세 개의 요구 사항을 만족하기 위해 노력한다. 특히 기능을 구현하기 전에 기능 목록을 만들고, 기능 단위로 커밋 하는 방식으로 진행한다.
- 기능 요구 사항에 기재되지 않은 내용은 스스로 판단하여 구현한다.

## 📮 미션 제출 방법

- 미션 구현을 완료한 후 GitHub PR 요청을 통해 제출합니다.

### 테스트 실행 가이드

- 터미널에서 `npm run test` 명령을 실행하여 모든 테스트가 아래와 같이 통과하는지 확인한다.

```
Ran all test suites.
```

---

## 🚀 기능 요구 사항
출석 체크 기록 API를 구현한다.

총 2개의 API 엔드포인트로 구성한다.
- 출석 체크 기록 생성 API
- 출석 체크 기록 조회 API

각 API의 기능 요구 사항은 다음과 같다.
1. 출석 체크 기록 생성 API
   1. 출석 체크 기록을 생성한다.
   2. 출석 체크 기록은 다음과 같은 정보를 포함하고 있어야한다.
      - 출석 체크 기록을 생성한 사용자의 정보 (이름,학과,학번)
      - 출석 시간
      - 출석 일시
      - 출석 상태 (출석, 지각, 결석)
   3. 출석 체크 기록 생성 시, 출석 체크 기록을 생성한 사용자의 정보를 함께 저장한다.
   4. 비회원인 사용자도 출석 체크 기록을 생성할 수 있어야한다.
   5. 생성된 시각을 기준으로 출석 상태를 기록한다. 강의는 오전 9시부터 오후 6시까지 매 시간마다 50분의 수업시간과 10분의 쉬는 시간으로 진행되며, 
매 시간대의 강좌 시작시간 이후 `10분`안에 출석 체크 기록을 생성하면 `출석`,
`10분` 이후에 출석 체크 기록을 생성하면 `지각`, 시작시간으로부터 `20분`을 초과하면 `결석` 으로 기록한다.
   ```
   ex) 11시 00분에 시작하는 강의가 있다고 가정하자.
   
   10시 51분 ~ 11시 10분까지 출석 체크 기록을 생성하면 출석, 
   11시 11분 ~ 11시 20분까지 출석 체크 기록을 생성하면 지각, 
   11시 21분 이후에 출석 체크 기록을 생성하면 결석으로 기록한다.
   ```
2. 출석 체크 기록 조회 API 
   1. 출석 체크 기록을 조회한다.
   2. 한 유저의 최대 30일의 최신순 출석 체크 기록을 조회할 수 있어야한다.

### 공통 필수 예외처리 사항

- API에 요청받은 Body 값의 타입을 검증하여 올바르지 않은 타입일 경우 `400 BadRequest` 에러를 리턴해야한다.
- API에 요청받은 Body 값의 필수 값이 누락되거나/빈 값인 경우 `400 BadRequest` 에러를 리턴해야한다.


### API 요청/응답 요구 사항
1. 모든 API의 요청/응답은 DTO를 통해 TypeSafe하게 이루어져야한다.
2. DTO의 타입은 `class-validator`를 이용하여 검증한다.
3. DTO 내부 요소의 명칭은 `camelCase`로 작성한다.

#### 요청
#{ 요청 DTO 작성 설명 및 예시 }


#### 응답

#{ 응답 DTO 작성 설명 및 예시 }

---

## 🎯 프로그래밍 요구 사항

- **Javascript 코드가 아닌 Typescript 코드로만 구현해야 한다.**
- **Swagger**를 이용하여 API 명세를 작성한다.
- **package.json**에 명시된 라이브러리만을 이용하여 구현한다.
- **eslint**, **prettier** 등의 코드 포맷팅 라이브러리를 이용하여 제공된 코드 컨벤션에 맞추어 코드를 작성한다.
- `node`, `npm` 버전은 `package.json`에 명시된 버전을 사용한다. [Volta를 이용하여 node 버전을 관리한다.](https://docs.volta.sh/guide/getting-started)


- **(선택 사항)** API 구현이 완료되고, 유닛 테스트, E2E 테스트등 모든 테스트 코드를 작성하여 테스트를 통과하면 굿!
---

## ✏️ 과제 진행 요구 사항

- 미션은 [nest-attendance-4](https://github.com/eojjeoda-nest/nest-attendance-4) 저장소를 Fork & Clone 하고 시작한다.
- **기능을 구현하기 전 `README.md`에 구현할 기능/예외처리를 목록으로 정리**해 추가한다.