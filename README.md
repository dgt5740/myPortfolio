
```markdown
# 2026년 초급프로젝트 과제 1 - 개인 포트폴리오 웹사이트

> **Hugo 정적 사이트 생성기(SSG)**와 **GitHub Actions**를 활용하여 구축 및 자동 배포한 개인 소개 및 포트폴리오 웹사이트입니다.

- **공개 배포 사이트**: [https://dgt5740.github.io/myPortfolio/](https://dgt5740.github.io/myPortfolio/)
- **소스 코드 저장소**: [https://github.com/dgt5740/myPortfolio](https://github.com/dgt5740/myPortfolio)
- **작성자**: 양현수 (전북대학교 컴퓨터인공지능학부)

---

## 1. 개발 및 빌드 환경 안내

본 프로젝트는 아래 도구 및 환경에서 빌드와 배포가 검증되었습니다.

- **OS**: Windows 11
- **Hugo**: `v0.143.0+extended` 이상 (Dart Sass 파이프라인 지원 필요)
- **Python**: 3.9 이상
- **CI/CD**: GitHub Actions

### 로컬 실행 및 확인 방법
로컬 개발 환경에서 사이트를 실시간으로 확인하려면 프로젝트 루트에서 `site` 폴더로 이동한 뒤 Hugo 로컬 서버를 실행합니다.

```bash
cd site
hugo server -b http://localhost:1313/ --theme template --themesDir themes

```

실행 후 웹 브라우저에서 `http://localhost:1313/`으로 접속하면 실시간 미리보기가 가능합니다.

---

## 2. 콘텐츠 수정 및 재배포 안내 (P57)

### 주요 수정 파일 위치

| 구분 | 수정 파일 경로 | 주요 설명 |
| --- | --- | --- |
| **기본 정보 & 콘텐츠** | `site/hugo.yaml` | 상단 메뉴, About, Education, Experience, Skills, Projects, Contact |
| **커스텀 스타일** | `site/themes/template/static/css/theme.css` | 디자인 스타일 및 접근성 보정 |
| **푸터 소셜 아이콘** | `site/themes/template/layouts/partials/sections/footer/socialNetwork.html` | 푸터 영역 소셜 네트워크 링크/아이콘 |
| **이미지 자원** | `site/static/images/` | 프로필 사진 및 대표 프로젝트 이미지 |

### 자동 재배포 및 반영 확인 절차

1. **로컬 파일 수정 후 커밋 & 푸시**
```bash
git add .
git commit -m "docs: update portfolio content"
git push origin main

```


2. **GitHub Actions 배포 확인**
* 원격 저장소의 `Actions` 탭으로 이동하여 `Deploy Hugo to GitHub Pages` 워크플로가 정상 완료(녹색 체크 표시)되었는지 확인합니다.


3. **배포 상태 최종 확인**
* [https://dgt5740.github.io/myPortfolio/](https://dgt5740.github.io/myPortfolio/) 접속 후 변경사항을 확인합니다.



---

## 3. 원본 테마 및 라이선스 고지

* **사용 테마**: [Hugo Profile](https://github.com/gurusabarish/hugo-profile) by gurusabarish
* **라이선스**: MIT License
* **테마 배포 준비 도구**: 수업 제공 `prepare_github_pages.py` v3.1 스크립트 활용

```
