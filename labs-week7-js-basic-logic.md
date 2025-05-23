# 🧪 실습 기록 - 7주차 labs.md

> 실습과 결과를 정리하는 공간입니다.

---

# ✅ Day 43 – 조건문이 있는 함수 설계 & 화살표 함수 변환

## 📘 1. 개념 정리

- 함수 내부에 조건문을 작성하면 입력값에 따라 다양한 결과를 분기할 수 있음  
- `return`은 조건마다 하나씩 작성되며, 실행 즉시 함수가 종료됨  
- 기존 함수 선언 방식은 `function`, 축약된 함수 표현은 화살표 함수(`=>`)로 작성  
- 화살표 함수는 짧은 함수 표현에 적합하며, 중괄호 `{}`와 `return`은 한 줄일 때 생략 가능

---

## 🧪 2. 실습 명령어

```
// 1. 기온에 따라 캠핑 메시지 출력
function campingMessage(temp) {
  if (temp >= 30) {
    return "무더위 캠핑은 조심하세요!";
  } else if (temp >= 15) {
    return "야외 활동하기 좋은 날씨입니다.";
  } else {
    return "쌀쌀해요. 따뜻한 장비를 챙기세요.";
  }
}

// 2. 닉네임과 기온을 받아 안내 메시지 생성
function introduce(name, temp) {
  return `${name}님, 오늘의 날씨에 따른 캠핑 안내: ${campingMessage(temp)}`;
}

// 3. 위 함수를 화살표 함수 버전으로 변환
const campingMessageArrow = temp => {
  if (temp >= 30) return "무더위 캠핑은 조심하세요!";
  else if (temp >= 15) return "야외 활동하기 좋은 날씨입니다.";
  else return "쌀쌀해요. 따뜻한 장비를 챙기세요.";
};

const introduceArrow = (name, temp) =>
  `${name}님, 오늘의 날씨에 따른 캠핑 안내: ${campingMessageArrow(temp)}`;
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day43-function-conditions.png" width="500" /><br/>
  > 조건문이 포함된 함수와 화살표 함수 변환까지 포함된 전체 script.js 코드
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day43-console-output.png" width="500" /><br/>
  > 입력값에 따라 분기된 캠핑 메시지가 Console에 정상 출력된 결과
</p>

---

## 🛠️ Troubleshooting & 기록

- `return`은 실행되는 순간 함수가 종료된다는 점을 실습하면서 체감함  
- 조건문에서 `else if`나 `else` 없이 return만 써도 다음 조건을 검사하지 않게 되는 구조를 이해함  
- 화살표 함수로 변환할 때는 **중괄호 `{}` 안에 조건문이 있을 경우 반드시 return을 명시해야 한다는 규칙**을 다시 확인함  
- `const fn = () => 값` 구조는 한 줄 반환 함수에만 해당되므로, 조건문이 들어가는 경우에는 중괄호와 return을 꼭 써야 한다

---

## 💭 느낀 점

- 함수 안에 조건문을 직접 넣어 로직을 구성하니, 마치 “판단 기계”를 직접 만든 느낌이었고  
  **입력에 따라 코드가 스스로 분기해서 다른 메시지를 출력한다는 흐름이 매우 직관적**이었다  
- 기존의 길고 반복되는 코드를 함수로 나누고, 그걸 화살표 함수로 축약하니  
  **코드가 짧아지면서도 명확해지는 경험**을 할 수 있었다  
- 이번 실습은 단순히 “함수를 배웠다”에서 벗어나  
  **현실 조건을 코드로 설계하고 표현하는 첫 구성 경험**이 되었다

---

# ✅ Day 44 – 반복문 (for, while, break, continue) 기초 실습

## 📘 1. 개념 정리

- `for`문은 반복 횟수가 명확할 때 사용하는 구조로, `for (초기값; 조건; 증감)` 형식  
- `while`문은 반복 조건만 주고 내부에서 조건을 변경하는 구조 → 무한 루프 주의  
- `break`는 반복문을 즉시 종료하고, `continue`는 현재 반복을 건너뛰고 다음 반복으로 이동  
- 배열과 함께 `for`문을 사용하면, 인덱스를 기준으로 순차 접근 가능 (`arr[i]`)  
- 반복문 안에서 조건문을 결합해 다양한 흐름 제어가 가능

---

## 🧪 2. 실습 명령어

```
// 1. 캠핑 준비물 출력 (for문)
const gearList = ["텐트", "침낭", "랜턴", "버너", "식기세트"];

for (let i = 0; i < gearList.length; i++) {
  console.log(`${i + 1}. ${gearList[i]} 준비 완료`);
}

// 2. 장작 소진 시뮬레이션 (while문)
let firewood = 5;
while (firewood > 0) {
  console.log(`장작 ${firewood}개 남음`);
  firewood--;
}
console.log("장작이 모두 탔습니다!");

// 3. 짝수 인원만 안내 (continue)
for (let i = 1; i <= 6; i++) {
  if (i % 2 !== 0) continue;
  console.log(`캠핑 참가자 ${i}번: 안내 메시지 전송 완료`);
}

// 4. 온도 조건에 따른 반복 중단 (break)
const temps = [22, 21, 19, 17, 14, 9, 5];

for (let i = 0; i < temps.length; i++) {
  if (temps[i] < 10) {
    console.log("온도가 너무 낮습니다. 캠핑 중단!");
    break;
  }
  console.log(`현재 온도: ${temps[i]}도 - 캠핑 계속 진행`);
}
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day44-loop-basic.png" width="500" /><br/>
  > for문, while문, break/continue까지 포함된 전체 반복 흐름 스크립트 코드
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day44-loop-output.png" width="500" /><br/>
  > 배열 요소와 조건에 따라 반복 흐름이 제어되는 console 출력 결과
</p>

---

## 🛠️ Troubleshooting & 기록

- `for`문의 i가 증가하면서 배열 `temps[i]`도 자연스럽게 다음 요소로 접근하게 된다는 점을 이해함  
- `.length`는 문자열뿐 아니라 배열에도 적용되며, 배열에서는 **요소의 개수**를 반환함  
- `if (i % 2)` 대신 `i % 2 !== 0`을 사용해 **조건을 명시적으로 표현하는 습관**이 가독성에 더 유리함  
- `break`는 조건 만족 시 반복문을 즉시 중단하는데, 그 흐름을 직접 구현해보며 **제어 로직 감각이 확실히 잡힘**

---

## 💭 느낀 점

- 단순 반복이 아닌 조건을 걸어 **어떤 상황에서 중단하거나 건너뛸지 로직으로 설계**하는 게 흥미로웠고,  
  이런 흐름 설계가 진짜 개발자의 사고방식이라는 걸 체감함  
- 반복문과 배열, 조건문이 서로 연결되는 구조를 이해하면서  
  **입력 → 반복 → 조건 판단 → 출력**의 전 과정을 코드로 다뤄본 느낌이 들었고,  
  이게 바로 로직 감각을 키우는 핵심이라는 걸 확실히 느낀 날이었다


