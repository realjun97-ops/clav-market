# 데일리 시장 브리핑 v2 — 실행 간 학습 + THE CLAV 60 영업 인텔리전스

## 구성
```
CLAUDE.md                     총괄(오케스트레이터) v2: 날짜·중복·메모리·회고 SOP
MEMORY_SCHEMA.md              Notion 메모리 구조(첫 실행 때 자동 생성)
ROUTINE_PROMPT.md             루틴 프롬프트 v2 + 트리거(평일)·환경 설정
.claude/settings.json         권한(WebFetch 전체 도메인·Bash date·Notion·PlayMCP)
.claude/settings.local.json   v1의 2개 도메인 제한 해제
.claude/commands/market-brief.md  수동 실행용(v2 절차로 통일)
.claude/agents/01~06          서브에이전트 6개(06 = CLAV 60 영업전략 신규)
```

## iPhone에서 적용 (약 10분)
1. Safari → github.com/realjun97-ops/clav-market 로그인.
2. 레포에서 **`agent/` 폴더 삭제**(구버전 zip 포함) — 파일 열기 → ⋯ → Delete file, 두 파일 모두.
3. **Add file → Upload files** → 이 압축을 푼 파일들을 경로 그대로 업로드.
   (iPhone 파일 앱에서 zip 탭 → 자동 압축해제 → 폴더째 선택. `.claude` 폴더는 숨김이라 안 보이면
   각 파일을 열어 GitHub 웹에서 **Edit(연필) → 전체 붙여넣기**로 교체 — 전체 교체 방식.)
4. claude.ai/code/routines → 기존 루틴 → Edit
   - Prompt: ROUTINE_PROMPT.md 본문으로 **전체 교체**
   - Schedule: **Weekdays 08:30**
   - Environment: Network **Full**
   - Connectors: Notion·PlayMCP 체크
5. **Run now** 1회 → Notion에 「CLAV 브리핑 시스템 메모리」와 DB 3개 생성 확인.
6. Windows PC의 작업 스케줄러에 `run_briefing.bat`가 남아 있으면 **사용 안 함**으로 전환(중복 발행 원인).
7. 매주 월요일 아침 전, Notion 앱에서 「CLAV 60 영업 실적 로그」에 1행 입력(문의·방문·계약·유입경로).

## 학습이 일어나는 방식
실행 시작: 메모리 읽기 → 교훈(규칙화 항목은 필수 규칙)·스냅샷·확인필요 큐를 각 에이전트에 주입
실행 종료: 각 에이전트의 「학습 메모」→ 교훈 로그 누적(3회 반복 시 규칙화) → 스냅샷·큐·경쟁상품 갱신
월요일: 영업 실적 로그로 타겟·채널 가설 재평가 → 메모리의 영업 가설 덮어쓰기

※ 산출물은 정보 제공용이며 투자 권유·매매 자문이 아님.
