# 루틴 프롬프트 v2 (claude.ai/code/routines → 기존 루틴 Edit → Prompt 전체 교체)

---
이 레포의 CLAUDE.md(v2) STEP 0~6을 순서대로 빠짐없이 수행하라.
STEP 0에서 반드시 Bash로 `TZ=Asia/Seoul date`를 실행해 KST 날짜를 확정하고, 토·일이면 종료하라.
STEP 1에서 Notion 「CLAV 브리핑 시스템 메모리」를 읽고(없으면 MEMORY_SCHEMA.md대로 생성),
6개 서브에이전트(financial-markets-analyst, realestate-market-analyst, govt-policy-analyst,
redevelopment-analyst, highend-market-analyst, 그리고 그 결과를 받은 clav60-sales-strategist)에게
메모리 발췌를 함께 넘겨라. 같은 날짜 Notion 페이지가 있으면 갱신하고 새로 만들지 마라.
STEP 6 메모리 갱신(교훈 로그·스냅샷·확인 필요 큐·경쟁상품 트래커)을 끝내기 전에는 종료하지 마라.
사실과 출처 중심, 추정·창작 금지, 투자 권유 금지.
---

## 트리거
- 유형 Schedule / 빈도 **Weekdays(평일)** / 시각 08:30 KST
  (cron 직접 지정 시 `30 23 * * 0-4` = UTC 일~목 23:30 = KST 월~금 08:30)
- v1의 "Daily" 설정 때문에 토요일 발행이 발생했음 → 반드시 평일로 변경

## 환경
- Network access: **Full(전체 허용)** — Trusted/제한 목록이면 WebFetch가 대부분 실패함
- Connectors: Notion(필수), PlayMCP(카카오톡)
