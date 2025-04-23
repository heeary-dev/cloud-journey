# 🧪 실습 기록 - 3주차 labs.md

> 명령어 실습과 결과를 정리하는 공간입니다.

---

# ✅ Day 15 – 조건문 고급 실습

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

# ✅ Day 16 실습 - case 선택문

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

---

# ✅ Day 17 - 쉘 함수 (function) 흐름 제어 실습

## 📘 1. 개념 정리

- **쉘 함수**는 명령어를 묶어 재사용할 수 있는 구조이며 `함수명() { ... }` 형식으로 정의함  
- 함수에 인자를 전달하면 `$1`, `$2`, `$@` 등으로 받을 수 있으며, CLI 입력값이나 내부 변수 모두 가능  
- `return`은 함수 실행 결과를 **숫자 상태코드(0=성공, 1~255=실패)** 로 반환함  
- `$?`는 **직전에 실행한 명령어 또는 함수의 상태코드**를 저장하는 특별 변수  
- `exit`은 **스크립트 전체를 종료**시키는 명령으로, 중대한 오류 발생 시 사용됨  
- 실무에서는 함수를 기능별로 분리하고, `main()` 함수에서 전체 흐름을 제어하는 구조를 선호함  
- `case` 문은 **사용자 입력 명령에 따라 기능을 분기 처리**할 때 유용하게 사용됨

---

## 🧪 2. 실습 명령어

```
#!/bin/bash                                              # bash 셸 사용 선언

# 사용자 로그인 함수
login() {
  if [ "$1" = "heeary" ] && [ "$2" = "1234" ]; then      # ID와 PW가 정확한 경우
    echo "Login success"                                 # 로그인 성공 메시지 출력
    return 0                                              # 성공 상태 반환
  else
    echo "Login failed"                                  # 실패 메시지 출력
    return 1                                              # 실패 상태 반환
  fi
}

# 명령 처리 함수 (case 선택문)
handle_action() {
  read -p "Enter action (start/stop/status): " act       # 사용자 명령 입력
  case "$act" in
    start)
      echo "Service started"
      ;;
    stop)
      echo "Service stopped"
      ;;
    status)
      echo "Service is running"
      ;;
    *)
      echo "Unknown command"
      ;;
  esac
}

# 메인 함수: 전체 흐름 제어
main() {
  read -p "Enter ID: " id                                 # ID 입력
  read -p "Enter PW: " pw                                 # PW 입력
  login "$id" "$pw"                                       # 로그인 함수 호출
  if [ $? -ne 0 ]; then                                   # 로그인 실패 시
    echo "Access denied"
    exit 1
  fi

  echo "Welcome to the system"                            # 로그인 성공 후 메시지
  handle_action                                           # 기능 분기 실행
}

main                                                     # main 함수 호출
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day17-function-login-script.png" width="450"/><br/>
  > 전체 함수 기반 스크립트 작성 화면
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day17-login-success.png" width="450" height="80"/><br/>
  > 올바른 ID/PW 입력 후 로그인 성공 메시지 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day17-login-fail.png" width="450" height="80"/><br/>
  > 잘못된 ID/PW 입력 시 로그인 실패 후 스크립트 종료
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day17-action-case-run.png" width="450" height="80"/><br/>
  > 로그인 후 입력한 명령에 따라 case문이 실행됨
</p>

---

## 🛠️ Troubleshooting & 기록

- `return` 없이 함수가 끝나면 마지막 명령어의 상태코드가 전달되므로, 항상 명시적으로 `return`을 작성함  
- `$?`는 오직 **직전 명령어 또는 함수의 결과**만 나타내므로, 중간에 다른 명령어가 들어가면 값이 바뀔 수 있음  
- 실습 초기에 ID와 PW 비교 시 `=` 연산자 앞뒤에 공백이 없도록 주의해야 함 (`[ "$id" = "heeary" ]`)  
- `case` 문 내의 명령어 처리에서 `*)` 블록이 else 역할을 한다는 것을 활용함  
- `exit`을 함수 안에서 사용하면 스크립트 전체가 강제 종료되므로, 반드시 필요한 경우에만 사용함

---

## 💭 느낀 점

쉘 함수는 단순 반복을 줄이기 위한 수단이 아니라,  
**코드 흐름을 명확하게 정리하고 유지보수성을 높이기 위한 필수 구조**라는 걸 실습을 통해 체감했다.  
특히 `return`과 `$?`의 연결을 이해하니, 조건 흐름 제어가 훨씬 정교해졌다.  
실무처럼 `main()` 함수로 전체 흐름을 통제하는 구조에 익숙해지는 게 중요하다고 느꼈다.

---

# ✅ Day 18 - 함수 응용 및 심화실습

## 📘 1. 개념 정리  
- `check_input()`: 입력값이 비었는지 검사 (빈 문자열 체크)  
- `login()`: ID/PW가 맞는지 확인하여 로그인 처리  
- `handle_command()`: 사용자 명령에 따라 start/stop/status 출력  
- `main()`: 전체 흐름을 통제하는 중심 함수  
- `return`: 함수 종료와 함께 상태코드(0/1) 반환  
- `exit`: 전체 스크립트 종료, 실패 시 조건문에서 사용  
- `$?`: 직전 명령어 또는 함수의 결과 상태코드 확인  

---

## 🧪 2. 실습 명령어  

```
#!/bin/bash                                             

check_input() {
  if [ -z "$1" ] || [ -z "$2" ]; then                   
    echo "Missing ID or PW"
    return 1
  fi
  return 0
}

login() {
  if [ "$1" = "heeary" ] && [ "$2" = "1234" ]; then     
    echo "Login success"
    return 0
  else
    echo "Login failed"
    return 1
  fi
}

handle_command() {
  read -p "Enter command (start/stop/status): " cmd     
  case "$cmd" in
    start)
      echo "Service started"
      ;;
    stop)
      echo "Service stopped"
      ;;
    status)
      echo "Service is running"
      ;;
    *)
      echo "Unknown command"
      ;;
  esac
}

main() {
  read -p "Enter ID: " id                               
  read -p "Enter PW: " pw                               

  check_input "$id" "$pw"                               
  if [ $? -ne 0 ]; then
    echo "Input validation failed"
    exit 1
  fi

  login "$id" "$pw"                                     
  if [ $? -ne 0 ]; then
    echo "Access denied"
    exit 1
  fi

  echo "Welcome, $id"
  handle_command                                        
}

main
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day18-login-flow-script.png" width="450" /><br/>
  > 전체 함수 기반 스크립트 작성 화면
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day18-check-input-fail.png" width="450" height="80"/><br/>
  > ID 또는 PW가 비어 있을 때 입력 실패 메시지 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day18-login-fail.png" width="450" height="80"/><br/>
  > 잘못된 ID/PW 입력 시 로그인 실패 메시지 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day18-login-success.png" width="450" height="80"/><br/>
  > 로그인 성공 후 기능 명령 프롬프트 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day18-command-start.png" width="450" height="80"/><br/>
  > start 명령 실행 결과 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day18-command-status.png" width="450" height="80"/><br/>
  > status 명령 실행 결과 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day18-command-invalid.png" width="450" height="80"/><br/>
  > 잘못된 명령 입력 시 Unknown command 출력
</p>

---

## 🛠️ Troubleshooting & 기록  
- `check_input()` 함수에서 공백 입력 시 `-z` 조건으로 정확히 검출됨  
- 함수 내부에서 `exit`을 사용하면 전체 종료되므로 **반드시 `main()`에서만 사용**  
- `$?` 상태코드를 체크할 때 **다음 줄에 다른 명령어가 오면 오류 발생 가능**  
- `case` 문에서 `*)`는 if의 `else` 역할 → 반드시 있어야 안정적인 분기 가능

---

## 💭 느낀 점  
오늘 실습은 단순히 조건문을 쓰는 것이 아니라  
**실제 흐름을 함수로 분리하고 main으로 조립하는 구조**를 직접 체득한 시간이었다.  
특히 return → $? → exit → 흐름 분기의 연결을 구현하면서,  
단순한 명령어를 넘어서 **작동하는 프로그램을 짜는 감각**을 얻었다. 

---

# ✅ Day 19 실무함수의 흐름

## 📘 1. 개념 정리

- 쉘 함수(Function): 명령어를 묶어 재사용하는 구조 (`함수명() { ... }`)
- 인자 전달: `$1`, `$2`, `$@` 로 함수 외부에서 값을 받을 수 있음
- `return`: 함수 내부에서 숫자 상태코드 반환 (`0 = 성공`, `1~255 = 실패`)
- `exit`: 스크립트 전체 종료용 명령, 일반적으로 `main()` 함수 내에서 사용
- `$?`: 직전에 실행된 명령어 또는 함수의 종료 상태코드를 확인하는 특수 변수

## 🧪 2. 실습 명령어

```
#!/bin/bash

login() {
  read -p "Enter ID: " id
  read -p "Enter PW: " pw

  if [ "$id" = "heeary" ] && [ "$pw" = "1234" ]; then
    echo "Login success"
    return 0
  else
    echo "Login failed"
    return 1
  fi
}

grade() {
  read -p "Enter score (0~100): " score

  if [ "$score" -ge 90 ]; then
    echo "Grade A"
  elif [ "$score" -ge 80 ]; then
    echo "Grade B"
  elif [ "$score" -ge 70 ]; then
    echo "Grade C"
  else
    echo "Grade F"
  fi
}

check_user() {
  read -p "Are you a super user? (yes/no): " answer

  if [ "$answer" = "yes" ]; then
    echo "Welcome, root user"
  else
    echo "Access level: normal user"
  fi
}

main() {
  login
  if [ "$?" -ne 0 ]; then
    echo "Access denied"
    exit 1
  fi

  grade
  check_user
}

main
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day19-login-fail-exit.png" width="450" height="80"/><br/>
  > 잘못된 ID 입력 시 로그인 실패 후 Access denied 처리
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day19-login-grade-a.png" width="450" height="80"/><br/>
  > 로그인 성공 후 점수 90점 입력 → Grade A 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day19-grade-f-normal.png" width="450" height="80"/><br/>
  > 로그인 성공 후 점수 69점 입력 → Grade F, 일반 사용자 인증
</p>

---

## 🛠️ Troubleshooting & 기록

- `$pw = "1234"`처럼 변수 앞뒤 따옴표 빠지면 비교 실패 → `"$pw" = "1234"`로 수정
- `-ge 90]`처럼 비교 연산자 뒤 공백 없으면 syntax error → `-ge 90 ];` 로 공백 필수
- bash로 실행해야 `read -p`가 동작함

---

## 💭 느낀 점

오늘은 함수, 조건문, 흐름제어를 결합해서 **완전한 로그인 → 등급 확인 → 사용자 인증** 흐름을 구현해봤다.  
실행 흐름에 따라 `return`, `exit`, `$?`가 어떻게 이어지는지 실제로 써보며 완전히 이해할 수 있었다.  

---

# ✅Day 20 함수 예외 처리 보강

## 📘 1. 개념 정리

- `-z "$변수"`: 값이 비었는지 검사 (입력값 유효성 체크에 사용)
- `return`: 함수 내부 종료 및 상태코드 반환 (0 = 성공, 1~255 = 실패)
- `exit`: 스크립트 전체 종료, 반드시 명시적인 상태코드와 함께 사용
- `$?`: 직전에 실행된 명령어나 함수의 종료 상태코드 확인

---

## 🧪 2. 실습 명령어

```
#!/bin/bash                                        # bash 셸 사용 선언

login() {
  read -p "Enter ID: " id                          # 사용자 ID 입력
  read -p "Enter PW: " pw                          # 사용자 PW 입력

  if [ -z "$id" ] || [ -z "$pw" ]; then            # 입력값 비어 있는지 검사
    echo "ID or PW cannot be empty"               # 경고 메시지
    return 1
  fi

  if [ "$id" = "heeary" ] && [ "$pw" = "1234" ]; then
    echo "Login success"                           # 로그인 성공
    return 0
  else
    echo "Login failed"                            # 로그인 실패
    return 1
  fi
}

grade() {
  read -p "Enter your score: " score               # 점수 입력

  if [ -z "$score" ]; then
    echo "Score is required"                       # 점수 입력 안했을 경우
    return 1
  fi

  if [ "$score" -ge 90 ]; then
    echo "Grade A"
  elif [ "$score" -ge 80 ]; then
    echo "Grade B"
  elif [ "$score" -ge 70 ]; then
    echo "Grade C"
  else
    echo "Grade F"
  fi
}

main() {
  login
  if [ $? -ne 0 ]; then                            # 로그인 실패 시 종료
    exit 1
  fi

  grade                                            # 점수 평가
}

main
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day20-empty-id.png" width="450" height="80"/><br/>
  > ID 또는 PW 입력 없이 Enter 시 오류 메시지 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day20-login-success-grade-b.png" width="450" height="80"/><br/>
  > 로그인 성공 후 점수 85 입력 → Grade B 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day20-grade-empty.png" width="450" height="80"/><br/>
  > 로그인 성공 후 점수 입력 없이 Enter 시 오류 메시지 출력
</p>

---

## 🛠️ Troubleshooting & 기록

- `-z`는 문자열이 비었는지 판단할 때 가장 기본적인 안전 장치
- `$?`는 반드시 `return` 직후에만 확인해야 신뢰성 확보 가능
- `exit`는 항상 숫자 상태코드를 명시하여 종료 원인 전달
- 로그인/점수 입력 시, 유효성 검사를 통해 흐름이 안정적으로 제어됨

---

## 💭 느낀 점

오늘 실습을 통해 입력값이 비었을 때 스크립트가 어떻게 오작동할 수 있는지 체감했다.  
단순한 조건문 하나만으로도 스크립트를 더 견고하게 만들 수 있다는 걸 알게 되었고,  
현업에서 왜 기본적인 유효성 검사 패턴을 강조하는지 이해가 됐다.





