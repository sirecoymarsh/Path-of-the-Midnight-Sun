# Path of the Midnight Sun Korean Patch

Korean patch packages prepared from the local Codex localization work.

## 추가·변경 사항

이 저장소는 스팀 PC판 RPG **Path of the Midnight Sun**의 한국어 패치 배포본을 보관합니다. 게임 데이터(`resources\app\data` 폴더의 `*.json.js` 파일, Visual Novel Maker 계열 엔진의 `gs.*` 명령 구조로 추정)의 표시 문자열(`defaultText`)을 한국어로 바꿉니다. 아래 내용은 커밋(`0ef4f98`, `39c42bb`), 릴리스 `v2026.07.21`, `docs/` 보고서 8개, 배포 ZIP 안의 README·설치 스크립트·매니페스트를 근거로 정리했습니다.

> **중요**: 이 저장소에 있는 ZIP 3개는 **이미 기본 한국어 패치가 깔린 설치본에 덧씌우는 후속 패치**입니다. 대사 전체를 번역한 기본 패치(아래 1단계)와 누락 문자열 보완 패치(2단계)의 배포 파일은 이 저장소와 릴리스에 들어 있지 않습니다(`docs/` 보고서에만 기록). ZIP ①은 1·2단계 결과물 위에 덮어쓰는 파일이고, ZIP ②는 안내문에 「기존 한국어 패치와 런타임 수정 패치가 적용된 설치본」이 대상이라고 적혀 있습니다. ZIP ③이 원판에 바로 깔리는지는 기록만으로는 알 수 없습니다(추정: 대상 12개 파일이 앞 단계와 겹치지 않으면 가능). 따라서 처음 설치하는 사람은 이 저장소만으로 한국어화를 끝까지 적용할 수 없습니다.

### 번역 범위

- **번역 원문**: 영어판 문자열(`defaultText`)을 원문으로 삼았습니다.
- **1단계 기본 패치(저장소에 없음)**: 레코드 1,118개, 항목 16,508개를 처리해 그중 14,413개를 한국어로 바꿨습니다. 일반 대사 대부분이 여기 들어갑니다(`docs/path_midnight_sun_translation_progress.md`, `docs/path_midnight_sun_qa_report.md`).
- **2단계 누락 문자열 보완(저장소에 없음)**: 1단계 추출기가 `params.message/text/title/label/description`만 모아서, 변수로 조립되는 문자열(`gs.ChangeStringVariables`의 `textValue`, 데이터의 `name`, 일부 공통 이벤트 매개변수)이 빠졌던 것을 보완했습니다. 751개 파일, 문자열 3,143개를 바꿨고, 분류별로 선택지 905개, 기술명·기술 설명 533개, 동적 UI 1,079개, 데이터 인명·지명·표시명 351개, 동적 인명 34개, 공통 이벤트 표시 문자열 268개, 튜토리얼 23개입니다(`docs/path_midnight_sun_missing_string_audit.md`, `docs/path_midnight_sun_dynamic_patch_final.md`). 보고서에 「기계 번역 기반의 빠른 보완판」이라고 적혀 있습니다.
- **3단계 런타임 조회 수정 핫픽스(이 저장소 ZIP ①)**: 아래 「버그 수정」 참고. 인명 오역 6건도 함께 고쳤습니다.
- **4단계 인물 대사 선택지 재번역(ZIP ②)**: 인물이 직접 말하는 선택지 669개를 화자·상대·앞뒤 대사·분기 반응을 보고 UID별로 다시 번역했습니다. 별도 감수자가 101개를 더 고쳤고, 기존과 같아도 자연스러운 30개를 빼고 639개(148개 파일)를 교체했습니다. 상점·게임 오버·반복 시스템 메뉴·행동 지시형 선택지는 건드리지 않았습니다(`docs/path_midnight_sun_contextual_choice_retranslation_report.md`).
- **5단계 아이템 설명(ZIP ③)**: 소비품·음식·재료·검·도끼·활·방패·갑옷·투구·장신구·마나드롭·중요 아이템의 설명 블록 181개(392줄, 12개 파일)를 번역했습니다. 3개 묶음을 서로 교차 검수해 38개 표현을 더 고쳤습니다(`docs/path_midnight_sun_item_description_report.md`).
- **번역 규칙**: 인명·호칭·세계관 용어집(예: 스자쿠 오르니에르 / 오르니에르 경, 파라트라스 님, 피비 여제, 성하, 성검단, 마왕 / 대악마)을 따릅니다. 인물 관계와 시점에 따라 존댓말·반말을 구분하고, `당신`·`그녀`·영어식 주어를 걷어냈습니다. 제어 코드(`{W}`, `{C}`, `{SP}`, `{GT}`, `{LT}`)는 순서까지 보존합니다(ZIP ②의 `documentation\choice_style_guide.md`).
- **일부러 원문을 남긴 곳**:
  - 타이틀 메뉴 키 `New`, `Load`, `Continue`, `MapSave`, `Settings`, `Quit` 6개는 메뉴 동작용 키라서 원문을 유지합니다. 실제 버튼·마우스를 올렸을 때 보이는 글자는 별도 문자열로 번역돼 있습니다.
  - `dummytext`, UID, 파일·리소스 경로, 스크립트 내부 태그, 장소·시스템 메시지의 조회 키 75개.
  - 초반에 보이는 듯하지만 곧 덮어써져 화면에 나오지 않는 Warp Sword 영어 설명 경로 1개.
- **그림 글자·음성**: 이미지 속 글자와 음성은 바꾸지 않았습니다(보고서에 관련 기록 없음, 추정).

### 화면·글꼴

- 게임 내장 글꼴(BelgranoMS, edoMS, Goodlight, SansitaMS, ThicketMS)에는 한글이 없습니다. 패치는 글꼴을 넣지 않고, 게임의 Chrome/Electron 계열 렌더러가 Windows 시스템 글꼴 **맑은 고딕**으로 대신 그려 주는 것에 기대고 있습니다(`docs/path_midnight_sun_qa_report.md`). 정적 시험 이미지만 만들었고, 실제 게임 화면 확인은 사용자에게 남겼습니다.
- 줄 길이는 최대 44자, 선택지는 최대 39~40자 한 줄로 맞췄습니다(넘는 줄 0개).
- 해상도·전체화면 설정은 바꾸지 않았습니다.

### 편의 기능·단축키

- 원판에 없던 편의 기능이나 단축키는 추가하지 않았습니다. 데이터 문자열만 바꾸는 패치입니다.
- 기존 저장 데이터를 그대로 쓸 수 있고 새 게임을 시작할 필요가 없다고 기록돼 있습니다.

### 버그 수정

- **이름이 엉뚱하게 복제되던 문제**(3단계 핫픽스, ZIP ①): 장소·시스템 메시지의 영어 조회 키 75개(장소 29개, 시스템 메시지 46개)를 1·2단계에서 한글로 번역해 버려서 게임의 정확 일치 조회가 실패했고, 그때 공용 출력 변수 `GT314/GT315`가 비워지지 않아 **직전 NPC·적·장소 이름이 다른 곳에 그대로 다시 나왔습니다**. 조회 키 75개를 영어로 되돌리고, 공용 조회표 10개에 실패 안전장치 12개를 넣었습니다. 기존 저장 데이터에 이미 들어간 한글 장소 키도 직전 이름을 이어받지 않게 처리했습니다(`docs/path_midnight_sun_runtime_lookup_hotfix_report.md`).
- **원판 조회표에 없던 이름 추가**(ZIP ①): 화자 6명, `Daimon Nero`, 지도 이름의 대소문자 별칭 6개를 추가했습니다. 이것은 원판의 누락을 메운 것입니다.
- **인명 오역 수정**(ZIP ①): `Roger`(「알았다」→ 로저), `Septimus`(→ 셉티머스), `Bandit`(「적기」→ 산적), `Thug`(「자객」→ 폭력배), `Wyv. Rider`(→ 와이번 기병), `Neaw`(「새로운」→ 니오).
- **원판 데이터 오류 수정**(5단계, ZIP ③): 원판에서 `Rubber Band`(고무줄) 설명을 넣는 명령 2개가 엉뚱하게 `Storm Pendant`(폭풍 펜던트) ID를 가리켜, 고무줄 설명이 폭풍 펜던트에 복사되던 오류를 고쳤습니다(`7C550F5815B42142530BAAB7872310C75643.json.js`).

### 설치·제거 방식

- **적용 순서**: ① 런타임 조회 핫픽스 → ② 인물 대사 선택지 → ③ 아이템 설명(README 「Packages」, 릴리스 노트). 그 앞에 1·2단계 기본 패치가 깔려 있어야 합니다.
- **ZIP ① 런타임 조회 핫픽스**(80개 파일): 설치 스크립트 없이 파일을 게임의 `resources\app\data` 폴더에 덮어쓰는 방식입니다. `manifest.json`에 파일별 적용 전·후 SHA-256이 있습니다. 자동 백업·복원은 없으므로 덮어쓰기 전에 직접 백업해야 합니다.
- **ZIP ② 선택지 재번역**(`tools\install_choice_retranslation.ps1`, `restore_choice_retranslation.ps1`): 148개 대상 파일의 현재 SHA-256이 예상과 모두 같을 때만 설치하고, 하나라도 다르면 아무것도 쓰지 않습니다. 적용 전 자동 백업, 도중 오류 시 자동 롤백, 설치 후 해시 재검증을 합니다.
- **ZIP ③ 아이템 설명**(`install_item_descriptions.ps1`, `restore_item_descriptions.ps1`): 12개 원본·패치 파일과 매니페스트 4종의 SHA-256을 검사합니다. 백업 폴더는 게임 data 폴더와 패치 폴더 바깥이어야 합니다. 정확히 허용된 394개 값(설명 392개 + ID 2개) 말고는 바뀌지 않음을 확인하고, 설치·복원이 중간에 끊겨 섞인 상태도 복원할 수 있습니다. 변조된 패키지·백업은 쓰기 전에 막습니다.
- 세 설치기 모두 `-GameDataDir`(게임의 `resources\app\data` 경로)와 `-BackupRoot`/`-BackupDir`를 직접 넣어야 하며, 스팀 경로 자동 탐색은 없습니다.
- 완전히 원본으로 되돌리려면 나중에 깐 것부터 거꾸로(③ → ② → ① → 2단계 → 1단계) 복원해야 합니다(2단계 보고서 기준, ①은 수동 백업으로 추정).
- 배포 ZIP의 SHA-256은 `SHA256SUMS.txt`에 있습니다.

### 판(버전)별 변경 기록

모든 작업은 2026-07-21 하루에 이루어졌습니다(한국 시각, 각 `docs/` 보고서 기준).

- **1단계 기본 대사 패치**: 16,508개 항목 처리, 14,413개 변경, 실제 게임 적용. 이후 실기 점검에서 선택지·기술명·튜토리얼 누락을 발견(저장소에 배포 파일 없음).
- **2단계 누락 문자열 보완**: 751개 파일, 3,143개 문자열(저장소에 배포 파일 없음).
- **3단계 런타임 조회 핫픽스**: 이름 복제 버그 수정, 80개 파일(ZIP ①).
- **4단계 인물 대사 선택지 재번역**: 639개 선택지 / 148개 파일, 13:37 적용(ZIP ②).
- **5단계 아이템 설명**: 181블록 / 392줄 / 12개 파일, 원판 ID 오류 2건 수정, 14:48 적용(ZIP ③).
- **2026-07-22** (커밋 `0ef4f98`, 릴리스 `v2026.07.21`): ZIP 3개와 보고서를 저장소에 올리고 릴리스로 공개.
- **2026-08-03** (커밋 `39c42bb`): 제3자 자산 권리 고지(`ASSET_NOTICE.md`) 추가.

### 알려진 문제

- 1·2단계 기본 패치가 저장소에 없어, 새로 설치하는 사람은 한국어화를 완성할 수 없습니다(위 「중요」 참고). 하나로 합친 설치기는 아직 없습니다.
- 한글 표시를 시스템 글꼴(맑은 고딕)에 기대므로, 맑은 고딕이 없는 환경(예: Steam Deck/Linux)에서는 한글이 깨질 수 있습니다(추정).
- 실제 게임 화면에서 글꼴·줄바꿈·인벤토리 설명을 확인했다는 기록은 없습니다. 보고서는 모두 정적 검사와 모의 폴더 설치 시험 결과입니다.
- 2단계는 기계 번역 기반 빠른 보완판이라, 선택지(4단계)와 아이템 설명(5단계) 외의 동적 문자열에는 어색한 번역이 남아 있을 수 있습니다.
- `docs/` 보고서와 ZIP 안 안내문의 예시 명령에는 작업한 PC의 게임·백업 경로가 그대로 들어 있습니다. 자기 경로로 바꿔서 실행해야 합니다.

## Packages

Apply in this order unless a later consolidated installer is provided:

1. `releases/Path_of_the_Midnight_Sun_runtime_lookup_hotfix_20260721.zip`
   - Runtime lookup/name/location-choice safety hotfix.
2. `releases/Path_of_the_Midnight_Sun_contextual_choices_20260721_133723.zip`
   - Contextual retranslation for awkward choice/dialogue-option strings.
3. `releases/Path_of_the_Midnight_Sun_item_descriptions_20260721_145021.zip`
   - Korean item description strings and QA manifest.

Each zip contains its own README/install/restore scripts and manifest files.

## Verification

Check package hashes against `SHA256SUMS.txt` before distribution.

## Notes

- Reports and QA notes are under `docs/`.
- This repository preserves the release packages exactly as generated in the workspace.
