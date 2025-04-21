# 🧪 실습 기록 - 3주차 labs.md

> 명령어 실습과 결과를 정리하는 공간입니다.

---

# 🧪 Day 15 – 조건문 고급 실습

---

## 📘 1. 개념 정리  
- `if`, `elif`, `else` 조건문 구조로 분기 제어 가능  
- `&&`, `||` 연산자를 사용하면 복합 조건을 한 줄로 표현 가능  
- 중첩 if는 조건문 안에 또 다른 조건문을 넣어 **단계적 검사**를 수행함  
- `-z`, `!`, `!=` 등 부정 조건 표현을 통해 예외적인 흐름 제어 가능  
- `"변수"` 형태로 조건문 내 비교 시 **공백, Null값에 대비한 안정성 확보** 필요

---

## 🧪 2. 실습 명령어  

```
# check_user.sh
#!/bin/bash
read -p "what is your name: " name
if [ "$name" = "heeary" ]; then
  echo "hi, $name 님!"
fi

# check_empty.sh
#!/bin/bash
read -p "what is your name: " name
if [ -z "$name" ]; then
  echo "Input value not  found"
else
  echo "name enterd: $name"
fi

# login_auth.sh
#!/bin/bash
read -p "please enter your ID: " ID
read -p "please enter your PW: " PW
if [[ "$ID" = "heeary" && "$PW" = "1234" ]]; then
  echo "Login successful"
else
  echo "Login faild"
fi

# grade_check.sh
#!/bin/bash
read -p "please enter your score: " score
if [ "$score" -ge 90 ]; then
  echo "A grade"
elif [ "$score" -ge 80 ]; then
  echo "B grade"
elif [ "$score" -ge 70 ]; then
  echo "C grade"
else
  echo "F grade"
fi

# admin_check.sh (중첩 if)
#!/bin/bash
user="heeary"
role="admin"
if [ "$user" = "heeary" ]; then
  if [ "$role" = "admin" ]; then
    echo "overlapping if: administrator verification completed"
  fi
fi

# admin_check.sh (복합 조건)
#!/bin/bash
user="heeary"
role="admin"
if [[ "$user" = "heeary" && "$role" = "admin" ]]; then
  echo "compound conditions: administrator verification completed"
fi
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day15-check-user-true.png" width="450" height="80"/><br/>
  > "heeary" 입력 시 환영 메시지가 출력된다
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day15-check-empty-warning.png" width="450" height="80"/><br/>
  > 아무 입력 없이 엔터 → "입력값이 없습니다" 출력 확인
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day15-login-success.png" width="450" height="80"/><br/>
  > 올바른 id/pw 입력 시 로그인 성공
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day15-login-fail.png" width="450" height="80"/><br/>
  > 틀린 입력 시 로그인 실패
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day15-grade-b.png" width="450" height="80"/><br/>
  > 85점 입력 시 B학점 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day15-grade-f.png" width="450" height="80"/><br/>
  > 67점 입력 시 F학점 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day15-nested-if.png" width="450" height="80"/><br/>
  > 중첩 조건으로 관리자 확인 메시지 출력
</p>


<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day15-compound-if.png" width="450" height="80"/><br/>
  > 복합 조건으로 같은 결과를 더 간단히 표현
</p>

---

## 🛠️ Troubleshooting & 기록

- `[ "$변수" = "값" ]` 구조에서 공백 유의: 반드시 양쪽 띄어쓰기 필요
- `-z "$변수"`는 빈 문자열 체크 시 매우 유용함
- `[[ ... && ... ]]` 복합 조건 시에는 `[[ ]]`로 반드시 감싸야 정상 작동
- `if-elif-else` 구조는 위에서부터 순차 평가되므로, 조건 순서 중요

---

## 💭 느낀 점

오늘 실습을 통해 `if`, `elif`, `else`, `&&`, `-z`, 중첩 등 다양한 조건문 구조를 실제로 작성해보면서  
단순 조건뿐 아니라 흐름 제어 능력이 생긴 느낌이 들었다.  
특히 중첩 구조와 복합 조건의 차이를 **직접 비교**해보며 어떤 상황에 적합한지 체감할 수 있었다.

---

## 🧪 Day 16 실습 - case 선택문

---

## 📘 1. 개념 정리

- `case` 조건문은 단일 변수의 여러 값 분기 처리를 간결하게 할 수 있는 구조이다.
- `*` 패턴은 기본 선택지 또는 예외 처리를 위한 분기로 자주 쓰인다.
- 쉘에서 `*`는 문맥에 따라 연산자가 아닌 패턴으로 해석될 수 있어 `\*`처럼 이스케이프 필요하다.
- 사용자 입력값 분기처리에 매우 유용하며 `read`와 함께 자주 쓰인다.

---

## 🧪 2. 실습 명령어

```
# select_menu.sh
#!/bin/bash
read -p "Enter command (start/stop/status): " cmd

case "$cmd" in
  start)
    echo "Starting service..."
    ;;
  stop)
    echo "Stopping service..."
    ;;
  status)
    echo "Checking service status..."
    ;;
  *)
    echo "Unknown command."
    ;;
esac

# calculator.sh
#!/bin/bash
read -p "Enter first number: " num1
read -p "Enter second number: " num2
read -p "Enter operator (+ - * /): " op

case "$op" in
  +)
    echo "Result: $((num1 + num2))"
    ;;
  -)
    echo "Result: $((num1 - num2))"
    ;;
  \*)
    echo "Result: $((num1 * num2))"
    ;;
  /)
    echo "Result: $((num1 / num2))"
    ;;
  *)
    echo "Invalid operator."
    ;;
esac

# multi_action.sh
#!/bin/bash

echo "1. Say Hello"
echo "2. Show Date"
echo "3. Exit"
read -p "Choose an option (1/2/3): " choice

case "$choice" in
  1)
    echo "Hello!"
    ;;
  2)
    date
    ;;
  3)
    echo "Exiting..."
    ;;
  *)
    echo "Invalid choice."
    ;;
esac
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day16-select-start.png" width="450" height="80"/><br/>
  > start 입력 시 서비스 시작 메시지 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day16-select-unknown.png" width="450" height="80"/><br/>
  > 알 수 없는 명령 입력 시 경고 메시지 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day16-calc-add.png" width="450" height="80"/><br/>
  > 덧셈 수행 결과 출력 (3 + 5)
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day16-calc-divide.png" width="450" height="80"/><br/>
  > 나눗셈 수행 결과 출력 (10 / 2)
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day16-choice-greeting.png" width="450" height="80"/><br/>
  > 1번 선택 시 인사 메시지 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day16-choice-date.png" width="450" height="80"/><br/>
  > 2번 선택 시 현재 날짜 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day16-choice-wrong.png" width="450" height="80"/><br/>
  > 잘못된 번호 선택 시 에러 메시지 출력
</p>

---

## 🛠️ Troubleshooting & 기록

- `case` 문에서 `*` 패턴을 그대로 사용할 경우 모든 값에 매칭되기 때문에  
  곱셈 연산자인 `*`을 비교 값으로 사용할 때는 `\*`처럼 이스케이프 처리 필요함
- `*`는 산술 연산자(`$((a * b))`)로 사용될 경우 이스케이프가 필요하지 않음
- 쉘에서 패턴으로 인식되지 않도록 보호할 때는 따옴표 또는 이스케이프 문자로 감싸야 함

---

## 💭 느낀 점

처음으로 `case` 선택문을 사용해 보면서  
`if-elif`보다 훨씬 **선택지가 명확한 분기 처리**에 적합하다는 걸 느꼈다.  
특히 사용자 입력을 받아 메뉴처럼 처리할 수 있어  
실제 프로그램처럼 만들 수 있다는 게 흥미로웠고,  
`*` 패턴이 **문맥에 따라 다르게 작동**한다는 점에서  
쉘의 해석 방식에 대해 더 깊이 생각해볼 수 있었다.




