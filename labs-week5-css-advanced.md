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

---

# ✅ Day 31 – 박스모델의 정확한 이해을 위한 재정리 및 추가 싫습

## 📘 1. 개념 정리

- 박스 모델(Box Model)은 HTML 요소가 사각형 박스로 구성되어 있고, 그 안에 4단계 구조를 가짐
  - `content`: 실제 콘텐츠 영역
  - `padding`: 콘텐츠와 테두리 사이 내부 여백
  - `border`: 요소의 테두리
  - `margin`: 요소 바깥 여백
- `width`, `height`, `padding`, `margin` 조합에 따라 요소의 배치와 크기, 간격이 완전히 달라짐
- 시각적으로 체감하는 게 핵심인 개념으로, DevTools를 통해 직접 구조를 확인하는 것이 중요

---

## 🧪 2. 실습 명령어

```
/* 박스 모델 실습 */

.box-layout {
  width: 90%;
  margin: 0 auto;
  margin-top: 40px;
}

.box {
  background-color: #dfe6e9;
  color: #2d3436;
  font-size: 20px;
  text-align: center;
  border: 2px solid #636e72;
  margin: 20px 0;
}

/* 개별 박스 설정 */
.box-1 {
  width: 100%;
  padding: 20px;
}

.box-2 {
  width: 80%;
  padding: 10px 30px;
  margin-left: auto;
  margin-right: auto;
}

.box-3 {
  width: 60%;
  padding: 40px;
  margin: 0 auto;
  background-color: #ffeaa7;
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day31-box-layout.png" width="450"/><br/>
  > 다양한 margin, padding, width 설정으로 시각 차이를 실습한 박스 레이아웃
</p>

---

## 🛠️ Troubleshooting & 기록

- 박스마다 width, padding, margin이 어떻게 시각적으로 다르게 작용하는지 명확하게 확인할 수 있었음  
- padding은 콘텐츠 영역을 확장하면서 배경색에 영향을 줬고, margin은 요소 간 간격만 조정됨을 눈으로 확인함  
- margin이 바깥 여백이기 때문에 배경색이 투명하게 유지된다는 점을 DevTools로 보면서 체득함  
- `margin: 0 auto`를 통해 수평 가운데 정렬이 된다는 점도 실습을 통해 완전히 이해함

---

## 💭 느낀 점

- 박스 모델은 이론으로만 이해할 수 있는 게 아니라,  
  반드시 눈으로 보고 손으로 배치해봐야 감이 잡히는 개념이라는 걸 다시 느꼈음  
- DevTools의 박스 시각화는 이해에 큰 도움이 되었고,  
  특히 margin/padding의 구분을 시각적으로 보는 순간 개념이 확실히 정리됐음  
- 이후 flex나 grid를 배울 때도 이 감각이 중요한 밑바탕이 될 것 같음

---

# ✅  Day 32 – 전체 구조 통일 및 CSS 스타일 정리

## 📘 1. 개념 정리

- 웹사이트가 여러 HTML 파일로 구성될수록 공통된 style.css를 사용해 디자인을 통일하는 것이 중요함
- `header`, `nav`, `main`, `footer` 등의 시맨틱 구조는 모든 페이지에 일관되게 구성되어야 유지보수와 확장성이 높아짐
- 공통 요소에는 반복되는 클래스명을 지정하고, 개별 콘텐츠만 각 HTML에서 다르게 관리하는 구조를 적용

---

## 🧪 2. 실습 명령어

```
/* style.css 주요 공통 스타일 */

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
  border-bottom: 1px solid #ccc;
}
.main-nav a {
  font-size: 18px;
  padding: 8px 12px;
  color: #2d3436;
  text-decoration: none;
  margin: 0 8px;
  transition: background-color 0.3s ease;
}
.main-nav a:hover {
  background-color: #dfe6e9;
  border-radius: 4px;
}

.intro-text {
  max-width: 700px;
  margin: 0 auto;
  font-size: 18px;
  background-color: #ffffff;
  color: #444;
  padding: 25px;
  border-radius: 8px;
  box-shadow: 0 0 8px rgba(0, 0, 0, 0.03);
  text-align: left;
}

footer {
  font-size: 14px;
  color: #777;
  background-color: #ecf0f1;
  text-align: center;
  padding: 20px;
  margin-top: 40px;
}
footer p {
  margin: 5px 0;
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day32-style-unified-index.png" width="450" ><br/>
  > index.html에 스타일이 통일된 구조로 적용된 결과
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day32-style-unified-gear.png" width="450" /><br/>
  > gear/summer.html에 헤더, 내비, 푸터가 일관되게 적용된 결과
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day32-style-unified-food.png" width="450" /><br/>
  > food/seasonal.html에 통일된 시각 구조 반영
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day32-style-unified-tips.png" width="450" /><br/>
  > tips/faq.html에 적용된 스타일 통일 예시
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day32-style-unified-sites.png" width="450" /><br/>
  > sites/beginner.html도 공통 스타일 구조로 정리됨
</p>

---

## 🛠️ Troubleshooting & 기록

- 각 HTML 파일이 디렉토리 위치에 따라 상대 경로가 달라 `href`, `link` 경로를 페이지마다 조정해야 했음  
- 파일마다 중복된 구조를 일일이 수정하기보다 **공통 구조를 복붙한 뒤 내용만 바꾸는 방식**이 훨씬 효율적이었음  
- 디자인보다도 **구조 정돈과 시각적 일관성** 확보가 이번 실습의 핵심이었음

---

## 💭 느낀 점

- HTML 파일이 많아지면 **디자인보단 구조 통일이 훨씬 더 중요하다는 걸 실감**  
- header/nav/footer 같은 반복되는 레이아웃은 반드시 CSS로 공통 관리해야 유지가 쉬움  
- 오늘 실습을 통해 캠핑 웹이 **단순한 실습용 프로젝트를 넘어서, 하나의 실제 사이트처럼 구성**될 수 있다는 자신감이 생김

---

# ✅  Day 33 – Flexbox 실습

## 📘 1. 개념 정리

- Flexbox는 요소를 **가로 또는 세로 방향(1차원)** 으로 유연하게 정렬하는 CSS 레이아웃 도구
- 주 축(main axis)과 교차 축(cross axis)을 기준으로 `justify-content`, `align-items` 등으로 정렬
- 주요 속성:
  - `display: flex`: Flex 컨테이너 선언
  - `flex-direction`: 주 축 방향 설정 (row, column)
  - `flex-wrap`: 줄바꿈 허용 여부
  - `justify-content`: 주 축 정렬
  - `align-items`: 교차 축 정렬
  - `flex`, `order`, `align-self`: 개별 아이템 제어

---

## 🧪 2. 실습 명령어

```
<!-- gear/summer.html 내부 section -->
<section class="gear-flex">
  <h2>Recommended Summer Gear</h2>
  <div class="gear-container">
    <div class="gear-card">Tent</div>
    <div class="gear-card">Cooler</div>
    <div class="gear-card">Portable Fan</div>
    <div class="gear-card">Water Jug</div>
    <div class="gear-card">Sunshade</div>
    <div class="gear-card">Camping Chair</div>
  </div>
</section>

<!-- style.css 내부 추가 -->
.gear-flex {
  padding: 2rem;
  background-color: #f9f9f9;
}

.gear-container {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: space-between;
  align-items: stretch;
}

.gear-card {
  background-color: #ffffff;
  border: 1px solid #ccc;
  padding: 1.5rem;
  width: 30%;
  text-align: center;
  box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.1);
  box-sizing: border-box;
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day33-gear-flexbox.png" width="500" /><br/>
  > Flexbox로 정렬된 여름 캠핑 장비 카드 레이아웃 (6개 카드, 2줄 정렬)
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day33-gear-center.png" width="500" /><br/>
  > justify-content를 center로 변경해 중앙 정렬된 카드 배치
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day33-gear-two-column.png" width="500" /><br/>
  > 카드 width를 45%로 변경해 2열로 정렬된 결과 화면
</p>

---

## 🛠️ Troubleshooting & 기록

- `flex-wrap` 누락 시 카드들이 한 줄에 모두 몰려서 깨짐 → `flex-wrap: wrap`으로 해결
- `box-sizing: border-box`를 생략하면 padding 포함 너비 계산이 달라짐 → 레이아웃 틀어짐 방지용으로 필수

---

## 💭 느낀 점

- Flexbox의 `justify-content`, `align-items` 개념을 실제로 적용해보니 축 개념의 중요성이 실감됨
- float, inline-block보다 훨씬 직관적이고 유지보수가 쉬운 구조라는 점에서 실무 활용도 높아 보임
- 향후 Grid와의 차이를 비교해보면 더 깊은 이해가 가능할 것으로 기대됨
