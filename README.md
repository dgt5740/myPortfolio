# 초급프로젝트 포트폴리오 웹사이트 과제

Hugo 정적 사이트 생성기(SSG)와 GitHub Actions를 활용하여 구축 및 자동 배포한 개인 포트폴리오 웹사이트입니다.

- **공개 사이트**: [https://dgt5740.github.io/myPortfolio/](https://dgt5740.github.io/myPortfolio/)
- **소스 저장소**: [https://github.com/dgt5740/myPortfolio](https://github.com/dgt5740/myPortfolio)
- **배포 워크플로**: [https://github.com/dgt5740/myPortfolio/actions](https://github.com/dgt5740/myPortfolio/actions)
- **작성자**: 양현수 (전북대학교 컴퓨터인공지능학부)

---

## 1. 도구 버전 및 설치 절차 안내

본 프로젝트는 아래 환경에서 빌드 및 배포가 검증되었습니다.

- **OS**: Windows 11 / Ubuntu Latest (GitHub Actions)
- **Hugo**: `v0.143.0+extended` (Dart Sass 지원을 위해 Extended 버전 필수)
- **Python**: `3.9` 이상 (수업 제공 배포 스크립트 실행용)
- **Git**: `2.40` 이상

### 설치 절차
1. **Git & Python**: 공식 홈페이지([git-scm.com](https://git-scm.com/), [python.org](https://www.python.org/))에서 설치합니다.
2. **Hugo Extended 설치**:
   - **Windows (Winget)**: `winget install Hugo.Hugo.Extended --version 0.143.0`
   - **수동 설치**: [Hugo Releases](https://github.com/gohugoio/hugo/releases/tag/v0.143.0)에서 `hugo_extended_0.143.0_...` 압축 해제 후 `PATH` 환경 변수에 등록합니다.
   - **설치 확인**: `hugo version` 명령어로 `extended` 문구를 확인합니다.

---

## 2. 빌드 및 실행(재현) 명령

저장소를 복제한 뒤 `site` 디렉토리로 이동하여 로컬 서버 실행 또는 정적 빌드를 진행합니다.

```bash
# 1. 저장소 복제 및 site 폴더 이동
git clone [https://github.com/dgt5740/myPortfolio.git](https://github.com/dgt5740/myPortfolio.git)
cd myPortfolio/site

# 2. 로컬 개발 서버 실행 (실시간 미리보기: http://localhost:1313/myPortfolio/)
hugo server -b http://localhost:1313/myPortfolio/ --theme template --themesDir themes

# 3. 정적 사이트 빌드 검증 (site/public 생성)
hugo --gc --minify --theme template --themesDir themes
```

---

## 3. 수정 및 재배포 안내

### 주요 수정 파일 위치

* **소개·학력·활동 콘텐츠**: `site/hugo.yaml` (메뉴, About, Education, Skills, Projects, Contact)
* **루트 엔트리 마크다운**: `site/content/_index.md`
* **스타일 및 접근성 CSS**: `site/themes/template/static/css/theme.css`
* **템플릿 레이아웃**: `site/themes/template/layouts/partials/` (헤더, 언어전환, 푸터 등)
* **프로필 및 프로젝트 이미지**: `site/static/images/`

### 재배포 및 확인 절차

1. **코드 수정 후 커밋 & 푸시**:
```bash
git add .
git commit -m "docs: README 및 포트폴리오 정보 갱신"
git push origin main
```


2. **배포 상태 확인**: 저장소 상단 **Actions** 탭에서 `Deploy Hugo to GitHub Pages` 워크플로가 녹색 체크(Success)로 완료되었는지 확인합니다.
3. **공개 화면 확인**: 배포 사이트 URL에 접속하여 변경 사항을 확인합니다.

---

## 4. 출처 및 라이선스 고지

본 프로젝트는 오픈소스 라이선스를 준수하며, 자료의 출처 및 제작 구분을 아래와 같이 명시합니다.

* **원본 테마**: Hugo Profile by gurusabarish (MIT License)
* **배포 스크립트**: 2026학년도 초급프로젝트 수업 제공 도구 (`prepare_github_pages.py v3.1`)
* **아이콘 및 폰트**: FontAwesome 6, Bootstrap 5, Google Fonts (오픈소스 라이선스 준수)

### 자료 제작 및 AI 활용 구분

| 구분 | 대상 항목 | 제작 / 출처 형태 |
| --- | --- | --- |
| **직접 제작** | 프로필 및 활동 소개 기획, 대표 활동 캡처 이미지, Git 이력 관리 | 본인 직접 작성 및 캡처 |
| **외부 자료** | Hugo Profile 테마 원본 코드, 수업 제공 자동 배포 스크립트 | 오픈소스 및 수업 제공물 활용 |
| **AI 활용** | 영문 번역 검수, 웹 접근성(W3C `aria-label`) 속성 보정, 보고서 규격 검토 | AI 도구 보조 활용 |