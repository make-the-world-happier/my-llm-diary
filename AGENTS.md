# LLM 다이어리 프로젝트 지침

이 프로젝트는 Hugo 기반의 정적 블로그입니다.

## 폴더 구조
- `content/posts/` - 블로그 포스트 (Markdown)
- `content/wiki/` - LLM Wiki (Markdown)
  - `errors/` - 오류 해결
  - `decisions/` - 아키텍처 결정
  - `tools/` - 도구 사용법
  - `projects/` - 프로젝트별
- `hugo.toml` - Hugo 기본 설정
- `hugo.local.toml` - 로컬 개발 환경 설정
- `hugo.prod.toml` - 프로덕션 환경 설정
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
- **커밋 및 푸시는 사용자의 명시적인 지시가 있을 때만 실행**
- `git add`, `git commit`, `git push` 모두 사용자가 지시할 때까지 대기
- 지시가 없을 경우 Git 작업을 절대 자동 실행하지 않음

## ⚠️ 보안 지침 (반드시 준수)

### 푸시 전 필수 확인
1. **개인정보, 토큰, API 키, 비밀번호, 시크릿 키**가 파일에 포함되지 않았는지 철저히 확인
2. `.env`, `.git/config`, `hugo.toml` 등 설정 파일에 민감한 정보가 없는지 반드시 검토
3. `git diff` 로 변경 사항을 미리 확인한 후 commit

### 커밋 및 푸시 규칙
- **커밋은 사용자의 명시적인 지시가 있을 때만 실행**
- **푸시는 사용자의 명시적인 지시가 있을 때만 실행**
- `git add`, `git commit`, `git push` 명령은 사용자가 "커밋해", "푸시해"라고 지시할 때까지 절대 자동으로 실행하지 않음
- 사용자가 Git 작업을 요청할 경우, 변경 사항을 먼저 확인하고 지시에 따라 단계별로 실행
