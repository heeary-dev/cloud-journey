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

