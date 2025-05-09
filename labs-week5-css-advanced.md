# 🧪 실습 기록 - 5주차 labs.md

> 실습과 결과를 정리하는 공간입니다.

---

# ✅ Day 29 – 텍스트 스타일링 및 시각 정렬

## 📘 1. 개념 정리

- `color`: 텍스트 색상을 지정하는 속성 (hex, color name, rgb 등 사용)
- `background-color`: 요소의 배경 색상 지정, 박스 전체 영역에 적용됨
- `font-size`: 글자 크기를 지정, px, em, rem, % 단위 사용
- `font-family`: 글꼴 지정, 여러 대체 폰트를 콤마로 나열함
- `text-align`: 텍스트 정렬 방식 지정 (left, center, right, justify)
- `display`: 요소의 레이아웃 방식을 지정 (block, inline, inline-block 등)

---

## 🧪 2. 실습 명령어

```

body {
  font-family: 'Noto Sans KR', sans-serif;
  background-color: #f5f5f5;
  color: #222;
  line-height: 1.6;
}

#main-title {
  font-size: 36px;
  color: #2d3436;
  text-align: center;
  margin-top: 40px;
}

.main-nav a {
  font-size: 18px;
  padding: 8px 12px;
  background-color: #dfe6e9;
  border-radius: 5px;
  display: inline-block;
}

.main-nav a:hover {
  background-color: #b2bec3;
  color: #fff;
}

.intro-text {
  font-size: 20px;
  background-color: #ffffff;
  color: #444;
  padding: 25px;
  text-align: justify;
}

footer {
  font-size: 14px;
  color: #555;
  background-color: #ecf0f1;
  text-align: center;
  padding: 15px;
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day29-index-text-style.png" width="450"/><br/>
  > 텍스트 스타일과 정렬이 적용된 index.html의 실행 화면
</p>

---

## 🛠️ Troubleshooting & 기록

- `text-align: justify` 적용 시 문단 내 공백이 들쭉날쭉할 수 있어 `line-height`로 가독성 조정 필요
- `display: inline-block`을 사용하지 않으면 padding, background가 인라인 요소에 제대로 적용되지 않음을 실습으로 확인

---

## 💭 느낀 점

- 단순히 텍스트에 색상과 정렬만 추가해도 전체 페이지의 인상이 크게 달라짐을 느꼈음  
- `font-family`를 바꾸고 나니 웹페이지의 분위기가 훨씬 깔끔하고 가독성이 좋아졌음  
- 시각적 스타일을 코드로 컨트롤할 수 있다는 점이 흥미로웠고, 실무에서도 유용하게 사용할 수 있을 것 같다는 자신감이 생김

---

# ✅ Day 30 – 고급 선택자 & 가상 클래스 실습

## 📘 1. 개념 정리

- `:hover`, `:first-child`, `:last-child`, `:nth-child()` 등 가상 클래스는  
  HTML 구조나 사용자 상호작용에 따라 자동으로 스타일을 적용할 수 있는 CSS 기능임
- `+`, `>`, `~`, 공백 등 고급 선택자는 요소 간 구조 관계에 따라 특정 요소만 정확히 선택할 수 있게 해줌
- 실습을 통해 **구조 기반 선택자와 가상 클래스의 실제 동작 방식**을 시각적으로 확인하고 체득함

---

## 🧪 2. 실습 명령어

```
/* Day 30 실습용 style.css - 다양한 가상 클래스 실험 */

body {
    font-family: 'Noto Sans KR', sans-serif;
    background-color: #f5f5f5;
    color: #222;
    line-height: 1.6;
}

#main-title {
    font-size: 36px;
    color: #2d3436;
    text-align: center;
    margin-top: 40px;
}

.main-nav {
    text-align: center;
    margin: 20px 0;
    padding: 10px;
    border: 1px dashed #aaa;
    width: 80%;
    margin-left: auto;
    margin-right: auto;
}
.main-nav a {
    font-size: 18px;
    padding: 8px 12px;
    background-color: #dfe6e9;
    border-radius: 5px;
    display: inline-block;
}
.main-nav a:hover {
    background-color: #0984e3;
    color: white;
}
.main-nav a:first-child {
    font-weight: bold;
    text-decoration: underline;
}
.main-nav a:last-child {
    color: #d63031;
}

.intro-text {
    font-size: 20px;
    background-color: #ffffff;
    color: #444;
    padding: 25px;
    text-align: justify;
}
.intro-text p:last-child {
    font-style: italic;
    color: #636e72;
}
.intro-text p:nth-child(odd) {
    background-color: #f1f2f6;
}

footer {
    font-size: 14px;
    color: #555;
    background-color: #ecf0f1;
    text-align: center;
    padding: 15px;
}
footer > p:first-child {
    font-size: 14px;
    color: #6c5ce7;
    text-transform: uppercase;
}
footer > p + p {
    font-size: 12px;
    color: #b2bec3;
    font-style: italic;
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day30-index-pseudoclass.png" width="450" /><br/>
  > 다양한 가상 클래스 및 고급 선택자가 적용된 실습용 index.html 화면
</p>

---

## 🛠️ Troubleshooting & 기록

- 실습을 위해 다양한 가상 클래스와 구조 선택자를 한꺼번에 적용하다 보니  
  실제 웹페이지로서는 다소 **과한 강조, 색상 중첩, 정렬 불균형** 등이 발생했음
- 특히 `.main-nav a:first-child`, `.intro-text p:last-child`, `footer > p + p` 등에서  
  시각적으로 의미 없는 강조가 여러 번 겹치면서 **레이아웃이 흐트러짐**
- 하지만 실습 목적으로는 기능별 동작 결과를 **명확하게 시각화하는 데에 성공했음**

---

## 💭 느낀 점

- 실습 중에는 기능 확인이 우선이므로, 시각적 일관성보다 **구조와 선택자 적용이 중요한 학습으로 진행해보았다 
- 실무에서는 전체적인 톤, 사용자 경험, 가독성, 조화가 훨씬 더 중요하다는 것을 대비적으로 느낄 수 있었음  
- 오늘은 **CSS의 구조 선택자와 가상 클래스의 실질적인 사용 방식**을 체험하면서,  
  앞으로는 필요한 부분에만 간결하게 적용하는 감각을 익혀야겠다고 느꼈음

