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

## 🖼️ 3. 실습 스크린샷  

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day23-summer-html-edit.png" width="450" /><br/>
  > summer.html 작성 화면 (시맨틱 태그 구조 포함)
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day23-summer-html-preview.png" width="450" /><br/>
  > summer.html을 브라우저에서 열었을 때 출력된 캠핑 준비물 목록
</p>

---

## 🛠️ 4. Troubleshooting & 기록  
- VS Code에서 새 프로젝트 폴더를 열고 하위 디렉토리를 만들 때 상대 경로를 정확히 지정해야 함
- `<ul>`, `<li>`로 목록을 구성할 때 들여쓰기를 맞추는 것이 가독성에 매우 중요
- `<a href="폴더/파일명.html">` 경로는 디렉토리 기준으로 설정됨 (루트는 `camping-guide`)

---

## 💭 5. 느낀 점  

처음으로 **시맨틱 태그만으로 웹페이지의 구조를 직접 짜보는 경험**을 했다.  
디자인 요소 없이도 정보의 흐름과 구조를 짜는 일 자체가 꽤 의미 있었다.  
**앞으로 만들 모든 웹페이지의 기반이 되는 구조**라는 점에서 큰 첫걸음이 된 날이었다.

---

# ✅ Day 24 – 캠핑 웹사이트 구조 설계 및 시맨틱 구조 확장

## 📘 1. 개념 정리
- Day 24는 캠핑 웹사이트의 전체 구조 설계를 수행하고, 각 카테고리 페이지에 시맨틱 HTML 태그를 적용한 날이다.
- 기존에 작성한 `gear/summer.html`의 시맨틱 구조를 기준으로, 동일한 형식으로 나머지 페이지(`seasonal.html`, `beginner.html`, `faq.html`)를 생성하였다.
- 사용한 주요 태그: `<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`
- GitHub Pages로 배포 가능한 구조를 유지하면서 캠핑 입문자에게 유용한 정보를 전달하는 형식으로 정리

---

## 🧪 2. 실습 명령어

```
# 디렉토리 및 파일 생성
mkdir food sites tips
touch food/seasonal.html sites/beginner.html tips/faq.html

# VS Code에서 각 HTML 파일을 열어 시맨틱 구조 적용
code food/seasonal.html
code sites/beginner.html
code tips/faq.html
```

---

## 3. 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day24-seasonal-semantic.png" width="450" /><br/>
  > 계절별 요리 페이지에 시맨틱 구조 적용
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day24-beginner-semantic.png" width="450" /><br/>
  > 초보자 캠핑장 소개 페이지 시맨틱 구조
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day24-faq-semantic.png" width="450" /><br/>
  > FAQ 페이지 시맨틱 구조 적용 결과
</p>

---

## 🛠️ 4. Troubleshooting & 기록
- 경로 실수 방지를 위해 모든 `<a href>`는 `/절대경로` 방식으로 통일함
- 시맨틱 태그 중복 사용 방지를 위해 `<main>`은 파일당 1회만 사용
- nav 링크에 파일이 없는 경우 404가 출력될 수 있으므로, 각 파일 존재 여부 확인 필수

---

## 💭 5. 느낀 점
- 기존에 단순히 구조만 있던 HTML이 시맨틱 구조를 통해 의미가 생기고 유지보수가 쉬워졌음을 체감함
- 시맨틱 태그를 일관되게 적용하니 전체 사이트 구조가 통일감 있게 구성되었고, 확장도 수월해질 것이라 확신함

---
# ✅ Day 25 – 사용자의 입력을 받는 <form>태그와 표형식의 <table>태그

## 📘 1. 개념 정리

- `<form>`: 사용자 입력을 서버로 전송하는 구조
- `<input>`: 다양한 형태의 입력 필드 (text, email, submit 등)
- `<label>`: 입력 필드에 대한 설명 연결, `for` 속성으로 `id`와 매칭
- `<textarea>`: 여러 줄 텍스트 입력 영역, 기본값은 태그 내부에 작성
- `<select>` + `<option>`: 드롭다운 선택, `value`가 없으면 텍스트가 value가 됨
- `<table>`: 데이터 표 형식 표현용, `<tr>`, `<th>`, `<td>`로 구성

---

## 🧪 2. 실습 명령어

```
<!-- tips/faq.html -->
<form action="/submit-question" method="post">
  <label for="username">Name:</label>
  <input type="text" id="username" name="user_name">

  <label for="email">Email:</label>
  <input type="email" id="email" name="user_email">

  <label for="question">Your Question:</label>
  <textarea id="question" name="user_question" rows="4" cols="40">Write your question</textarea>

  <br>
  <input type="checkbox" id="agree" name="consent" value="yes">
  <label for="agree">개인정보 이용에 동의합니다</label>

  <br>
  <input type="submit" value="제출">
</form>

<!-- gear/summer.html -->
<table border="1">
  <tr>
    <th>제품</th>
    <th>평균가격</th>
    <th>필수품목(O,X)</th>
  </tr>
  <tr>
    <td>쿨매트</td>
    <td>₩15,000</td>
    <td>O</td>
  </tr>
  <tr>
    <td>모기 기피제</td>
    <td>₩5,000</td>
    <td>X</td>
  </tr>
  <tr>
    <td>휴대용 선풍기</td>
    <td>₩12,000</td>
    <td>O</td>
  </tr>
</table>
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day25-faq-form.png" width="450"/><br/>
  > 문의 제출 form이 제대로 표시됨
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day25-summer-table.png" width="450"/><br/>
  > 장비 목록 table이 시맨틱 구조에 맞게 출력됨
</p>

---

## 🛠️ Troubleshooting & 기록

- `<textarea>`에 `value`를 넣어도 작동하지 않음 → 태그 내부에 기본값 작성해야 함
- `<option>`에서 `value`를 안 넣으면 텍스트가 value로 사용됨 (서버 전송 값에 주의)
- label 없이 input만 있으면 화면이 허전하고 UX가 떨어짐 → 제목(h2)과 안내문(p)을 같이 배치함

---

## 💭 느낀 점

- form 태그는 단순히 입력만 하는 게 아니라, 전체 전송 구조를 통제하는 부모 역할이라는 걸 실감함
- value와 name, label의 역할이 각각 다르며, 어디서 보이고 어디로 전송되는지를 명확히 이해할 수 있었음
- 실제 웹페이지와 비슷한 구조로 실습하니 시맨틱한 HTML 구성 방식이 훨씬 직관적으로 와닿았음

---

# ✅ Day 26 – HTML 마무리: button, HTML5 입력 필드, 테이블 병합

## 📘 1. 개념 정리

- `<button>`: 텍스트, 이미지 등 자유롭게 콘텐츠를 넣을 수 있는 유연한 버튼 태그
- `<input type="email|url|date|text">`: HTML5 입력 필드로 사용자의 입력을 쉽게 제한하고 검증
- `required`: 필수 입력을 브라우저 단에서 검증하는 속성
- `<table>`: 행과 열을 구성하여 데이터를 정리하는 태그
- `colspan`, `rowspan`: 열/행 병합을 통해 시각적 그룹화 표현 가능

---

## 🧪 2. 실습 명령어

```
<!-- faq.html -->
<section>
  <h2>문의자 정보 입력</h2>
  <form action="/submit-question" method="post">
    <label for="name">이름</label>
    <input type="text" id="name" name="user_name" required><br>

    <label for="email">이메일</label>
    <input type="email" id="email" name="user_email" required><br>

    <label for="birth">생년월일</label>
    <input type="date" id="birth" name="user_birth"><br><br>

    <button type="submit">
      <img src="send-icon.png" alt="제출" width="16">
      제출하기
    </button>
  </form>
</section>

<!-- summer.html -->
<section>
  <h2>장비 목록 요약표</h2>
  <table border="1">
    <tr>
      <th colspan="2">장비 카테고리</th>
      <th rowspan="2">공통 비고</th>
    </tr>
    <tr>
      <th>이름</th>
      <th>가격</th>
    </tr>
    <tr>
      <td>쿨매트</td>
      <td>₩15,000</td>
      <td rowspan="2">여름 필수품</td>
    </tr>
    <tr>
      <td>모기 퇴치제</td>
      <td>₩5,000</td>
    </tr>
    <tr>
      <td colspan="3">※ 일부 품목은 상황에 따라 변경될 수 있습니다.</td>
    </tr>
  </table>
</section>
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day26-faq-form-final.png" width="450"/><br/>
  > 실전형 입력 필드 form이 자연스럽게 구성됨
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day26-summer-table-merged.png" width="450"/><br/>
  > 병합 속성이 적용된 테이블이 정리되어 출력됨
</p>

---

## 🛠️ Troubleshooting & 기록

- 실전 중심 입력 필드 선택 기준 정립: 이름, 이메일, 생년월일, 홈페이지 주소 등 실무 유의미한 항목만 사용

---

## 💭 느낀 점

- 이제는 불필요한 태그까지 외우는 게 아니라, 실전에서 진짜 사용하는 HTML 구조만 익히는 게 얼마나 중요한지 알게 됐다.
- 태그 하나하나에 의미를 부여하고, 실제 흐름에 맞춰 배치하는 연습을 하면서 웹 개발자의 시야가 더 넓어진 느낌이다.

---


# ✅ Day 27 – CSS적용과 선택자 기본

## 📘 1. 개념 정리

- 외부 스타일시트는 `<link rel="stylesheet" href="파일명.css">` 형태로 `<head>` 안에 작성하며, 실무에서 가장 일반적으로 사용됨
- 선택자는 태그 선택자(`p`), 클래스 선택자(`.클래스명`), 아이디 선택자(`#아이디명`)가 있으며, 우선순위는 id > class > tag
- CSS 기본 속성: `color`, `font-size`, `background-color` 등을 통해 텍스트 색상, 크기, 배경 등을 제어할 수 있음
- 주석은 HTML에선 `<!-- -->`, CSS에선 `/* */` 사용함

---

## 🧪 2. 실습 명령어

```
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>캠린이 사용설명서</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <h1 id="main-title">캠핑 가이드에 오신 걸 환영합니다</h1>
    <nav class="main-nav">
      <a href="gear/summer.html">여름 캠핑</a> |
      <a href="food/seasonal.html">캠핑 요리</a> |
      <a href="sites/beginner.html">추천 캠핑장</a>
    </nav>
  </header>

  <main>
    <p class="intro-text">이 웹사이트는 캠핑을 처음 시작하는 분들을 위한 안내서입니다.</p>
  </main>

  <footer>
    <p>© 2025 캠린이. All rights reserved.</p>
  </footer>
</body>
</html>

/* style.css */
body {
  font-family: 'Arial', sans-serif;
  background-color: #f8f9fa;
  color: #333;
  margin: 0;
  padding: 0;
}

#main-title {
  color: #2c3e50;
  font-size: 32px;
  text-align: center;
  margin-top: 30px;
}

.main-nav {
  text-align: center;
  margin: 10px 0;
}

.main-nav a {
  color: #2980b9;
  text-decoration: none;
  margin: 0 10px;
}

.main-nav a:hover {
  text-decoration: underline;
}

.intro-text {
  text-align: center;
  font-size: 18px;
  margin: 40px 20px;
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day27-index-css-applied.png" width="450"/><br/>
  > 외부 CSS가 적용된 index.html의 실행 화면
</p>

---

## 🛠️ Troubleshooting & 기록

- 없음

---

## 💭 느낀 점

- 처음으로 style.css 파일을 외부에서 연결하고, HTML 문서 구조를 기반으로 디자인을 입히는 과정을 경험함  
- 선택자와 기본 속성을 통해 텍스트의 시각적 표현을 제어하는 감각을 익힐 수 있었음  
- 아직 배우지 않은 속성들이 존재하지만, 실습 흐름상 구조만 먼저 적용하고 이후 순차적으로 학습할 계획임



