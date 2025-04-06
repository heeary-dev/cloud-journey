# 🧪 실습 기록 - 2주차 labs.md

> 명령어 실습과 결과를 정리하는 공간입니다.

---

## ✅ Day8 학습 주제  

- `find` 명령어 활용 심화 실습
- `-name`, `-delete`, `-exec`, `-print0 | xargs -0` 방식 비교
- 공백 포함 파일 처리 실습 포함

---

## 📘 1. 개념 정리  
- `find`는 조건에 맞는 파일/디렉토리를 검색하는 명령어
- `-name "*.확장자"`로 원하는 형식의 파일만 필터링 가능
- `-delete`는 `find` 자체 기능으로 삭제 수행
- `-exec`은 외부 명령을 각각 실행 (느리지만 유연함)
- `-print0` + `xargs -0`은 공백이 있는 파일 처리에 유리

---

## 🧪 2. 실습 명령어  

```
mkdir find-test                     # 실습용 디렉토리 생성
cd find-test                        # 디렉토리로 이동
touch a.log b.log c.txt "my log.log"   # 다양한 파일 생성
find . -name "*.log"               # .log 파일 검색
find . -name "*.log" -delete       # .log 파일 전체 삭제
touch a.log b.log "my log.log"     # 다시 .log 파일 생성
find . -name "*.log" -print0 | xargs -0 rm  # xargs로 정확 삭제
touch a.log b.log                  # .log 다시 생성
find . -name "*.log" -exec rm {} \;     # exec 방식 삭제
```

---

## 🖼️ 실습 스크린샷

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day8-init-files.png" width="450" height="80"/><br/>
  > 다양한 확장자 & 공백 포함된 파일 생성 확인
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day8-find-log.png" width="450" height="80"/><br/>
  > find 명령어로 `.log` 파일만 필터링 결과 출력
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day8-after-delete.png" width="450" height="80"/><br/>
  > -delete 옵션으로 .log 파일이 삭제된 상태
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day8-before-xargs.png" width="450" height="80"/><br/>
  > 다시 공백 포함된 파일 포함하여 .log 파일 생성됨
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day8-after-xargs.png" width="450" height="80"/><br/>
  > xargs -0 방식으로 공백 포함된 파일까지 정확히 삭제됨
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day8-before-exec.png" width="450" height="80"/><br/>
  > 마지막 exec 실습 전, 파일 재생성 상태
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/heeary-dev/cloud-journey/main/images/day8-after-exec.png" width="450" height="80"/><br/>
  > exec 방식으로 모든 .log 파일 삭제 완료
</p>

---

## 🛠️ Troubleshooting & 기록

- 공백이 포함된 파일명은 기본 `xargs`로 처리 시 오류 발생 가능  
  → `-print0 | xargs -0` 조합을 사용해 정확히 처리해야 함
- `-exec`은 한 파일씩 실행되므로 많은 파일에는 비효율적일 수 있음
- `-delete`는 빠르지만 되돌릴 수 없어 주의 필요

---

## 💭 느낀 점

이번 실습은 단순 명령어 암기를 넘어서,  
**“파일 시스템을 실제로 제어해보는 감각”**을 길렀다고 느꼈다.  

공백 파일은 그동안 신경도 안 썼지만,  
`xargs -0` 같은 처리법을 통해 실무에서 필요한 세밀한 제어법을 배웠다.  
