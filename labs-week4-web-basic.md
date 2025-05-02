# 🧪 실습 기록 - 3주차 labs.md

> 명령어 실습과 결과를 정리하는 공간입니다.

---

# ✅ Day 22 – HTML 첫걸음

## 📘 1. 개념 정리
- HTML은 웹 페이지를 만들기 위한 기본 언어이다.
- `<html>`, `<head>`, `<body>` 기본 구조를 이해하고 사용한다.
- `<h1>`, `<p>`, `<ul>`, `<li>`, `<a>` 같은 태그들을 이용해 페이지를 구성한다.
- Visual Studio Code를 사용해 작성하며, .html 파일로 저장한다.
- git add → git commit → git push 로 GitHub에 업로드하여 관리한다.

---

## 🧪 2. 실습 명령어

(Visual Studio Code 안에서 작업)

- index.html 파일 작성

```
<!DOCTYPE html>
<html>
<head>
    <title>캠린이 사용설명서</title>
</head>
<body>
    <h1>캠핑 입문자를 위한 가이드</h1>
    <p>캠핑 준비, 요리, 추천 캠핑장, 팁을 안내합니다.</p>

    <ul>
        <li><a href="gear/summer.html">캠핑 준비물</a></li>
        <li><a href="food/seasonal.html">캠핑 요리</a></li>
        <li><a href="sites/beginner.html">캠핑장 추천</a></li>
        <li><a href="tips/faq.html">캠핑 팁</a></li>
    </ul>
</body>
</html>

```
- Git Bash 사용해서 GitHub에 업로드
```
git add .
git commit -m "Add index.html for 캠린이 가이드 메인 페이지"
git push origin main
```

---

## 🖼️ 3. 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day22-index-edit.png" width="450" /><br/>
  > index.html 작성 화면
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day22-index-result.png" width="450" /><br/>
  > 웹 페이지 출력 화면
</p>

---

## 🛠️ 4. Troubleshooting & 기록
- Git 터미널 작업이 익숙하지 않아 처음에는 명령어를 외워서 입력함.
- `git add`, `git commit`, `git push` 순서를 잘 기억하고 따라야 한다.
- HTML 기본 구조는 머릿속에 익힐 수 있을 정도로 반복 작성하는 것이 중요하다.

---

## 💭 5. 느낀 점
- Visual Studio Code로 직접 HTML을 작성하고, Git 터미널로 관리하는 과정을 처음 경험했다.
- 단순히 파일을 만드는 것이 아니라 "버전 관리"까지 함께하는 게 신기했다.
- 아직 Git 명령어는 어색하지만, 몇 번 반복하면 손에 익을 것 같아 자신감이 생겼다.

---

# ✅ Day 23 – HTML 시멘틱태그 

## 📘 1. 개념 정리  
- HTML5 시맨틱 태그(`header`, `nav`, `main`, `footer`)를 사용하여 웹 페이지 구조를 명확하게 구성
- `<ul>`, `<li>`로 항목 목록을 표현하고, `<nav>` 안에는 사이트 내비게이션 링크를 구성함
- 디렉토리 구조는 콘텐츠를 분류하기 위해 `gear/`, `food/`, `sites/`, `tips/` 하위 폴더로 구성
- 실습 파일: `camping-guide/gear/summer.html`

---

## 🧪 2. 실습 명령어  

```
mkdir -p gear                    # 카테고리용 디렉토리 생성
cd gear
touch summer.html               # 여름 캠핑 준비물 페이지 생성
code summer.html                # VS Code로 파일 열기
```

---

## 🖼️ 실습 스크린샷  

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day23-summer-html-edit.png" width="450" /><br/>
  > summer.html 작성 화면 (시맨틱 태그 구조 포함)
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day23-summer-html-preview.png" width="450" /><br/>
  > summer.html을 브라우저에서 열었을 때 출력된 캠핑 준비물 목록
</p>

---

## 🛠️ Troubleshooting & 기록  
- VS Code에서 새 프로젝트 폴더를 열고 하위 디렉토리를 만들 때 상대 경로를 정확히 지정해야 함
- `<ul>`, `<li>`로 목록을 구성할 때 들여쓰기를 맞추는 것이 가독성에 매우 중요
- `<a href="폴더/파일명.html">` 경로는 디렉토리 기준으로 설정됨 (루트는 `camping-guide`)

---

## 💭 느낀 점  

처음으로 **시맨틱 태그만으로 웹페이지의 구조를 직접 짜보는 경험**을 했다.  
디자인 요소 없이도 정보의 흐름과 구조를 짜는 일 자체가 꽤 의미 있었다.  
**앞으로 만들 모든 웹페이지의 기반이 되는 구조**라는 점에서 큰 첫걸음이 된 날이었다.

