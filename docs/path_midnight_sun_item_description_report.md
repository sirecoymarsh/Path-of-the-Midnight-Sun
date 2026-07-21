# Path of the Midnight Sun — 아이템 설명 한국어 패치 보고서

## 적용 결과

- 적용 시각: 2026-07-21 14:48 KST
- 적용 위치: `P:\SteamLibrary\steamapps\common\Path of the Midnight Sun\resources\app\data`
- 수정 파일: 12개 아이템 데이터 생성 이벤트
- 번역 범위: 아이템 설명 블록 181개, 런타임 표시 문자열 392줄
- 구조 수정: 2건
- 실파일 검증: 392/392 일치, 오류 0
- 누적 패치 검증: 705/705 파일 일치 및 JavaScript 컴파일 통과, 오류 0

## 번역 방식

- 아이템 종류, 앞뒤 설명 줄, 실제 효과와 기존 고유명사를 함께 보고 문맥별로 번역했다.
- 3개 분할 번역 묶음을 서로 교차 검수해 38개 표현을 추가 교정했다.
- 최종 언어 QA: 181개 블록/392줄 전수 검토, 미해결 오류 0.
- 같은 영어 조각이라도 아이템이나 이어지는 문장이 다르면 완성 문장에 맞춰 별도로 옮겼다.

## 원본 데이터 오류 수정

`Rubber Band`의 두 설명 setter가 잘못된 `Storm Pendant` ID를 대상으로 삼던 오류를 함께 수정했다.

- 파일: `7C550F5815B42142530BAAB7872310C75643.json.js`
- UID: `9FBBB8E6783C5549F18A5A0016D49D922BB0`
- UID: `D97685DB5C7BE54EDD8A5657A2334784803B`
- 잘못된 대상: `3BD6FE871C51B8479799CE638237B9CC10B7`
- 수정 대상: `873C5AA060C4B748B57A7AC2E563C0CDF90E`

따라서 고무줄 설명이 폭풍 펜던트에 복사되는 현상도 막는다.

## 범위 안전성

- 정확히 392개의 `defaultText` leaf와 위 2개의 `characterId` leaf만 변경했다.
- 총 허용 변경 leaf: 394개, 예상 밖 변경: 0개.
- 초기에 보이는 Warp Sword 영어 setter(`15ECC...`)는 뒤의 검 생성 이벤트에서 항상 덮어써지는 비표시 경로라 패치 대상에서 제외했다.
- 대사, 선택지, 장소 이동, 인명 및 전투 이름 로직은 이번 아이템 패치가 건드리지 않는다.

## 설치·복원 시험

- 격리 게임 구조에서 정상 설치: 12파일/181블록/392줄/2수정 통과.
- 설치 후 의미 검증: 392줄, 오류 0.
- 정상 복원 후 원본 해시 불일치: 0.
- 원본 5개 + 패치본 7개의 중단 혼합 상태 복원: 통과.
- 변조한 패키지 및 변조한 백업: 쓰기 전에 차단, 게임 파일 변경 0.
- ZIP 추출 파일 19개 해시 일치, 추출본 설치·의미 검증·복원 통과.

## 실게임 백업

원본 12개 파일과 패치 복구본, 고정 manifest 및 설치 journal을 다음 폴더에 보관했다.

`C:\Users\CadriacLord\Documents\Codex\2026-07-20\https-github-com-mcpads-emucap-codex\work\path_midnight_sun\backups\item_descriptions_20260721_144819`

복원할 때는 게임을 종료하고 ZIP의 `restore_item_descriptions.ps1`에 위 폴더를 `-BackupDir`로 전달하면 된다.

## 승인 아티팩트 SHA-256

- 상세 semantic manifest: `A29BB8B8DB0683F5AFE3A12DEFEB64CBABB45EF6402C6AC90CBBB917E979DCBB`
- 설치 manifest: `957A4715373C0C6E668872E0C567050AB03111E3F015A7DD11DD53099B5B8746`
- 번역 map: `12EFA0C94A93417AF104530A8FE74F1086D5E3DEA6C5D3185FB9F2F0021C2754`
- 최종 언어 QA: `499C414B73F362BBB9C3E2562D3200F2C4BDF25136D98603B7A95ED6E48A0B88`
- 배포 ZIP: `280511C4623FD28EE1DB7E737E6B1E635DFCE35680AE8298C02D11EF87F773DB`

## 마지막 확인

게임 프로세스가 종료된 상태에서 적용했으며, 적용 직후 실파일과 누적 패치 705개를 다시 대조했다. 실제 인벤토리 UI 렌더링은 게임을 실행한 뒤 소비품·장비·재료 설명을 열어 확인하면 된다.
