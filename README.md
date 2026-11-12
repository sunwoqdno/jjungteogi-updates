# 쭝터기 공식 홈페이지 운영 안내 (2026-11-12)

이 브랜치(`gh-pages`)는 홈페이지 전용입니다. `main`의 Windows EXE 배포, GitHub Releases, 프로그램 자동 업데이트 체계는 변경하지 않습니다.

## 현재 공개 대상으로 유지하는 기능
- `index.html`: 공식 소개 및 GitHub Releases 최신 파일 다운로드·업데이트 내역.
- `schedule.html`: 한국 서버별 어비스 매칭, 이벤트 카운트다운.
- `records.html`: 수동 PvP 기록장은 현재 홈페이지 메뉴·소개 카드에서 숨김. 파일은 기존 로컬 기록 보호를 위해 보존하며 직접 주소로는 계속 접근할 수 있습니다.
- `feedback.html`: **GitHub 로그인 없이 익명 문의·건의사항 접수**.
- `privacy.html`: 웹 로컬 저장 및 문의 데이터 처리 안내.

## 잠정 중단
- `hub.html`: 미완성 기능을 비노출 처리하고 준비 중 안내만 남겼습니다.
- PvP 자동 홈페이지 연동 기획은 보류 중이며, 새로운 기록 수집·서버 동기화는 추가하지 않았습니다.
- 과거 `data/portal.json` 자료는 재작업을 위해 그대로 보존했으나, 공개된 허브 UI에서는 사용되지 않습니다.
- 캐릭터 아이디 조회·장비 자동 연동 기능은 구현되지 않았습니다. 임의로 '지원'이라고 표기하지 않습니다.

## 익명 문의 운영
- 익명 문의 API: Supabase Edge Function `jjung-feedback` (`verify_jwt=false`, 공개 POST는 제출만 가능).
- 데이터: `public.jjung_feedback_messages` — RLS 활성화, `anon` 및 `authenticated` SELECT/INSERT/UPDATE/DELETE 권한 없음.
- 작성: 유형/제목/내용 필수, 닉네임 선택. GitHub 계정이나 이메일 필요 없음.
- 보안: 글자 수 제한, 접수량 제한(10분 3건/일 최대 10건, 동일 IP 해시 기준), 숨김 스팸 필드. IP 원문은 문의 DB에 저장하지 않고 일별 해시만 저장합니다. 다만 분산 공격 차단을 완전히 보장하지는 않습니다.
- 운영자 문의함: `inbox.html` — 기존 쭝터기 관리자용 ZIP의 **관리자_접속키.txt**를 입력해 비공개 접수 목록을 조회. 상태를 미확인/확인 중/완료로 변경하거나 삭제할 수 있습니다.
- 운영자 키는 프런트엔드 파일이나 로컬 저장소에 포함되지 않으며, 기존 `jjung_admin_access` 서버 보관 해시와 비교합니다.
- 문의는 운영자 웹 문의함에 저장되며 이메일·Discord로 자동 전송하지 않습니다.
- 익명으로 접수한 이용자에게 개별 답장을 보내는 기능은 아직 없습니다. 공개 FAQ나 패치 노트로 후속 안내하는 방식입니다.

## 공개 배포
저장소 **Settings → Pages → Build and deployment → Deploy from a branch → `gh-pages` / `/(root)` → Save**.
예상 URL: `https://sunwoqdno.github.io/jjungteogi-updates/`.
현재는 파일·함수 배포까지 반영했으나 실제 GitHub Pages 호스팅이 공개됐는지 별도 접속 테스트가 필요합니다. GitHub 코드 보기 페이지는 실행 가능한 공개 사이트가 아닙니다.

## 배포 후 반드시 수동 검증
1. `index.html`에 통합 허브 링크가 없어야 하며, `hub.html`을 열어도 준비 중 화면이어야 함.
2. 최신 EXE 및 어비스 일정·기록장 기존 기능 정상 확인.
3. `feedback.html`에서 닉네임 미입력 상태로 테스트 문의 제출 → 접수번호 표시.
4. `inbox.html`에서 기존 관리자 접속키로 로그인 → 테스트 문의 확인.
5. 문의 '확인 중' 상태 변경 및 삭제 → 목록 반영.
6. 잘못된 관리자 키와 로그인하지 않은 브라우저에서는 문의 목록에 접근 불가.
7. PC/모바일 해상도 및 네트워크 오류·글자 수 제한 안내 검증.
8. 사용량 증가 시 Supabase 무료 Edge Function 호출량과 DB 용량 확인.

**참고:** GitHub Pages 외 사용자 지정 도메인을 사용할 경우 Edge Function의 CORS 허용 출처를 추가해야 합니다.
