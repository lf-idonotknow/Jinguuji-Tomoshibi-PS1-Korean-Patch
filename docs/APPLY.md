# 탐정 진구지 사부로: 등불이 꺼지기 전에 — 한글 패치 적용 방법

원본 일본 보급판 BIN과 컴퓨터를 준비하세요. 아래에서 파일을 선택하고 버튼을 눌러 적용할 수 있습니다.

## 1. 패치 적용

1. [한글 패치 ZIP 다운로드](https://github.com/lf-idonotknow/Jinguuji-Tomoshibi-PS1-Korean-Patch/releases/download/v0.8/Tomoshibi_Fukyuuban_KO_v0.8.zip) 후 압축을 모두 풉니다. `Source code (zip)`은 받지 않습니다.
2. [Windows용 Delta Patcher 다운로드](https://github.com/marco-calautti/DeltaPatcher/releases/download/v3.1.6/windows_bin_x86_64.zip) 후 압축을 풀고 `DeltaPatcher.exe`를 실행합니다. Mac에서는 [Mac용 다운로드](https://github.com/marco-calautti/DeltaPatcher/releases/download/v3.1.6/macos11%2B_bin_universal.zip) 후 `DeltaPatcher.app`을 실행합니다.
3. `Original file:` 오른쪽 폴더 버튼을 눌러 원본 일본 보급판 BIN을 선택합니다.
4. `XDelta patch:` 오른쪽 폴더 버튼을 눌러 패치 ZIP에서 꺼낸 `Tomoshibi_Fukyuuban_KO_v0.8.xdelta`를 선택합니다.
5. 톱니바퀴 버튼을 눌러 `Backup original file`을 체크합니다. `Checksum validation`도 체크된 상태로 둡니다.
6. `Apply patch`를 누릅니다. `Patch successfully applied!`가 나오면 적용이 끝난 것입니다. 원본과 같은 폴더에 이름 끝이 `PATCHED.bin`인 한글판 파일이 생깁니다.
7. 새로 생긴 `PATCHED.bin`의 이름을 아래 한글판 BIN 이름으로 맞춘 뒤, 패치 ZIP에서 꺼낸 한글판 CUE를 같은 폴더에 넣습니다. 에뮬레이터에서 CUE 파일을 열면 됩니다.

한글판 BIN 이름 — 아래 한 줄을 복사해서 사용하세요.

```text
Tantei Jinguuji Saburou - Tomoshibi ga Kienu Ma ni (Japan) (Fukyuuban) (Korean).bin
```

함께 둘 한글판 CUE

```text
Tantei Jinguuji Saburou - Tomoshibi ga Kienu Ma ni (Japan) (Fukyuuban) (Korean).cue
```

Windows에서 이름을 맞추기 전에 탐색기의 보기 → 표시 → 파일 확장명을 켜세요.
Windows 10에서는 보기 → 파일 확장명을 체크합니다. 이름 끝이 `.bin.bin`이 되지 않도록 확인하세요.
다른 기기로 게임을 옮길 때도 한글판 BIN과 CUE 두 파일을 함께 복사하세요.

`Backup original file`을 체크하면 원본은 남고 한글판이 별도로 생성됩니다.
패치 적용과 결과 파일을 위한 여유 공간은 2GB 이상을 권장합니다.

## 2. 잘 안 될 때

| 현상 | 확인할 것 |
|---|---|
| 원본 또는 패치가 선택되지 않음 | ZIP의 압축을 먼저 모두 풀고, BIN과 `.xdelta`를 각각 선택하세요. |
| `The file you are trying to patch is not the right one.` | 아래 원본 판본과 크기를 확인하세요. 이미 패치된 파일에는 다시 적용하지 않습니다. `Checksum validation`은 체크된 상태로 유지하세요. |
| 성공했는데 게임을 열 수 없음 | 새로 생성된 BIN의 이름과 위 한글판 BIN 이름이 같은지 확인하고, CUE를 같은 폴더에 넣어 CUE를 여세요. |
| Mac에서 앱을 열 수 없다는 안내가 나옴 | [Delta Patcher 공식 배포 페이지](https://github.com/marco-calautti/DeltaPatcher/releases/tag/v3.1.6)에서 받은 Mac용 파일인지 확인하세요. 문제가 계속되면 표시된 안내를 오류 제보에 첨부해 주세요. |

해결되지 않으면 오류 메시지 전체와 운영체제, 사용한 프로그램 버전을 [오류 제보](https://github.com/lf-idonotknow/Jinguuji-Tomoshibi-PS1-Korean-Patch/issues/new/choose)에 적어 주세요.

## 3. 적용할 원본의 상세 정보

| 항목 | 적용할 원본 BIN |
|---|---|
| 판본 | PlayStation 일본 보급판 / Fukyuuban / SLPS-03015 |
| 파일명 | `Tantei Jinguuji Saburou - Tomoshibi ga Kienu Ma ni (Japan) (Fukyuuban).bin` |
| 크기 | 738,819,648바이트 |
| SHA256 | `cc44e8c81ae0f379c2adfc07fdd5dec280e8efb85217115567c8c7f9838ae519` |

파일명만 같아서는 같은 원본이라고 판단할 수 없습니다. 해시는 파일의 내용을 식별하는 값입니다.
일반판이나 이미 한글 패치를 적용한 파일에는 사용할 수 없습니다.

추가 원본 해시:

- SHA1: `ed49bcf5cb969e4719a11ffeaadd5c42d5357664`
- MD5: `08a8e4f588360c40289cc43d488eb6cb`
- CRC32: `f708a694`
- 디스크 구성: 단일 트랙 `MODE2/2352`.

## 4. 적용 결과를 확인할 때

| 파일 | 크기 | SHA256 |
|---|---:|---|
| 한글판 BIN | 750,349,152바이트 | `e59ae345bf56a9b660a448c1341c49c4d4fd86334fadd0e71c0a39f476f1f232` |
| 한글판 CUE | 142바이트 | `b060fc3f94e0a45b58b2e4c4ee5f84482697b04271ee7c22efd54b838fc84d68` |

macOS에서 Delta Patcher 3.1.6으로 실제 적용하고 결과 BIN의 전체 SHA256을 확인했습니다.
Windows용 파일의 배포 구성은 확인했으며, Windows에서의 직접 실행 검증은 아직 하지 않았습니다.

[처음으로](../README.md)
