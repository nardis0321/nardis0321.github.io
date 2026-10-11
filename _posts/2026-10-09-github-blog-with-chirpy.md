---
title: Jekyll Chirpy 테마로 깃허브 블로그 만들기
date: 2026-10-09 00:00:00 +0900
categories: [Tools, Github]
tags: [jekyll, chirpy, github-pages]
---

공부한 내용을 기록할 곳이 필요해서 깃허브 블로그를 만들었다.
처음이라 헤맨 부분도 있어서, 만든 과정을 첫 글로 남겨둔다.

## 왜 깃허브 블로그?

- 마크다운에 익숙해질 수 있다.
- 호스팅 비용이 들지 않는다.
- 잔디 심을 수 있다 ㅎㅎ...

테마는 검색하다가 **Chirpy**로 골랐다. 기술 블로그용으로 많이 쓰이고, 카테고리·태그·목차·다크 모드가 기본으로 들어 있다.

## 만든 과정

### 1. Chirpy Starter로 저장소 만들기

[chirpy-starter](https://github.com/cotes2020/chirpy-starter) 저장소에서 **Use this template → Create a new repository**를 눌렀다.
저장소 이름은 반드시 `아이디.github.io` 형식이어야 한다. 그래야 `https://아이디.github.io` 주소로 접속된다.

### 2. GitHub Pages 배포 설정

저장소의 **Settings → Pages → Source**를 `GitHub Actions`로 바꿨다.
이후로는 `main` 브랜치에 push할 때마다 `.github/workflows/pages-deploy.yml`이 자동으로 사이트를 빌드하고 배포한다.
배포가 잘 됐는지는 **Actions** 탭에서 확인할 수 있다. 초록 체크가 뜨면 성공이다.

### 3. `_config.yml` 기본 설정

블로그 전체 설정은 `_config.yml`에서 한다. 내가 바꾼 항목은 다음과 같다.

```yaml
lang: ko
timezone: Asia/Seoul
title: Tech Notes
tagline: Think. Learn. Share.
description: >-
  Keep learning.
url: "https://nardis0321.github.io"
github:
  username: nardis0321
```
그리고 추가로 about 탭도 바꿨는데 왠지 부끄러워서 긴 말은 못 썼음.

## 삽질한 부분

설정 파일 아래쪽에 이런 부분이 있다.

```yaml
jekyll-archives:
  enabled: [categories, tags]
  layouts:
    category: category
    tag: tag
```

나는 `category` 값을 내가 쓸 카테고리 이름이라고 생각해서 `[notes]`로 바꿨다.
그런데 여기 값은 **카테고리 이름이 아니라 테마의 레이아웃 파일 이름**이었다.
잘못 바꾸면 카테고리 페이지가 깨지기 때문에 다시 `category`로 되돌렸다.

카테고리는 설정 파일이 아니라 **글마다** 지정한다.

## 글 쓰는 방법

`_posts` 폴더에 `YYYY-MM-DD-제목.md` 형식으로 파일을 만든다. 형식이 틀리면 글이 보이지 않는다.
파일 맨 위에는 글 정보를 적는 front matter를 넣는다.

```yaml
---
title: 글 제목
date: 2026-10-09 20:00:00 +0900
categories: [대분류, 소분류]
tags: [태그1, 태그2]
---
```

- `date`에 `+0900`을 붙여야 한국 시간 기준으로 표시된다.
- 미래 시각을 적으면 그 시각이 될 때까지 글이 보이지 않는다.
- 카테고리는 최대 2단계까지 쓸 수 있다.

## 앞으로 해보면 좋은 것

- [ ] giscus로 댓글 기능 붙이기
- [ ] 로컬에서 미리보기 환경 만들기
- [ ] Google Search Console에 사이트 등록하기
