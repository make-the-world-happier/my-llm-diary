---
title: "Wiki Index"
---

# Wiki Index

이 파일은 Wiki 의 모든 항목을 인덱싱하여 LLM 이 프로젝트의 맥락과 규칙을 빠르게 파악하고 검색할 수 있도록 돕는 지도 역할을 합니다.

## 운영 철학
본 위키는 단순한 '해결 로그'가 아닌, LLM이 향후 유사한 문제에 직면했을 때 추론의 근거로 사용할 수 있는 **패턴(Pattern), 전략(Strategy), 규칙(Rule)** 중심으로 관리합니다.

## 항목 목록
| 파일 | 제목 | 태그 | 요약 |
|------|------|------|------|
| `errors/hugo-setup-issues.md` | PaperMod 테마 동작 원리 및 주의사항 | hugo, papermod, pattern | PaperMod 테마의 기본 가정과 설정 불일치 패턴 및 해결 원칙 |
| `projects/brain-storming-with-ai.md` | Brain Storming with AI | project, ai, llm | 프로젝트의 목적, 철학 및 전체 지식 구조 정의 |
| `decisions/hugo-environment-config.md` | Hugo 환경별 설정 | hugo, configuration, environment | baseURL 등 환경별 설정을 분리하여 관리하는 전략 |
| `decisions/wiki-folder-structure.md` | Wiki 폴더 구조 | wiki, structure, organization | 지식 관리의 일관성을 위한 위키 폴더 구조 정의 및 운영 규칙 |
| `tools/hugo-version-management.md` | Hugo 버전 관리 | hugo, version, update | Hugo 버전 업데이트 및 CI/CD 연동 프로세스 |

## 검색 팁
- LLM 이 grep 으로 검색할 때 유용합니다: `grep -r "키워드" content/wiki/`
- 태그로 필터링: `grep -r "tags:.*태그" content/wiki/`
- 파일 경로로 직접 검색: `grep -r "content/wiki/경로" content/wiki/`
