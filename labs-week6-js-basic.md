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

---

# ✅ Day 37 – JavaScript 변수 선언 심화 및 형변환

## 📘 1. 개념 정리

- JavaScript 코드를 HTML과 분리해 `.js` 파일로 관리하면 유지보수에 유리하고 구조가 깔끔해짐
- `<script src="파일.js">`를 사용해 외부 자바스크립트 파일을 HTML에 연결 가능
- `let`, `const`는 변수 선언 키워드 (`let`: 변경 가능, `const`: 변경 불가)
- 문자열은 `"`, `'`으로 감싸며, `+` 연산자를 통해 연결 가능
- 숫자는 수학 연산 가능, `Number()`, `String()`으로 형변환 가능
- 출력은 전부 `console.log()`로 확인하며, 화면 대신 **개발자 도구 Console 탭**에서 결과 확인

---

## 🧪 2. 실습 명령어

```
<!-- index.html 하단 -->
<script src="script.js"></script>

<!-- script.js -->
let username = "희성";
const siteName = "캠린이 사용설명서";

console.log("안녕하세요, " + username + "님!");
console.log("이곳은 " + siteName + "입니다.");

let tempToday = 24;
let tempTomorrow = 27;
console.log("오늘과 내일 기온 차: " + (tempTomorrow - tempToday) + "도");

let likeCount = "100";
console.log("좋아요 수 (문자열): " + likeCount);
console.log("좋아요 수 (계산 후): " + (Number(likeCount) + 50));

let items = 5;
console.log("가방에 든 물건은 총 " + String(items) + "개입니다.");
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day37-script-link.png" width="500" /><br/>
  > index.html에 외부 자바스크립트 파일이 `<script src="script.js">`로 연결된 모습
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day37-script-code.png" width="500" /><br/>
  > script.js에 작성된 변수 선언, 문자열 연결, 숫자 연산, 형변환 코드
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day37-console-output.png" width="500" /><br/>
  > 브라우저 개발자 도구 Console 탭에 출력된 전체 결과
</p>

---

## 🛠️ Troubleshooting & 기록

- `<script>` 태그를 HTML 상단에 배치하면 JS 코드가 DOM보다 먼저 실행되어 오류 발생 → 항상 `<body>` 하단에 삽입하는 것이 안전함
- `"100"`과 같은 문자열 숫자는 연산 시 자동 형변환되지 않으므로 `Number()`로 명시적 변환 처리함
- 문자열 + 숫자 연산 시 괄호 사용 여부에 따라 출력값이 달라짐 → 연산 우선순위 주의 필요
- 외부 `.js` 파일로 코드 분리 후 실행 구조를 명확히 이해하게 되었고, HTML과 JS의 역할이 분리된 상태가 유지보수에 효과적임을 체감함

---

## 💭 느낀 점

- 자바스크립트를 처음으로 외부 파일에 작성해보고 HTML과 연결해보니, **진짜 웹 개발자의 흐름을 시작한 기분**이었다  
- 콘솔에 여러 종류의 데이터를 출력하면서 JS 문법을 실험하고 결과를 눈으로 확인하니, 단순한 이론보다 훨씬 깊게 이해할 수 있었음  
- 변수 선언 방식, 형변환의 필요성, 연산 방식 등 초반에 익숙해져야 할 개념들을 직접 만져보며 감을 잡을 수 있어 의미 있는 시간이었다

---

# ✅ Day 38 – 조건문, 비교/논리 연산자 실습

## 📘 1. 개념 정리

- `if`, `else if`, `else`는 조건에 따라 분기 처리할 때 사용하는 핵심 구조
- 비교 연산자 (`===`, `!==`, `<`, `>=` 등)로 값의 상태를 판별
- 논리 연산자 (`&&`, `||`, `!`)를 조합해 복합 조건을 구성할 수 있음
- 중첩 if문은 하나의 조건 내부에서 또 다른 조건을 확인할 때 사용
- **조건식과 변수명이 의미적으로 일치해야** 코드 해석과 유지보수가 쉬워짐

---

## 🧪 2. 실습 명령어

```
<!-- script.js -->
let temperature = 26;
let isSunny = true;
let hasTent = false;
let isWeekend = true;

// [조건 1] 기온에 따른 메시지
if (temperature >= 30) {
  console.log("폭염 주의! 그늘이 꼭 필요해요.");
} else if (temperature >= 20) {
  console.log("완벽한 캠핑 날씨입니다!");
} else {
  console.log("쌀쌀하니 따뜻한 옷을 챙기세요.");
}

// [조건 2] 날씨와 텐트 보유 여부
if (isSunny && hasTent) {
  console.log("맑은 날씨에 텐트도 있으니 바로 설치 가능!");
} else if (isSunny && !hasTent) {
  console.log("맑지만 텐트가 없으니 준비가 필요해요.");
} else {
  console.log("날씨가 좋지 않으니 실내 대안을 고려하세요.");
}

// [조건 3] 주말 + 텐트 보유 여부
if (isWeekend) {
  if (hasTent) {
    console.log("주말 캠핑 출발 준비 완료!");
  } else {
    console.log("주말이지만 장비가 부족해요. 캠핑 전 준비 먼저!");
  }
} else {
  console.log("평일엔 장비 점검과 계획 세우기에 좋은 날입니다.");
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day38-script-link.png" width="500" /><br/>
  > index.html에 외부 자바스크립트 파일이 `<script src="script.js">`로 연결된 모습
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day38-logic-code.png" width="500" /><br/>
  > script.js에 작성된 조건문, 중첩 if, 논리 연산자 포함 실습 코드 전체
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day38-console-output.png" width="500" /><br/>
  > 브라우저 Console 탭에 출력된 날씨, 텐트, 주말 상태별 메시지 결과
</p>

---

## 🛠️ Troubleshooting & 기록

- 처음에는 `needsTent`, `!hasTent` 등 **부정형 변수와 조건 조합이 혼동을 유발**해 출력 메시지와 변수의 의미가 어긋남  
→ `hasTent`, `isSunny` 등 긍정형 변수로 구조 변경  
→ 조건식과 출력 메시지가 일치하게 되어 가독성과 논리 흐름이 개선됨
- 중첩 if문 작성 시 중괄호 `{}` 누락 오류 발생 → 자동 들여쓰기 활용하여 구조 점검으로 해결

---

## 💭 느낀 점

- `if`, `else if`, `else` 구조를 활용해 실제 캠핑 조건별로 분기되는 메시지를 구현하면서  
**조건문이 어떻게 상황을 제어하고 웹의 행동을 바꾸는지** 직접 체감할 수 있었다  
- 변수명을 긍정형으로 설계하고 논리 연산자(`&&`, `!`)를 사용할 때 **사람의 언어와 코드 흐름이 일치하도록 만드는 것**이  
개발자에게 매우 중요한 감각이라는 걸 알게 되었다  
- 실습을 통해 **프로그래밍은 “조건에 따라 다르게 말하게 만드는 기술”**이라는 본질을 경험했다




