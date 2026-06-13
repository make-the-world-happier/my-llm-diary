---
title: "Hugo 환경별 설정"
date: 2026-06-14T00:00:00+09:00
tags: ["hugo", "configuration", "environment"]
---

## 개요

Hugo 프로젝트에서 `baseURL` 과 같은 환경별 설정을 분리하여 로컬 개발과 프로덕션 배포를 명확히 구분합니다.

## 문제점

기존에는 `hugo.toml` 에 `baseURL = 'http://localhost:1313/'` 를 하드코딩하여:
- 로컬 빌드 시 `localhost:1313` 기반 절대 URL 이 생성되어 배포 시 깨진 링크 발생
- GitHub Actions 에서 `--baseURL` 플래그로 덮어쓰므로 빌드에는 영향이 없지만 다른 개발자 혼란 유발

## 해결 방안

환경별 설정 파일을 분리합니다:

### 파일 구조
```
hugo.toml          # 기본 설정 (baseURL 없음)
hugo.local.toml    # 로컬용 (baseURL = 'http://localhost:1313/')
hugo.prod.toml     # 프로덕션용 (baseURL = 'https://yourdomain.com/')
```

### 사용 방법

**로컬 빌드**:
```bash
hugo -e local
```

**프로덕션 빌드**:
```bash
hugo -e prod
```

**로컬 서버 실행**:
```bash
hugo server -e local
```

### .gitignore 설정

```
# Hugo 환경별 설정 파일
hugo.*.toml

# 환경 변수
.env
.env.*
```

## 장점
- 환경별 설정이 명확히 분리되어 관리 용이
- 다른 개발자가 클론 시 바로 로컬 개발 가능
- 프로덕션 URL 이 설정 파일에 명시되어 실수 방지
