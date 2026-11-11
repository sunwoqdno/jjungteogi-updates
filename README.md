# 쭝터기 홈페이지 v0.3

아이온2 **한국 서버**용 비공식 PvP 유틸리티의 홈페이지. 웹사이트는 `gh-pages` 브랜치에만 있으며 EXE·릴리스 배포는 기존 `main`에 영향을 주지 않습니다.

## 사이트 기능

| 파일 | 기능 | 데이터 방식 |
|---|---|---|
| `index.html` | 최신 EXE·업데이트 내역, 웹 기능 연결 | GitHub Releases + 정적 HTML |
| `hub.html#home` | **1** 내 서버 홈, 매칭·다음 보스·중요 마감 | `schedule.json` + localStorage |
| `hub.html#rewards` | **4** 쿠폰·보상 센터, 코드 복사·발급 링크·수령 체크 | `portal.json` + localStorage |
| `hub.html#patches` | **5** 패치 전·후 비교, PvP·장비·어비스 필터 | 확인한 패치 자료 정적 JSON |
| `hub.html#calendar` | **6** 시즌·점검 예정 날짜 달력 | 정적 JSON (시간 미확정 표시) |
| `hub.html#updates` | **8** 최신 버전 알림 센터, 확인 버전 저장 | GitHub Releases API + 로컬 저장 |
| `hub.html#search` | **10** 42개 서버, 쿠폰, 패치, 일정, 메뉴 통합 검색 | 정적 JSON + 브라우저 검색 |
| `schedule.html` | 21개 그룹 검색, KST 실시간 카운트다운, 이벤트별 필터 | `data/schedule.json` |
| `records.html` | 교전 수동 입력, RP 추이, JSON 백업·복원 | 브라우저 localStorage |
| `feedback.html` | 버그·일정 오류·기능 제안 접수 | GitHub Issues 열기 |
| `privacy.html` | 브라우저 저장·외부 서비스 이용 안내 | 정적 HTML |
| `data/portal.json` | 11/11 패치, 유효 쿠폰, 일정·마감일, 메뉴 검색 인덱스 | 2026-11-11 기준 검증 자료 |

## 공식 소스 / 적용 범위

- [AION2 빛과 장막의 경계](https://aion2.plaync.com/ko-kr/conts/261108_update) — 11/11 업데이트, 11/18 무료 서버 이전 예정.
- [AION2 11/11 패치노트 게재본](https://m.inven.co.kr/board/aion2/6388/295057?category=%EC%86%8C%EC%8B%9D) — 어비스 시즌, 스탯, 장비, 게임 내 보상 및 일정.
- [NC 1주년 쿠폰 안내](https://lounge.plaync.com/feed/86800?country=KR&locale=ko-KR) — `THANKYOUDAEVA` 쿠폰, 2027-03-03 점검 전까지 사용.
- [NC 성장 서포트 쿠폰](https://aion2.plaync.com/ko-kr/promo/261111_boost) — 개인 발급, 2027-02-24 점검 전까지 발급·등록.
- **정기점검 시작 시간 미공개:** 달력에는 날짜와 '정기점검 전' 표기만 사용합니다.
- **미래 일정 변경 가능:** 운영자가 공지를 재확인해 `data/portal.json` / `data/schedule.json`을 갱신해야 합니다. 자동 공식 공지 수집은 구현하지 않았습니다.
- 무료 서버 이전은 시행 **예정**으로 표기하며 후속 공지 전까지 상세 조건을 확정하지 않습니다.

## 무료 운영 및 개인정보

1. 모든 검색, 쿠폰 완료 체크, 서버 선택, 마지막으로 본 버전 정보는 **브라우저 로컬에 저장**됩니다. 검색어는 서버로 전송하지 않습니다.
2. 프로그램 EXE의 실제 PvP 교전 로그는 자동으로 수집하지 않습니다. 웹 기록장은 수동 입력만 가능합니다.
3. 개인 발급형 쿠폰 번호는 홈페이지에서 조회·저장하지 않습니다. 공식 발급 화면만 연결합니다.
4. GitHub Releases API 사용량은 10분 세션 캐시로 감소시켰습니다. 자동 푸시/백그라운드 감시는 구현하지 않았습니다.
5. Supabase 관리자 통계·서비스 역할 키·설치 ID 원본은 공개하지 않습니다.

## 공개

GitHub 저장소 **Settings → Pages → Build and deployment → Deploy from a branch → `gh-pages` / `/(root)` → Save**.

GitHub Pages 설정을 완료하기 전에는 URL이 열리지 않을 수 있습니다. 코드가 업로드됐다는 사실과 웹사이트 공개 완료는 별개입니다.

## 회귀 테스트 체크리스트

- [ ] `index.html`에서 `hub.html` 메뉴 6개 연결 및 기존 EXE 다운로드 유지
- [ ] 서버 선택(네자칸=17그룹↔바카르마, 이스라펠=20그룹↔이슈타르) 및 새로고침 후 저장 유지
- [ ] KST 날짜·시간, 그룹별 점령전·나흐마 카운트다운 정확성
- [ ] 쿠폰 `THANKYOUDAEVA` 복사, 개인 발급 쿠폰 공식 링크, 수령 체크 및 기간 만료 표시
- [ ] 패치 PvP/어비스/장비/시스템 필터, 전후 수치 및 원문 링크
- [ ] 달력 이전/다음 달 이동, 날짜 선택 및 일정 출처 표시
- [ ] GitHub API 최신 릴리스 조회, 확인 전·후 상태, 10분 캐시, 오류 시 공식 릴리스 이동
- [ ] Ctrl/⌘+K 검색, 서버·쿠폰·패치·날짜 검색 및 링크 이동
- [ ] 기록장·문의·어비스 일정 기존 기능 정상 여부
- [ ] 375px 모바일, 1280x720 PC, 1920x1080 PC 화면 및 키보드 조작
- [ ] 개인정보 안내 및 관리자 키·비공개 데이터 노출 없는지 확인
