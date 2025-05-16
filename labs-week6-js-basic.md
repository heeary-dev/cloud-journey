# 🧪 실습 기록 - 6주차 labs.md

> 실습과 결과를 정리하는 공간입니다.

---

# ✅ Day 36 – JavaScript 변수 선언 및 기초 이론

## 📘 1. 개념 정리

- JavaScript는 HTML/CSS와 함께 웹을 구성하는 **동작 제어 언어**
- HTML은 구조, CSS는 스타일, JavaScript는 사용자 행동에 반응하는 기능 구현에 사용됨
- 기본 실행 방식은 HTML 문서 내부 `<script>` 태그를 통해 브라우저에서 해석됨
- `console.log()`는 브라우저 개발자 도구(Console 탭)를 통해 **디버깅용으로 출력**하는 함수
- 변수 선언 시에는 `let`, `const` 키워드를 사용

---

## 🧪 2. 실습 명령어

```
<!-- index.html 내부에 삽입한 script -->
<script>
  // 변수 선언 및 출력
  let username = "희성";
  console.log("캠린이 사용설명서에 오신 것을 환영합니다, " + username + "님!");
</script>
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day36-console-output.png" width="500" /><br/>
  > 브라우저 콘솔에 변수 값이 포함된 환영 메시지가 출력된 화면
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day36-script-snippet.png" width="500" /><br/>
  > index.html 내부에 삽입한 `<script>` 태그와 JavaScript 코드 내용
</p>

---

## 🛠️ Troubleshooting & 기록

- 처음엔 `console.log()` 결과가 화면에 안 보여 당황했지만, **F12 → Console 탭**을 통해 확인 가능하다는 점을 학습함
- `<script>` 위치를 `<body>` 안쪽에 잘못 넣으면 HTML 구조에 영향을 줄 수 있어 **본문 끝 직전에 넣는 것이 안전**함
- VSCode로 작성한 HTML 파일을 **브라우저에서 직접 열어야** JavaScript가 실행된다는 점도 중요 포인트

---

## 💭 느낀 점

- JavaScript가 HTML 안에서 **그 자체로 실행되는 언어**라는 점이 처음엔 신기했지만, 직접 실행 결과를 보니 구조가 이해되기 시작함
- `console.log()`는 눈에 보이진 않지만, **개발자에게는 꼭 필요한 실험도구**라는 걸 깨달았고, 디버깅에도 유용하다는 걸 체감함
- 지금은 작은 출력이지만, 이후 사용자 클릭, 입력, 조건 제어까지 확장될 것을 생각하니 기대감이 생김
