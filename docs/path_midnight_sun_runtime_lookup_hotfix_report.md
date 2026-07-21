# Path of the Midnight Sun 런타임 이름 복제 버그 수정

## 원인

- 장소·시스템 메시지용 영문 조회 키 75개가 먼저 한글로 번역되어 exact-match 조회가 실패했습니다.
- 조회 실패 시 공용 출력 변수 `GT314/GT315`가 초기화되지 않아 직전 NPC·적·장소 이름이 재사용됐습니다.
- `Daimon Nero` 등 일부 실제 화자·적 이름은 원본 조회표에도 누락돼 있었습니다.

## 적용 내용

- 런타임 조회 입력 75개 복원: 장소 29개, 시스템 메시지 46개
- 공용 번역 조회표 10개에 실패 안전장치 12개 추가
- 누락 화자 6명, `Daimon Nero`, 지도 대소문자 별칭 6개 추가
- `Roger`, `Septimus`, `Bandit`, `Thug`, `Wyv. Rider`, `Neaw` 오역 수정
- 기존 저장 데이터의 한글 장소 키도 직전 NPC 이름을 상속하지 않도록 처리

## 설치 및 검증

- 게임 데이터 80개 파일에 적용 완료
- 적용 후 해시·JavaScript 구문·조회 키·fallback·추가 매핑 검증: 오류 0
- 저장 파일은 변경하지 않았으며 새 게임을 시작할 필요가 없습니다.
- 원상 복구 백업: `C:\Users\CadriacLord\Documents\Codex\2026-07-20\https-github-com-mcpads-emucap-codex\work\path_midnight_sun\backups\runtime_lookup_fix_20260721_122213`

별도 hotfix ZIP의 파일들은 게임의 `resources\app\data` 폴더에 덮어쓰는 구조입니다.
