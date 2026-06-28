# 루틴에 붙여넣을 프롬프트 (claude.ai/code/routines → New routine → Prompt)

아래 한 단락을 루틴의 Prompt 칸에 그대로 붙여넣으세요.
(레포에 CLAUDE.md가 있으므로 자세한 절차는 자동으로 따라갑니다. 그래도 무인 실행 안정성을
위해 핵심 지시를 한 번 더 명시합니다.)

---

이 레포의 CLAUDE.md 지침에 따라 "데일리 시장 브리핑"을 작성하라.
먼저 오늘 날짜(KST)와 전날(주말·공휴일이면 직전 영업일) 범위를 확정한 뒤,
financial-markets-analyst, realestate-market-analyst, govt-policy-analyst,
redevelopment-analyst, highend-market-analyst 5개 서브에이전트를 모두 호출해
각 도메인의 전날 동향을 조사시켜라. 각 결과를 검수하고(출처·날짜 없는 수치는
"확인 필요"로 표기, 추정·창작 금지), CLAUDE.md의 출력 형식대로 하나의 한국어
보고서로 종합하라. 보고서를 reports/{오늘날짜}.md 로 저장하라(필요 시
claude/ 브랜치로 푸시·PR 생성). Notion 또는 Gmail 커넥터가 연결돼 있으면
같은 내용을 그 채널로도 발송하라. 사실과 출처 중심으로, 투자 권유는 하지 마라.

---

## 트리거 설정
- 유형: Schedule (스케줄)
- 빈도: Daily (매일)
- 시각: 오전 8:30 (로컬 KST — 자동 변환됨)
- 참고: 스태거로 인해 8:3X분에 시작될 수 있음(정상)

## 레포/환경 설정
- Repositories: 이 레포 연결
- Environment: **네트워크(웹) 접근 허용** — 서브에이전트의 WebSearch/WebFetch가 동작해야
  실제 데이터를 수집할 수 있습니다.
- Connectors(선택): Notion / Gmail — 보고서 발송용
