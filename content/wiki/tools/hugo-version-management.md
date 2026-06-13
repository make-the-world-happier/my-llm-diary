---
title: "Hugo 버전 관리"
date: 2026-06-14T00:00:00+09:00
tags: ["hugo", "version", "update"]
---

## 개요

Hugo 버전 업데이트 방법과 GitHub Actions 연동 가이드입니다.

## 현재 버전

- **최신 버전**: v0.163.1 (2026 년 6 월 기준)
- **프로젝트 버전**: v0.163.1

## 업데이트 방법

### 1. 로컬에서 최신 버전 설치

```bash
# 최신 버전 다운로드
curl -sL https://github.com/gohugoio/hugo/releases/download/v0.163.1/hugo_extended_0.163.1_linux-amd64.tar.gz -o /tmp/hugo.tar.gz

# 압축 해제
tar -xzf /tmp/hugo.tar.gz -C /tmp

# 실행 파일 복사
cp /tmp/hugo /home/worker/projects/llm-diary/hugo
chmod +x /home/worker/projects/llm-diary/hugo

# 버전 확인
/home/worker/projects/llm-diary/hugo version
```

### 2. GitHub Actions 업데이트

`.github/workflows/pages.yml` 의 `HUGO_VERSION` 을 최신 버전으로 변경:

```yaml
env:
  HUGO_VERSION: 0.163.1
```

### 3. 빌드 테스트

```bash
# 기본 빌드
hugo --quiet

# 로컬 빌드
hugo -e local --quiet

# 프로덕션 빌드
hugo -e prod --quiet
```

## 참고

- GitHub Releases: https://github.com/gohugoio/hugo/releases
- 항상 `hugo_extended` 버전 사용 (Sass 지원)
- Hugo 버전은 시간이 지나면 구식이 되므로, 최신 버전으로 유지 권장
