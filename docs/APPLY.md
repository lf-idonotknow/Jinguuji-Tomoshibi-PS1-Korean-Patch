# 패치 적용 방법

## 다운로드

저장소의 **Releases → v0.8 → Assets**에서 `Tomoshibi_Fukyuuban_KO_v0.8.zip`을 다운로드합니다.
`Source code (zip)`은 패치가 들어 있는 파일이 아닙니다.
ZIP 전체를 압축 해제하며 파일의 상대 위치를 유지합니다.

## 준비물

- 자신의 원본 일본 보급판 BIN/CUE.
- Python 3.9 이상.
- [xdelta3 공식 배포](https://github.com/jmacd/xdelta/releases)의 실행 파일.

원본 BIN 크기는 **738,819,648바이트**이며 SHA256은 다음과 같습니다.

```text
cc44e8c81ae0f379c2adfc07fdd5dec280e8efb85217115567c8c7f9838ae519
```

원본 파일 이름보다 전체 바이트의 해시를 기준으로 검사합니다.
적용 스크립트는 원본, 패치, CUE의 해시와 생성된 BIN의 전체 해시를 검사합니다.

## 적용

ZIP을 푼 폴더에서 실행합니다.

```sh
python3 apply_patch.py "Tantei Jinguuji Saburou - Tomoshibi ga Kienu Ma ni (Japan) (Fukyuuban).bin" --output-dir "Korean"
```

원본이 다른 폴더에 있으면 따옴표 안을 원본 BIN의 전체 경로로 바꿉니다.
Windows에서 Python 실행 명령이 `py`라면 `python3` 대신 `py -3`를 사용합니다.
`xdelta3`가 PATH에 없으면 `--xdelta "실행 파일의 전체 경로"`를 추가합니다.
Windows 적용 안내는 제공하지만 실제 적용 검사는 macOS에서 수행했습니다.

## 적용 결과

```text
Tantei Jinguuji Saburou - Tomoshibi ga Kienu Ma ni (Japan) (Fukyuuban) (Korean).bin
Tantei Jinguuji Saburou - Tomoshibi ga Kienu Ma ni (Japan) (Fukyuuban) (Korean).cue
```

두 파일은 `Korean` 폴더에 생성됩니다. 에뮬레이터에서 CUE를 엽니다.
버전은 패치 이름에만 들어가며 적용 후 BIN/CUE 이름은 고정입니다.

| 파일 | 크기 | SHA256 |
|---|---:|---|
| BIN | 750,349,152바이트 | `e59ae345bf56a9b660a448c1341c49c4d4fd86334fadd0e71c0a39f476f1f232` |
| CUE | 142바이트 | `b060fc3f94e0a45b58b2e4c4ee5f84482697b04271ee7c22efd54b838fc84d68` |

## 오류 메시지

| 메시지 | 확인할 내용 |
|---|---|
| `Source BIN SHA256 mismatch` | 원본이 일본 보급판의 지정 덤프인지 확인합니다. 기존 한글 ROM에는 재적용하지 않습니다. |
| `xdelta3 executable was not found` | PATH를 설정하거나 `--xdelta`로 실행 파일을 지정합니다. |
| `already exists` | 같은 결과 파일이 없는 새 출력 폴더를 `--output-dir`로 선택합니다. |

## 개별 첨부파일

개별 `Tomoshibi_Fukyuuban_KO_v0.8.xdelta`과 공개용 CUE도 같은 릴리스에 제공합니다.
해시 검사와 적용 스크립트를 함께 쓰려면 ZIP을 받으세요.
첨부 `SHA256SUMS.txt`는 배포 ZIP·개별 패치·CUE·manifest의 해시 목록입니다.
ZIP 안의 같은 이름 파일은 ZIP 내부 구성 파일의 해시 목록입니다.

[처음으로](../README.md)
