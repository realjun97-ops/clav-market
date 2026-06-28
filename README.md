# 데일리 시장 브리핑 에이전트 시스템

매일 아침 8:30, 5개 전문 서브에이전트가 전날 시장 동향을 조사하고 오케스트레이터가
하나의 한국어 브리핑으로 종합하는 Claude Code 루틴용 구성.

## 구성
```
CLAUDE.md                         # 오케스트레이터(총괄) 지침 + 출력 형식
ROUTINE_PROMPT.md                 # 루틴에 붙여넣을 프롬프트 + 트리거 설정
reports/                          # 매일 보고서가 저장되는 폴더(.gitkeep)
.claude/agents/
  01-financial-markets.md         # 금융시장(채권·주식·환율·금)
  02-realestate-market.md         # 부동산 시세·신규분양·미분양
  03-government-policy.md         # 세제·수요/공급·대출규제
  04-redevelopment.md             # 재개발·재건축·정비사업
  05-highend-market.md            # 하이엔드 공급·분양·시세
```

## 설치 (폰에서)
1. 이 파일들을 GitHub 레포에 올린다. (지난주 만든 레포가 있으면 그 레포의
   `.claude/agents/`와 `CLAUDE.md`를 이 내용으로 교체.)
   - 폴더 구조 그대로 유지: `.claude/agents/` 안에 5개 `.md`, 루트에 `CLAUDE.md`.
2. claude.ai/code/routines → **New routine**.
3. `ROUTINE_PROMPT.md`의 프롬프트를 Prompt 칸에 붙여넣기.
4. 이 레포 연결, **Environment에서 네트워크(웹) 접근 허용**.
5. (선택) Notion / Gmail 커넥터 연결 → 보고서 자동 발송.
6. 트리거: Daily · 08:30 (KST) → **Create**.

## 운영 팁
- **정확도:** 모든 에이전트는 출처·날짜를 붙이고, 못 찾은 수치는 "확인 필요"로 표기하도록
  설계됨(임의 숫자 생성 금지). 그래도 첫 1주일은 결과 transcript를 열어 검수 권장.
- **초록불 = 성공 아님:** 실행 목록의 초록불은 "에러 없이 종료"일 뿐, 보고서 품질은
  run을 열어 확인.
- **모델:** 서브에이전트는 `model: inherit`(루틴 설정값 사용). 종합 품질을 높이려면
  루틴 모델을 상위 모델로 두면 됨.
- **요금:** 루틴은 Pro 이상에서 동작(Pro = 하루 5회). 하루 1회 실행이면 충분.
- **시각 조정:** 8:30이 아닌 다른 시각은 트리거에서 변경하거나 `/schedule update`로
  cron 직접 지정(예: `30 8 * * *`).

※ 본 시스템 산출물은 정보 제공용이며 투자 권유·매매 자문이 아님.
