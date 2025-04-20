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

```bash
# check_user.sh
#!/bin/bash
read -p "이름을 입력하세요: " name
if [ "$name" = "heeary" ]; then
  echo "어서 와, $name 님!"
fi

# check_empty.sh
#!/bin/bash
read -p "이름을 입력하세요: " name
if [ -z "$name" ]; then
  echo "입력값이 없습니다"
else
  echo "입력한 이름: $name"
fi

# login_auth.sh
#!/bin/bash
read -p "아이디를 입력하세요: " id
read -p "비밀번호를 입력하세요: " pw
if [[ "$id" = "heeary" && "$pw" = "1234" ]]; then
  echo "로그인 성공"
else
  echo "로그인 실패"
fi

# grade_check.sh
#!/bin/bash
read -p "점수를 입력하세요: " score
if [ "$score" -ge 90 ]; then
  echo "A학점"
elif [ "$score" -ge 80 ]; then
  echo "B학점"
elif [ "$score" -ge 70 ]; then
  echo "C학점"
else
  echo "F학점"
fi

# admin_check.sh (중첩 if)
#!/bin/bash
user="heeary"
role="admin"
if [ "$user" = "heeary" ]; then
  if [ "$role" = "admin" ]; then
    echo "중첩 if: 관리자 확인 완료"
  fi
fi

# admin_check.sh (복합 조건)
#!/bin/bash
user="heeary"
role="admin"
if [[ "$user" = "heeary" && "$role" = "admin" ]]; then
  echo "복합 조건: 관리자 확인 완료"
fi

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day15-check-user-true.png" width="450" height="80"/>
</p>
> "heeary" 입력 시 환영 메시지가 출력된다

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day15-check-empty-warning.png" width="450" height="80"/>
</p>
> 아무 입력 없이 엔터 → "입력값이 없습니다" 출력 확인

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day15-login-success.png" width="450" height="80"/>
</p>
> 올바른 id/pw 입력 시 로그인 성공

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day15-login-fail.png" width="450" height="80"/>
</p>
> 틀린 입력 시 로그인 실패

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day15-grade-b.png" width="450" height="80"/>
</p>
> 85점 입력 시 B학점 출력

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day15-grade-f.png" width="450" height="80"/>
</p>
> 67점 입력 시 F학점 출력

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day15-nested-if.png" width="450" height="80"/>
</p>
> 중첩 조건으로 관리자 확인 메시지 출력

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day15-compound-if.png" width="450" height="80"/>
</p>
> 복합 조건으로 같은 결과를 더 간단히 표현

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



