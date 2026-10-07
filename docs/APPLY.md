# 처음 적용하는 분을 위한 패치 안내

**순서: 패치 ZIP 받기 → 압축 풀기 → 프로그램 준비 → 원본 BIN 복사 → 명령 실행 → CUE로 게임 실행.**

아래는 컴퓨터에서 패치를 적용하는 방법입니다.
원본과 배포 파일은 이름을 그대로 사용합니다. 원본은 복사해서 사용하며 적용 결과는 별도 `Korean` 폴더에 생성됩니다.

## 1. 적용할 원본 확인

대상은 **PlayStation 일본 보급판(Fukyuuban / SLPS-03015)**입니다.
원본 BIN 파일명과 크기가 아래와 같은지 확인합니다.

```text
Tantei Jinguuji Saburou - Tomoshibi ga Kienu Ma ni (Japan) (Fukyuuban).bin
```

| 항목 | 원본 BIN 값 |
|---|---|
| 크기 | **738,819,648바이트** |
| SHA256 | `cc44e8c81ae0f379c2adfc07fdd5dec280e8efb85217115567c8c7f9838ae519` |
| SHA1 | `ed49bcf5cb969e4719a11ffeaadd5c42d5357664` |
| MD5 | `08a8e4f588360c40289cc43d488eb6cb` |
| CRC32 | `f708a694` |

**파일명이 같아도 내용이 다를 수 있으므로 SHA256을 기준으로 확인합니다.**
SHA256은 파일 내용을 구별하는 값입니다. 아래 적용 프로그램이 이 값을 자동으로 검사하며, 원본이 다르면 적용을 중단합니다.
일반판이나 이미 한글 패치된 BIN은 이 패치의 적용 대상이 아닙니다.

원본 CUE의 참고 정보:

```text
Tantei Jinguuji Saburou - Tomoshibi ga Kienu Ma ni (Japan) (Fukyuuban).cue
```

- 크기: 136바이트.
- SHA256: `7fb6aff76102a2534693ea3fea00b14bbe6cc84c1e948318713c81fdee8c1356`.
- 트랙: 단일 `TRACK 01 MODE2/2352`.

패치에 입력하는 파일은 **BIN**입니다. CUE는 적용 후 게임을 실행할 때 사용합니다.

## 2. 패치 ZIP 다운로드와 압축 풀기

GitHub 저장소의 **Releases → v0.8 → Assets**에서 다음 파일을 받습니다.

```text
Tomoshibi_Fukyuuban_KO_v0.8.zip
```

이름 끝이 `.xdelta`인 파일 하나만 받으면 적용 스크립트가 없으므로 위 ZIP을 받으세요.
`Source code (zip)`은 GitHub가 자동으로 만드는 문서 묶음이며 패치 ZIP이 아닙니다.

다운로드한 ZIP의 **압축을 모두 풉니다**. Windows에서는 ZIP을 오른쪽 클릭해 **모두 추출**을 선택합니다.
압축을 푼 폴더에 `apply_patch.py`, `manifest.json`, `Tomoshibi_Fukyuuban_KO_v0.8.xdelta`이 있는지 확인합니다.
함께 들어 있는 CUE, 설명서, 해시 목록, `LICENSES` 폴더도 그대로 둡니다.

작업할 드라이브에는 원본 복사본과 결과 파일을 위해 **3GB 정도의 여유 공간을 권장**합니다.

## 3. Windows에서 적용

### 3-1. Python 준비

이미 Python 3.9 이상이 설치되어 있다면 다음 확인 단계로 넘어갑니다.
설치하지 않았다면 [Python 공식 Windows 다운로드 페이지](https://www.python.org/downloads/windows/)에서
**Python install manager**를 받아 실행하고 **Install(설치)**을 선택합니다.
설치 후 열려 있던 명령 창은 닫고 새로 엽니다.
[공식 설치 안내](https://docs.python.org/3/using/windows.html)

### 3-2. xdelta3 준비

[xdelta3 3.2.1 공식 다운로드](https://github.com/jmacd/xdelta/releases/tag/v3.2.1)의 **Assets**에서
일반적인 Intel/AMD 64비트 Windows PC는 **`xdelta3-3.2.1-windows-x86_64.zip`**을 받습니다.
ARM 기반 Windows PC는 `xdelta3-3.2.1-windows-arm64.zip`을 사용합니다.

이 ZIP도 압축을 풉니다. 안쪽 폴더에 있는 **`xdelta3.exe`**를
패치 ZIP을 풀어 놓은 폴더, 즉 **`apply_patch.py`와 같은 위치**에 복사합니다.
실행 파일을 두 번 클릭할 필요는 없습니다.

### 3-3. 원본 BIN 복사

다음 원본 BIN을 패치 폴더에 **파일명을 그대로 유지해 복사**합니다.

```text
Tantei Jinguuji Saburou - Tomoshibi ga Kienu Ma ni (Japan) (Fukyuuban).bin
```

패치 폴더에는 최소한 다음 파일들이 같은 위치에 있어야 합니다.

```text
apply_patch.py
manifest.json
Tomoshibi_Fukyuuban_KO_v0.8.xdelta
xdelta3.exe
Tantei Jinguuji Saburou - Tomoshibi ga Kienu Ma ni (Japan) (Fukyuuban).bin
```

### 3-4. 명령을 입력할 창 열기

탐색기에서 패치 폴더를 엽니다. 위쪽 **주소 표시줄**을 클릭하고
`powershell`을 입력한 뒤 Enter를 누릅니다. 열린 창에서 다음 명령을 입력합니다.

```powershell
py -3 --version
```

`Python 3.x.x`가 나오면 준비되었습니다. 버전은 **3.9 이상**이어야 합니다.
처음 실행할 때 Python 추가 설치 안내가 나오면 설치를 마치고 같은 명령을 다시 실행합니다.

### 3-5. 패치 실행

아래 **한 줄 전체를 복사**해 같은 창에 붙여 넣고 Enter를 누릅니다.
파일명의 공백과 따옴표도 그대로 복사합니다.

```powershell
py -3 .\apply_patch.py "Tantei Jinguuji Saburou - Tomoshibi ga Kienu Ma ni (Japan) (Fukyuuban).bin" --xdelta .\xdelta3.exe --output-dir Korean
```

처리가 끝날 때까지 창을 닫지 않습니다. 완료 확인 방법은 아래 5번에 있습니다.

## 4. macOS에서 적용

### 4-1. Python과 xdelta3 준비

Python이 없다면 [Python 공식 macOS 다운로드 페이지](https://www.python.org/downloads/macos/)에서
Python 3의 **macOS installer**를 받아 설치합니다.

[xdelta3 3.2.1 공식 다운로드](https://github.com/jmacd/xdelta/releases/tag/v3.2.1)에서
Apple M1·M2·M3·M4 등 Apple Silicon Mac은 **`xdelta3-3.2.1-macos-arm64.tar.gz`**,
Intel Mac은 **`xdelta3-3.2.1-macos-x86_64.tar.gz`**를 받습니다.
압축을 풀고 안쪽 폴더의 **`xdelta3`** 파일을 `apply_patch.py`와 같은 위치에 복사합니다.

원본 BIN도 이름을 유지해 같은 패치 폴더에 복사합니다.

### 4-2. 패치 폴더에서 터미널 열기

터미널 앱을 엽니다. `cd`를 입력하고 **공백 한 칸**을 넣은 뒤,
Finder의 패치 폴더를 터미널 창으로 끌어다 놓고 Enter를 누릅니다.
이제 명령은 그 폴더에서 실행됩니다.

다음 확인 명령을 실행합니다.

```sh
python3 --version
```

`Python 3.x.x`가 나오며 버전이 3.9 이상이면 아래 명령을 한 줄씩 실행합니다.

```sh
chmod +x ./xdelta3
python3 ./apply_patch.py "Tantei Jinguuji Saburou - Tomoshibi ga Kienu Ma ni (Japan) (Fukyuuban).bin" --xdelta ./xdelta3 --output-dir Korean
```

macOS가 실행을 차단하면 표시된 메시지를 확인하고 오류 제보에 첨부합니다.

## 5. 완료 확인과 게임 실행

명령 창에 다음 문구가 표시되면 **패치 적용과 결과 파일의 해시 검사까지 완료**된 것입니다.

```text
패치 적용 및 전체 SHA256 확인 완료.
```

패치 폴더 안에 **`Korean` 폴더**가 생성되며 다음 두 파일이 들어 있습니다.

```text
Tantei Jinguuji Saburou - Tomoshibi ga Kienu Ma ni (Japan) (Fukyuuban) (Korean).bin
Tantei Jinguuji Saburou - Tomoshibi ga Kienu Ma ni (Japan) (Fukyuuban) (Korean).cue
```

1. 두 파일을 같은 폴더에 둡니다.
2. 에뮬레이터의 게임 열기 메뉴에서 **위 CUE 파일**을 선택합니다.
3. 다른 기기로 옮길 때도 BIN과 CUE **두 파일을 함께** 복사합니다.

결과 파일의 이름은 그대로 유지합니다.

| 결과 파일 | 크기 | SHA256 |
|---|---:|---|
| BIN | 750,349,152바이트 | `e59ae345bf56a9b660a448c1341c49c4d4fd86334fadd0e71c0a39f476f1f232` |
| CUE | 142바이트 | `b060fc3f94e0a45b58b2e4c4ee5f84482697b04271ee7c22efd54b838fc84d68` |

## 6. 원본 해시를 직접 확인하려면

위 3-4 또는 4-2의 방법으로 원본 BIN이 들어 있는 폴더에서 명령 창을 엽니다.

**Windows PowerShell**

```powershell
Get-FileHash -Algorithm SHA256 "Tantei Jinguuji Saburou - Tomoshibi ga Kienu Ma ni (Japan) (Fukyuuban).bin"
```

**macOS 터미널**

```sh
shasum -a 256 "Tantei Jinguuji Saburou - Tomoshibi ga Kienu Ma ni (Japan) (Fukyuuban).bin"
```

출력된 64자리 값이 다음과 같으면 지정 원본과 일치합니다. 영문 대소문자는 관계없습니다.

```text
cc44e8c81ae0f379c2adfc07fdd5dec280e8efb85217115567c8c7f9838ae519
```

## 7. 실패했을 때 확인할 것

| 보이는 메시지 또는 현상 | 해결 방법 |
|---|---|
| `py` 또는 `python3`를 찾지 못함 | Python 설치를 확인하고 명령 창을 닫았다가 새로 엽니다. |
| `can't open file` / `apply_patch.py`가 없음 | ZIP을 모두 풀었는지, `apply_patch.py`가 있는 폴더에서 창을 열었는지 확인합니다. |
| 원본 BIN을 찾지 못함 / `No such file or directory` | 원본 BIN을 같은 폴더에 복사했는지, 실제 파일명과 명령의 파일명이 일치하는지 확인합니다. 이름을 바꿀 필요는 없습니다. |
| `Source BIN file size mismatch` / `Source BIN SHA256 mismatch` | 지정 원본과 다른 파일입니다. 위 원본 크기와 SHA256을 확인합니다. 이름만 같아서는 적용되지 않습니다. |
| `xdelta3 executable was not found` | Windows의 `xdelta3.exe` 또는 macOS의 `xdelta3`를 `apply_patch.py` 옆에 넣었는지 확인합니다. |
| `Patch` 또는 `CUE`의 해시 불일치 | 배포 ZIP을 다시 받아 새 폴더에 모두 풉니다. |
| `already exists` | `Korean` 폴더에 이미 결과가 있습니다. 재적용하려면 명령 끝의 `--output-dir Korean`을 `--output-dir Korean_new`로 바꿔 새 폴더에 출력합니다. 파일명은 유지됩니다. |
| 실행 파일 형식 또는 아키텍처 오류 | xdelta3 다운로드가 자신의 운영체제와 Intel/AMD·ARM 종류에 맞는지 확인합니다. |

해결되지 않으면 **명령 창 전체 메시지**, 운영체제와 프로그램 버전을 오류 제보에 붙여 주세요.

## 확인한 적용 환경

기존 패키지는 macOS / Python 3.9 / xdelta3 3.1.0에서 실제 적용을 검증했습니다.
공식 xdelta3 3.2.1의 macOS arm64 실행 파일로도 패키지를 적용해 전체 결과 BIN/CUE 해시 일치를 확인했습니다.
Windows 절차는 공식 설치 안내와 배포 파일 구성을 확인해 작성했으며 Windows에서 직접 실행한 검증은 아직 없습니다.

## 다운로드한 ZIP 자체의 해시

```text
Tomoshibi_Fukyuuban_KO_v0.8.zip
SHA256: e7fd4dffa8a61742bf408db74a8687a1e03d1d36dc00d8fd93702b8ff67a6218
```

[처음으로](../README.md)
