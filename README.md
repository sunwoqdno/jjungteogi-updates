# 쭝터기 홈페이지 (v0.2)

아이온2 **한국 서버**용 비공식 PvP 유틸리티의 홈페이지입니다. 이 브랜치는 웹사이트 전용이며 프로그램 EXE 배포는 별도 `main` 브랜치의 기존 GitHub Releases를 유지합니다.

## 사이트 기능
- `index.html`: 소개, GitHub Releases 기반 최신 EXE 다운로드·업데이트 내역, 패치 요약.
- `schedule.html`: 21개 재매칭 그룹 검색, KST 이벤트 타이머·필터.
- `records.html`: 수동 입력 브라우저 로컬 PvP 기록장, RP 그래프, JSON 백업·복원. **EXE 자동 연동 아님**.
- `feedback.html`: GitHub Issues 양식 작성. GitHub 로그인 후 최종 제출해야 접수됨.
- `data/schedule.json`: 2026-11-11 패치 기준 매칭과 이벤트 데이터.

## 공개 및 테스트
GitHub 저장소 Settings → Pages → Deploy from a branch → `gh-pages` / `/(root)` → Save. 공개 전 GitHub 저장소 Issues 기능을 확인하세요.

검증 항목:
1. 네자칸↔바카르마=17그룹, 이스라펠↔이슈타르=20그룹.
2. 수·토 점령전, 금·일 나흐마: 그룹1=22:00, 그룹2=22:30, 그룹3=23:00.
3. 카이라: 매일 01:00·09:00·13:00·21:00.
4. 일정 시각 한국시간 표시, 24시간/7일 전환, 콘텐츠 필터 동작.
5. 로컬 PvP 기록 작성·새로고침·백업·삭제·복원.
6. 문의 양식에서 GitHub Issues 새 이슈 작성이 가능한지 로그인 후 확인.
7. PC·모바일 가독성, GitHub EXE 다운로드, 11/11 패치 링크 확인.

## 개인정보와 서버 운영
- 웹페이지의 개인 PvP 기록은 브라우저에만 저장되고 서버로 전송되지 않습니다.
- 웹사이트는 공개 Supabase 관리자 통계·설치 식별자·관리자 키에 접근하지 않습니다.
- GitHub Issues에 등록한 제보는 공개 글입니다. 민감한 정보는 작성하지 마세요.
- `data/schedule.json` 변경 전 출처와 적용일을 확인하고 `verifiedAt`을 갱신하세요. `confidence=patch`는 11/11 패치 확인, `recent`는 최근 일정, `community`는 커뮤니티 참고입니다.
- 향후 EXE↔웹 자동 통계 연동 시 수집 동의·접근제어·보관기간·삭제 및 공유 권한 정책을 먼저 설계하세요.

참고: [11월 11일 패치노트 게재본](https://www.inven.co.kr/board/aion2/6388/295057), [AION2 공식 업데이트](https://aion2.plaync.com/ko-kr/board/update/list).
