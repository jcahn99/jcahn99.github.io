# Personal Website (Jekyll · GitHub Pages)

세이지/올리브 그린 톤의 "허바리움 저널" 컨셉 개인 웹페이지입니다.

## 폴더 구조

```
_config.yml          → 사이트 제목, 이메일, 소셜 링크 등 전역 설정
index.md             → 메인 페이지 (모든 섹션을 순서대로 include)
_layouts/default.html→ 공통 레이아웃 (head + nav + footer)
_includes/           → 섹션별 조각 (section-*.html) + nav, footer, divider
_data/               → 실제 내용(텍스트) — 여기만 수정하면 됩니다
  education.yml
  research.yml
  publications.yml
  presentations.yml
  projects.yml
  patents.yml
assets/css/main.scss  → 디자인 (색상, 폰트, 레이아웃)
assets/js/main.js     → 모바일 메뉴, 스크롤 시 네비게이션 하이라이트
assets/images/        → 프로필 사진 (placeholder 교체 필요)
```

## 1. 배포 방법

1. 이 폴더 전체를 `username.github.io` 저장소(본인 GitHub 아이디로 된 repo)에 업로드
2. GitHub repo → **Settings → Pages** 에서 Source를 `Deploy from a branch`, 브랜치를 `main`(또는 사용 중인 기본 브랜치) / `root`로 설정
3. 몇 분 후 `https://username.github.io` 에서 확인 가능
   (Jekyll + github-pages gem 조합이라 별도 빌드 설정 없이 GitHub가 자동으로 빌드합니다)

## 2. 내용 채우기 (가장 먼저 할 일)

- `_config.yml`
  - `title`, `tagline`, `email`, `url`, `author`, `social.*` 를 본인 정보로 수정
  - `profile_image` 경로를 실제 사진 파일명으로 변경
- `assets/images/` 에 실제 프로필 사진을 넣고 (예: `profile.jpg`), `_config.yml`의 `profile_image` 값을 `/assets/images/profile.jpg` 로 수정
- `_data/*.yml` 각 파일에 실제 Education / Research / Publications / Presentations / Projects / Patents 내용을 입력
  - 각 yml 파일 상단에 예시와 주석이 있으니 그 형식을 그대로 따라서 항목을 추가/삭제하면 됩니다
  - 항목 순서가 곧 표시 순서입니다 (최신이 위로 오게 배치 추천)
  - 링크(pdf, code, doi 등)가 없는 항목은 값을 `""` 로 두면 자동으로 화면에서 숨겨집니다

## 3. 나중에 여러 페이지로 분리하고 싶을 때

지금은 `index.md` 하나에서 모든 `_includes/section-*.html` 을 순서대로 불러오는 구조입니다.
나중에 예를 들어 Publications만 별도 페이지로 빼고 싶다면:

1. `publications.md` 같은 새 파일을 만들고 `layout: default` 지정
2. 그 안에서 `{% include section-publications.html %}` 한 줄만 넣기
3. `index.md` 에서는 해당 섹션 include를 지우기
4. `_includes/nav.html` 의 해당 링크를 `#publications` 대신 `/publications/` 같은 실제 경로로 변경

섹션 로직과 데이터(`_data/*.yml`)는 그대로 재사용되므로 디자인이나 내용을 다시 만들 필요는 없습니다.

## 4. 디자인 토큰 (색상/폰트 커스터마이징)

`assets/css/main.scss` 최상단 `:root` 안에 있는 CSS 변수만 바꾸면 전체 톤을 조정할 수 있습니다.

```
--bg        배경색 (따뜻한 베이지)
--sage      기본 그린 (포인트, 밑줄, 배지 등)
--sage-dark 진한 그린 (제목, 강조 텍스트)
--accent    보조 포인트 컬러
```

폰트는 Fraunces(제목) / Inter(본문) / IBM Plex Mono(날짜·태그) 조합이며, `_includes/head.html` 상단의 Google Fonts 링크에서 굵기 등을 조정할 수 있습니다.

## 5. 로컬에서 미리보기 (선택 사항)

Ruby/Bundler가 설치되어 있다면:

```
bundle install
bundle exec jekyll serve
```

`http://localhost:4000` 에서 확인 가능합니다. 로컬 환경 설정 없이 바로 GitHub에 올려서 Pages 빌드 결과로만 확인해도 무방합니다.
