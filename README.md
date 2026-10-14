# wooyeonhan-siktak-hackathon

2026 우연한 식탁 MVP 개발 해커톤 레포지토리

## 기술 스택

- React + TypeScript + Vite
- TanStack Query: 서버 상태 관리
- Zod: 런타임 데이터 검증
- TanStack Devtools + Query 패널: 개발 환경에서 쿼리 상태 확인
- ESLint + Prettier: 코드 검사와 포맷 통일

## 시작하기

Node.js 20.19+ (20.x), 22.13+ (22.x) 또는 24+가 필요합니다. `.nvmrc`는 초기 설정을 검증한 22.17.0을 지정합니다.

```sh
nvm use
npm ci
npm run dev
```

## 명령어

| 명령어                 | 설명                                       |
| ---------------------- | ------------------------------------------ |
| `npm run dev`          | 개발 서버 실행                             |
| `npm run build`        | TypeScript 검사 후 프로덕션 빌드 (`dist/`) |
| `npm run preview`      | 빌드 결과 미리보기                         |
| `npm run typecheck`    | TypeScript 검사                            |
| `npm run lint`         | ESLint 검사                                |
| `npm run lint:fix`     | ESLint 자동 수정                           |
| `npm run format`       | Prettier 포맷 적용                         |
| `npm run format:check` | Prettier 포맷 검사                         |
| `npm run check`        | ESLint, Prettier, 프로덕션 빌드 일괄 검증  |

## 기본 구조

```text
src/
  lib/query-client.ts          # 공통 QueryClient
  providers/app-providers.tsx  # Query Provider와 개발용 Devtools
  App.tsx                     # 시작 화면
  main.tsx                    # 앱 진입점
  index.css                   # 전역 스타일
```

`AppProviders`가 앱 전체를 감싸므로 하위 컴포넌트에서 `useQuery`, `useMutation`을 바로 사용할 수 있습니다. 개발 화면의 TanStack Devtools 버튼을 열면 Query 패널이 표시됩니다. Devtools는 프로덕션 빌드에서 제외됩니다.

API 응답 검증이 필요할 때 Zod 스키마를 정의하고 Query 함수에서 `schema.parse(data)`로 검증할 수 있습니다.

- [TanStack Devtools 공식 설정 가이드](https://tanstack.com/devtools/latest/docs/quick-start)
- [Prettier와 ESLint 연동 가이드](https://prettier.io/docs/integrating-with-linters)
