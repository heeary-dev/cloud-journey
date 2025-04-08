# 📘 파일 압축 명령어 실습 (`zip`, `tar`)

## 🎯 오늘 학습 목표
- `zip`, `tar` 명령어의 동작 방식 및 차이점 이해
- 압축 해제, 내부 확인, 권한 포함 백업 실습
- 선택적 해제, 복원 위치 지정 등 실전 사용법 숙지

---

## 🧠 오늘 배운 개념

### 🔹 압축 포맷 이해
- `zip`: 파일 압축 및 **선택적 해제** 가능
- `tar`: 다수 파일을 하나로 묶는 **아카이브** 형식이며, 옵션 조합으로 압축도 가능

### 🔹 주요 옵션 정리

| 명령어 | 설명 |
|---|---|
| `zip sample.zip a.txt b.txt` | zip 파일 생성 |
| `unzip -l sample.zip` | 압축 내부 목록 확인 |
| `unzip sample.zip a.txt` | 특정 파일만 해제 |
| `tar -cvf file.tar` | 압축 없이 아카이브 생성 |
| `tar -zcvf file.tar.gz` | gzip 포함 압축 |
| `tar -tvf` | 내용만 확인 (해제 없음) |
| `tar -xvf` | 전체 해제 |
| `tar -xpvf` | 권한 포함 해제 |
| `-C` | 압축 해제 위치 지정 |

---

### 🔹 실습 중 사용한 명령어 요약

```
touch a.txt b.txt c.txt                   # 테스트용 파일 생성
chmod 744 a.txt                           # 권한 설정
zip sample.zip a.txt b.txt                # zip 압축
unzip sample.zip a.txt                    # 개별 해제
tar -cvf archive.tar c.txt                # tar 압축
tar -tf archive.tar                       # 내부 구조 확인
tar -cpvf backup.tar a.txt                # 권한 포함 백업
sudo tar -xpvf backup.tar -C recover/     # 권한 유지하며 복원

```

## 🧪 실습 과정 요약

1. `zip`으로 `a.txt`, `b.txt` 파일을 압축하고 `unzip -l`로 내부 구조 확인
2. `unzip sample.zip a.txt` 명령어로 특정 파일만 선택적 압축 해제
3. `tar -cvf archive.tar c.txt`로 아카이브 생성 후 `-tvf`로 구조 확인
4. `tar -xvf archive.tar`로 일반 해제, `-cpvf`로 권한 포함 백업
5. `sudo tar -xpvf backup.tar -C recover/`로 권한 보존 복원 실습

---

### ⚠️ 실수 & 깨달은 점

- `tar` 복원 시 `sudo` 없이 수행하면 **파일 권한이 복원되지 않음**
- `.DS_Store` 같은 불필요한 파일이 zip에 자동 포함됨 → `zip -x "*.DS_Store"`로 제외 가능
- `zip`은 사용이 직관적이고 유연하나, `tar`은 **백업·복원에 더 강력함**

---

### 💭 느낀 점

이번 실습을 통해 압축 명령어들이 단순한 도구가 아니라  
**시스템을 보호하고 복원하는 핵심 무기**가 될 수 있다는 걸 느꼈다.

특히 `tar -cpvf`와 `-xpvf` 조합은 단순 복사 이상의  
**퍼미션 포함 백업**을 가능하게 해주며,  
리눅스에서 운영체제를 **신뢰도 있게 관리**할 수 있다는 자신감을 줬다.





