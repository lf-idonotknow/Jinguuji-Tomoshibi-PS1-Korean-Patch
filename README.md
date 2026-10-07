# 탐정 진구지 사부로 — 등불이 꺼지기 전에

PlayStation **일본 보급판(Fukyuuban)** 한글 패치. 첫 공개 버전은 **0.8**입니다.

## 다운로드 및 적용

이 저장소의 **Releases → v0.8 → Assets**에서 `Tomoshibi_Fukyuuban_KO_v0.8.zip`을 받으세요.
ZIP에는 패치, CUE, 해시를 검사하는 적용 스크립트, 설명서, Galmuri 라이선스가 들어 있습니다.
GitHub의 자동 생성 `Source code (zip)`은 패치 배포 ZIP이 아닙니다.

1. 배포 ZIP 전체를 같은 폴더에 풉니다.
2. Python 3.9 이상과 [xdelta3](https://github.com/jmacd/xdelta/releases)를 준비합니다.
3. 압축 해제 폴더에서 다음 명령을 실행합니다. 원본 BIN이 다른 폴더에 있으면 그 경로를 넣습니다.

```sh
python3 apply_patch.py "Tantei Jinguuji Saburou - Tomoshibi ga Kienu Ma ni (Japan) (Fukyuuban).bin" --output-dir "Korean"
```

적용 후 생성된 BIN/CUE를 같은 폴더에 두고 에뮬레이터에서 **CUE**를 엽니다.

[자세한 적용 방법](docs/APPLY.md) · [0.8 변경 내역](CHANGELOG.md) · [검증 범위](docs/VERIFICATION.md)

## 적용 대상

| 항목 | 값 |
|---|---|
| 판본 | 일본 보급판 / SLPS-03015 |
| 형식 | 단일 트랙 BIN/CUE, MODE2/2352 |
| 원본 BIN | `Tantei Jinguuji Saburou - Tomoshibi ga Kienu Ma ni (Japan) (Fukyuuban).bin` |
| 원본 크기 | 738,819,648바이트 |
| 원본 SHA256 | `cc44e8c81ae0f379c2adfc07fdd5dec280e8efb85217115567c8c7f9838ae519` |

원본 이름이 달라도 크기와 전체 해시가 같으면 적용할 수 있습니다.
일반판, 다른 덤프, 기존 한글 ROM은 적용 대상이 아닙니다.

## 0.8 포함 범위

- 대사·선택지·메뉴·수첩·인물 정보·관계도의 누적 한글화와 교정.
- 대사의 줄 배치, 선택지 잘림, 화자명 표시 및 이름표 공백·가운데 정렬 교정.
- Galmuri11-Condensed 사용처의 인접 한글 사이 1px 자간 적용. 다른 글꼴의 자간은 유지.
- 진행에 필요한 일본어 그림 글자의 한글화 및 색상 교정. 영어와 장식용 배경 글자는 유지.
- 대상 영상의 한글 자막. 검은 배경은 한글 글자 뒤에만 배치하며, 원래 일본어 일부가 그 밖에 보일 수 있음.
- JIN7의 화면 글자를 한글로 직접 교체. TITLEMVE와 ENDMOV는 원본 영상 유지.
- 저장 불러오기 시 스크립트 적재 조건 복구, 의뢰 설명의 마지막 행 표시 교정.
- 진구지와 점원·무쓰미·미야케·여관 여주인·올리버 등의 말투 교정, 관계도 중앙 인물명 교정.
- 조직명 `관동메이지파`, 관계 호칭 `두목 / 형님 / 아우` 적용 및 개별 오역 교정.

## 확인 범위

패치와 ZIP을 실제 원본에 적용해 생성한 BIN의 전체 SHA256이 기준 한글 ROM과 같음을 확인했습니다.
검사 환경은 **macOS / Python 3.9 / xdelta3 3.1.0**입니다.

게임의 원래 문자 출력·GPU 제출 경로와 CD 적재 계약을 검사했습니다. 모든 분기를 실플레이한 검증은 아닙니다.
모든 에뮬레이터와 원본·이전 한글판 세이브의 호환성은 아직 확인되지 않았습니다.
문제 제보에는 패치 버전, 실행 환경, 장면과 재현 순서, 스크린샷을 함께 적어 주세요.

## 오류 제보

**Issues → New issue → 오류 제보**를 사용해 주세요.
게임 원본·완성 ROM·BIOS를 첨부하지 마세요.

## 출처

게임 및 원본 자산의 권리는 원 권리자에게 있습니다.
사용한 [Galmuri](https://github.com/quiple/galmuri)의 저작권 표시와 OFL은
[LICENSES/Galmuri_LICENSE.txt](LICENSES/Galmuri_LICENSE.txt)에 있습니다.
[출처 및 권리 안내](docs/ATTRIBUTION.md)
