# myblog (Hugo, GitHub Pages)

개인 기록용 한글 블로그. `minducky.github.io/myblog` 로 배포 예정.

## 1. Hugo 로컬 설치 (본인 컴퓨터에서)
- Mac: `brew install hugo`
- Windows: `choco install hugo-extended` 또는 `winget install Hugo.Hugo.Extended`
- 설치 후 확인: `hugo version`

## 2. 로컬 미리보기
```bash
hugo server -D
```
`http://localhost:1313` 접속. `-D`는 draft(초안) 글도 같이 보여줌.

## 3. 새 글 쓰기
```bash
hugo new posts/글제목.md
```
`content/posts/` 안에 파일 생성됨. 맨 위 `draft: true`를 `false`로 바꿔야 실제 배포에 포함됨.

## 4. GitHub에 올리기
1. GitHub에서 `myblog`라는 이름으로 Public 리포 생성 (계정: minducky)
2. 이 폴더에서:
```bash
git init
git add .
git commit -m "첫 커밋"
git branch -M main
git remote add origin https://github.com/minducky/myblog.git
git push -u origin main
```

## 5. GitHub Pages 배포 설정
Jekyll과 달리 Hugo는 GitHub가 자동으로 빌드해주지 않아서, `.github/workflows/hugo.yml`에 미리 만들어둔 GitHub Actions로 자동 빌드/배포하게 만들어놨어요.

1. 리포 → `Settings` → `Pages`
2. `Build and deployment` → Source를 `GitHub Actions`로 선택
3. `main`에 push할 때마다 자동으로 빌드되고 `https://minducky.github.io/myblog`에 배포됨
4. 첫 push 후 리포의 `Actions` 탭에서 빌드 진행 상황 확인 가능

## 6. 디자인/폰트 커스터마이징
- 지금 테마는 외부 테마 없이 직접 만든 아주 단순한 구조예요 (`layouts/`, `static/css/style.css`)
- 폰트는 기본적으로 시스템 폰트(맥/윈도우 한글 폰트) 사용 중이라 외부 요청 없이 빠름
- Pretendard 같은 무료 한글 웹폰트를 쓰고 싶으면 `static/css/style.css` 맨 위 주석 처리된 `@import` 줄의 주석을 풀면 됨
- 레이아웃 바꾸고 싶으면 `layouts/_default/single.html`(글 하나), `layouts/index.html`(목록), `layouts/partials/header.html`/`footer.html` 수정
- 색상, 폭, 여백 등은 `static/css/style.css` 맨 위 `:root` 변수 값만 바꾸면 전체 적용됨

## 참고
- 이 스캐폴드는 Cowork 세션의 샌드박스 네트워크 제한 때문에 `hugo build`로 직접 실행 테스트는 못 했어요. TOML 설정과 템플릿 문법은 표준 Hugo 문법대로 작성했지만, 본인 컴퓨터에 Hugo 설치 후 `hugo server -D`로 한 번 확인해보는 걸 추천해요.
- 문제가 생기면 에러 메시지 그대로 알려주면 같이 고칠 수 있어요.
