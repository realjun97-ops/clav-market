---
description: 5개 분야 전문 에이전트를 모두 실행해 일일 시장 브리핑(종합 요약 보고서)을 생성
allowed-tools: ["Task", "WebSearch", "WebFetch", "Read", "Write"]
---

오늘 날짜를 기준으로 THE CLAV 60 일일 시장 브리핑을 작성하라.

1. 다음 5개 서브에이전트를 **모두 실행**한다(가능하면 병렬). 각 호출 프롬프트에 오늘 날짜와 조사 대상기간(기본: 최근 1주)을 포함한다:
   - finance-analyst
   - realestate-analyst
   - highend-clav60-analyst
   - policy-analyst
   - redevelopment-analyst
2. 추가 초점이 있으면 ($ARGUMENTS) 해당 주제에 가중치를 둔다. 비어 있으면 전 분야 균형.
3. 5개 보고를 취합·종합한다. 중복은 제거하고, 상충하는 수치는 양쪽을 병기·플래그하며, 분야 간 인과(예: 금리·정책 → 분양수요)를 해석한다.
4. `CLAUDE.md`의 **표준 보고 구조**에 따라 작성하고 `reports/시장브리핑_<YYYYMMDD>.md` 로 저장한다.
5. 저장 후, **0. 핵심 요약** 섹션만 콘솔에 출력한다.

모든 수치에는 출처와 기준일을 붙이고, 사실과 전망을 구분하며, 확인되지 않은 정보는 "확인 안 됨"으로 남긴다.
