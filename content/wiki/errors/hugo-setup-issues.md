---
title: "PaperMod 테마 동작 원리 및 주의사항"
date: 2026-06-14T00:00:00+09:00
tags: ["hugo", "papermod", "pattern", "troubleshooting"]
---

## 개요

Hugo의 PaperMod 테마를 사용할 때 발생하는 공통적인 문제들은 대부분 테마의 기본 가정(Convention)과 프로젝트 설정 간의 불일치에서 발생합니다. 본 문서는 개별 오류 해결보다, LLM이 향후 유사한 설정을 구성할 때 참고할 수 있는 **동작 패턴과 주의사항**을 정의합니다.

---

## 1. 콘텐츠 섹션 인식 패턴 (Content Sectioning)

PaperMod는 기본적으로 `post` (단수형) 섹션을 메인 콘텐츠로 인식하는 경향이 있습니다.

- **패턴**: 프로젝트에서 `content/posts/` (복수형) 폴더를 사용할 경우, 테마는 이를 메인 섹션으로 자동으로 인식하지 못합니다.
- **해결 원칙**: `hugo.toml`의 `params.mainSections` 설정을 통해 명시적으로 섹션 이름을 지정해야 합니다.
  ```toml
  [params]
    mainSections = ['posts']
  ```

## 2. 시간대 및 지역화 설정 (Localization)

Hugo는 기본적으로 모든 날짜를 UTC 기준으로 처리하며, 언어 설정을 따릅니다.

- **패턴**: 한국 시간(KST) 적용 및 한국어 날짜 표시를 위해서는 전역 설정 파일에서 시간대를 명시해야 합니다.
- **해결 원칙**: `timeZone = 'Asia/Seoul'` 설정을 추가하여 빌드 시 시간대 변환이 일어나도록 합니다.

## 3. Front Matter 제약 사항 (Front Matter Constraints)

Hugo의 템플릿 엔진은 Front Matter의 필드 타입을 엄격하게 해석합니다.

- **패턴**: `published: true`와 같이 불리언 값을 사용하면, Hugo는 이를 날짜 타입으로 해석하려 시도하여 파싱 에러를 발생시킬 수 있습니다.
- **해결 원칙**: 날짜 관련 필드는 `publishDate`를 사용하거나, 게시 여부는 `draft: false`를 통해 제어하는 것이 안전합니다.

## 4. 최소 기능주의 설계 (Minimalist Design)

PaperMod는 가볍고 빠른 성능을 위해 매우 제한적인 기능만 제공하는 최소주의 테마입니다.

- **패턴**: 다른 종합 테마에서 제공하던 `tag` shortcode 같은 편의 기능이 포함되어 있지 않습니다.
- **해결 원칙**: 테마가 제공하지 않는 기능은 shortcode를 찾기보다 일반 Markdown 문법을 사용하거나, 필요 시 `layouts/shortcodes/`에 직접 구현하여 사용합니다.

## 5. CI/CD 환경 구성 주의사항 (Infrastructure)

테마의 구조와 외부 툴(GitHub Actions, gh CLI) 간의 연동 시 주의가 필요합니다.

- **패턴 1 (Dependencies)**: PaperMod는 순수 Hugo 테마이므로 `package.json`이 존재하지 않습니다. CI 워크플로우에서 무조건적인 `npm install`을 실행하면 에러가 발생합니다.
- **패턴 2 (Permissions)**: GitHub Actions에서 `.github/workflows` 파일을 수정하거나 생성하려면 `workflow` 스코프 권한이 반드시 필요합니다.

---

## 요약 및 LLM 가이드라인

향후 PaperMod 기반의 설정을 변경하거나 새로운 기능을 추가할 때 다음 원칙을 우선 고려하십시오:
1. **명시적 설정**: 테마의 기본값에 의존하기보다 `hugo.toml`에서 명시적으로 섹션과 시간대를 정의할 것.
2. **타입 엄격성**: Front Matter 필드명과 값의 타입이 Hugo의 기대치와 일치하는지 확인할 것.
3. **최소 기능 확인**: 테마에 내장된 기능인지 확인하고, 없을 경우 직접 구현하는 방향으로 접근할 것.
4. **환경 격리**: CI/CD 환경에서는 불필요한 패키지 매니저 호출을 지양하고 정확한 API 권한을 설정할 것.
