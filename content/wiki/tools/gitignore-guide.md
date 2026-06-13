---
title: ".gitignore 가이드"
date: 2026-06-14T00:00:00+09:00
tags: ["git", "security", "configuration"]
---

## 개요

민감한 파일과 빌드 산출물을 Git 에서 제외하는 가이드입니다.

## .gitignore 설정

```
# Hugo public folder
public/

# Hugo build lock file
.hugo_build.lock

# Hugo binary
hugo

# Hugo 환경별 설정 파일
hugo.*.toml

# Environment variables
.env
.env.*
```

## 각 항목의 이유

### public/
- Hugo 빌드 산출물
- Git 에 포함하면 불필요한 파일 크기 증가
-每次 빌드 시 재생성 가능

### .hugo_build.lock
- Hugo 빌드 중 생성되는 잠금 파일
- 프로세스 충돌 방지용

### hugo
- Hugo 실행 파일 (약 60MB)
- GitHub 의 권장 최대 파일 크기 (50MB) 초과
- Git Large File Storage(LFS) 사용 권장 또는 제외

### hugo.*.toml
- 환경별 설정 파일 (hugo.local.toml, hugo.prod.toml)
- 민감한 정보 (URL 등) 포함 가능
- 각 개발자가 로컬 환경에 맞게 설정

### .env, .env.*
- 환경 변수 파일
- API 키, 비밀번호 등 민감한 정보 포함
- 절대 Git 에 포함하면 안 됨

## 보안 팁

1. **푸시 전 확인**: `git diff` 로 변경 사항을 미리 확인
2. **민감한 정보 확인**: API 키, 비밀번호, 시크릿 키가 파일에 포함되지 않았는지 철저히 확인
3. **실수 시**: Git 히스토리에서 민감한 정보를 완전히 제거하려면 `git filter-branch` 또는 `BFG Repo-Cleaner` 사용 권장
