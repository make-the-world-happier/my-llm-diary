---
title: "Hugo 초기 설정 시 문제점과 해결 방법"
date: 2026-06-14T00:00:00+09:00
tags: ["hugo", "troubleshooting", "papermod"]
---

## 개요

Hugo + PaperMod 테마로 블로그를 설정하는 과정에서 발생한 문제점들과 해결 방법을 기록합니다.

---

## 문제 1: Posts 가 표시되지 않음

### 증상
- `content/posts/` 에 Markdown 파일이 있음
- 하지만 `/posts/` 페이지에서 포스트가 보이지 않음

### 원인
- PaperMod 테마는 기본적으로 `post` (단수형) 섹션만 인식
- 우리는 `posts` (복수형) 를 사용 중

### 해결 방법
`hugo.toml` 에 `mainSections` 설정 추가:

```toml
[params]
  mainSections = ['posts']
```

---

## 문제 2: 날짜가 UTC 로 표시됨

### 증상
- 포스트 날짜가 "June 14, 2026" 으로 영어 + UTC 로 표시

### 원인
- Hugo 가 기본 시간대 (UTC) 를 사용

### 해결 방법
`hugo.toml` 에 시간대 설정 추가:

```toml
timeZone = 'Asia/Seoul'
```

---

## 문제 3: `published` front matter 필드 에러

### 증상
```
ERROR the "published" front matter field is not a parsable date
```

### 원인
- Hugo 가 `published` 필드를 날짜로 해석하려고 함

### 해결 방법
- `published: true` 대신 `publishDate` 사용
- 또는 `draft: false` 명시

---

## 문제 4: `tag` shortcode not found

### 증상
```
failed to extract shortcode: template for shortcode "tag" not found
```

### 원인
- PaperMod 테마가 `tag` shortcode 를 제공하지 않음

### 해결 방법
- shortcode 대신 일반 텍스트 사용
- 예: `- Hugo` (불릿 포인트)

---

## 문제 5: GitHub Actions 빌드 실패

### 증상
```
npm error enoent Could not read package.json: Error: ENOENT
```

### 원인
- PaperMod 테마에 `package.json` 이 없음
- GitHub Actions 워크플로우에서 `npm install` 을 실행하려고 함

### 해결 방법
- GitHub Actions 워크플로우에서 `npm install` 단계 제거

---

## 문제 6: gh CLI workflow scope 부족

### 증상
```
refusing to allow an OAuth App to create or update workflow
  '.github/workflows/pages.yml' without 'workflow' scope
```

### 원인
- gh CLI 가 workflow 스코프 없이 인증됨

### 해결 방법
```bash
gh auth login --scopes workflow
```

---

## 정리

| 문제 | 원인 | 해결 |
|------|------|------|
| Posts 안 보임 | `post` vs `posts` | `mainSections` 설정 |
| 날짜 UTC | 시간대 미설정 | `timeZone` 설정 |
| `published` 에러 | 필드 이름 문제 | `publishDate` 또는 `draft` 사용 |
| shortcode 에러 | 테마 미지원 | 일반 텍스트 사용 |
| npm install 실패 | package.json 없음 | npm install 단계 제거 |
| workflow scope | 인증 범위 부족 | `--scopes workflow` 추가 |
