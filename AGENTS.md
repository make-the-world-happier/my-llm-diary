# LLM 다이어리 프로젝트 지침

이 프로젝트는 Hugo 기반의 정적 블로그입니다.

## 폴더 구조
- `content/posts/` - 블로그 포스트 (Markdown)
- `content/wiki/` - LLM Wiki (Markdown)
  - `errors/` - 오류 해결
  - `decisions/` - 아키텍처 결정
  - `tools/` - 도구 사용법
  - `projects/` - 프로젝트별
- `hugo.toml` - Hugo 설정
- `themes/PaperMod/` - 테마 (git submodule)

## 콘텐츠 작성 규칙
1. 모든 Markdown 파일은 front matter를 포함해야 함
2. 날짜는 +09:00 시간대 사용 (예: 2026-06-14T00:00:00+09:00)
3. 포스트 제목은 한국어로 작성
4. Wiki 항목은 태그(tags)를 포함하여 검색 가능하게 작성

## Hugo 명령어
- 새 포스트: `hugo new posts/YYYY-MM-DD-제목.md`
- 새 Wiki: `hugo new wiki/errors/제목.md`
- 로컬 테스트: `hugo server -D --buildFuture --bind 0.0.0.0 --port 1313`

## Git 작업
- 변경 사항 후: `git add . && git commit -m "메시지" && git push`
