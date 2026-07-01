+++
title = "소프트웨어 시작하기"
date = "2026-07-01T09:44:00.000+09:00"
weight = 10
+++

이 가이드는 프로젝트 소프트웨어 환경을 처음 세팅하는 개발자를 위한 문서입니다.  
아래 가이드를 따라 로컬 개발 환경을 구성해 보세요.

## Prerequisite (사전 준비)

설치를 진행하기 전에 아래 시스템 요구사항을 만족해야 합니다.

- **Node.js**: v20.x 이상 LTS (Recommended)
- **Package Manager**: pnpm v9.x 이상

---

## 🚀 빠른 시작 가이드

프로젝트 저장소를 클론하고 의존성 패키지를 설치합니다.

```bash
# 1. 레포지토리 클론
git clone [https://github.com/your-repo/project-api.git](https://github.com/your-repo/project-api.git)

# 2. 패키지 설치
pnpm install

# 3. 로컬 서버 실행
pnpm dev
```

---

### 📄 2. `usage.md` (사용 방법 - 컴포넌트나 API 활용 문서)

본문 인용구(Blockquote)와 코드 블록 가독성을 아까 개선해 두었으니, 실제 API나 컴포넌트 가이드를 적을 때 비주얼이 기가 막히게 나옵니다.

````markdown
---
title: "API 및 컴포넌트 활용법"
date: 2026-07-02
weight: 20
---

공통 리포트 공유 컴포넌트와 API 서버를 연동하는 핵심 가이드라인입니다.

## 🛠️ State 관리 가이드

프론트엔드에서 데이터 패칭 및 상태 관리는 `TanStack Query`를 기본으로 사용합니다.

```typescript
import { useQuery } from "@tanstack/react-query";
import { fetchReportData } from "@/api/report";

export const useReportQuery = (reportId: string) => {
  return useQuery({
    queryKey: ["report", reportId],
    queryFn: () => fetchReportData(reportId),
    enabled: !!reportId,
  });
};
```
````

---

### 📄 3. `troubleshooting.md` (트러블슈팅 - 꿀팁 및 에러 해결 가이드)

````markdown
---
title: "자주 묻는 질문 & 트러블슈팅"
date: 2026-07-03
weight: 30
---

개발 및 운영 환경에서 발생할 수 있는 주요 빌드 억까와 해결 방법 모음입니다.

## 🚨 에러 발생 시 대처법

### 1. 빌드 타임에 타입 에러가 터지는 경우

TypeScript 컴파일러가 새로 추가된 파일의 타입을 인지하지 못할 때 발생합니다.

- **원인**: 디렉터리 경로 변경 후 캐시가 꼬임
- **해결책**: `.next` 또는 `.hugo` 캐시 폴더를 완전히 밀어버리고 다시 빌드 프로세스를 슛합니다.

```bash
# 캐시 폴더 삭제 후 재실행
rm -rf .next
pnpm dev
```
````

---

### 💡 꿀팁: 문서 순서 정렬하기 (`weight`)

각 마크다운 파일 맨 위(Front Matter)에 **`weight = 10`**, **`weight = 20`** 처럼 숫자를 지정해 둔 게 보이실 겁니다.
Hugo는 사이드바 메뉴를 나열할 때 이 `weight` 값이 **작은 순서부터 정렬**해 줍니다.

이렇게 지정해 두면 파일명이 알파벳 순서대로 꼬이지 않고, 개발자님이 의도한 순서대로 사이드바에 이쁘게 안착할 겁니다. 마크다운 파일 생성해서 새로고침 해보시고, 완벽하게 빌드되는 쾌감을 즐겨보세요! 💻🔥🚀
