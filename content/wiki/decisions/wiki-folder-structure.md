---
title: "Wiki 폴더 구조"
date: 2026-06-14T00:00:00+09:00
tags: ["wiki", "structure", "organization"]
---

## 개요

Wiki 폴더 구조를 명확히 구분하여 지식 관리의 일관성을 유지합니다.

## 폴더 구조

```
content/wiki/
├── errors/       # 오류 해결 기록
├── decisions/    # 아키텍처 결정 사항 (ADR)
├── tools/        # 도구 사용법
└── projects/     # 프로젝트별 기록
```

## 각 폴더의 용도

### errors/
- 발생한 오류와 해결 방법 기록
- 예: `hugo-setup-issues.md`

### decisions/
- 기술 결정 사항 (Architecture Decision Record, ADR) 기록
- 왜 그 결정을 내렸는지, 어떤 대안이 있었는지 기록
- 예: `hugo-environment-config.md`, `about-page-menu.md`

### tools/
- 도구 사용법 및 가이드 기록
- 예: `docker-cheatsheet.md`, `gitignore-guide.md`

### projects/
- 프로젝트 개요 및 브레인스토밍 기록
- 예: `brain-storming-with-ai.md`

## 변경 이력

| 날짜 | 변경 내용 |
|------|-----------|
| 2026-06-14 | `troubleshooting/` → `errors/` 로 폴더명 변경 |
| 2026-06-14 | `decisions/` 폴더 신규 생성 |
