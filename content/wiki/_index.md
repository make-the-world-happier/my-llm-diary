---
title: "Wiki Index"
---

# Wiki Index

이 파일은 Wiki 의 모든 항목을 인덱싱하여 LLM 이 빠르게 검색할 수 있도록 합니다.

## 구조
- `content/wiki/` 폴더 내 모든 Markdown 파일의 메타데이터

## 항목 목록
| 파일 | 제목 | 태그 | 요약 |
|------|------|------|------|
| `errors/hugo-setup-issues.md` | Hugo 초기 설정 문제 | hugo, troubleshooting, papermod | Hugo + PaperMod 설정 시 발생한 6 가지 문제와 해결 방법 |
| `tools/docker-cheatsheet.md` | Docker 기본 명령어 모음 | docker, cheatsheet | Docker 컨테이너, 이미지, 볼륨, 네트워크 관리 명령어 |
| `projects/brain-storming-with-ai.md` | Brain Storming with AI | project, ai, llm | 로컬 LLM 과 브레인스토밍 프로젝트 개요 |
| `decisions/hugo-environment-config.md` | Hugo 환경별 설정 | hugo, configuration, environment | baseURL 을 환경별 설정 파일 (hugo.local.toml, hugo.prod.toml) 로 분리하는 설정 아키텍처 |
| `decisions/wiki-folder-structure.md` | Wiki 폴더 구조 | wiki, structure, organization | Wiki 폴더 구조 (errors/, decisions/, tools/, projects/) 변경 결정 |
| `decisions/about-page-menu.md` | About 페이지 메뉴 추가 | ui, menu, navigation | Hugo 메뉴에 About 페이지를 추가하는 UI/UX 개선 결정 |
| `tools/hugo-version-management.md` | Hugo 버전 관리 | hugo, version, update | Hugo 버전 업데이트 방법과 GitHub Actions 연동 가이드 |
| `tools/gitignore-guide.md` | .gitignore 가이드 | git, security, configuration | 민감한 파일 (.env, 환경별 설정, Hugo binary) 제외 가이드 |

## 검색 팁
- LLM 이 grep 으로 검색할 때 유용합니다: `grep -r "키워드" content/wiki/`
- 태그로 필터링: `grep -r "tags:.*태그" content/wiki/`
- 파일 경로로 직접 검색: `grep -r "content/wiki/경로" content/wiki/`
