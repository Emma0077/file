# 부록 A – 지표 정의 및 산식(고정)
버전: v2.3.2  
최종 개정일: 2025-08-12  
소유자: LG U+ CHO부문 Innovation CoE팀 (email: hkchoi00@lguplus.co.kr)

## 목적
지표의 정의·산식을 표준화하여 비교 가능성과 재현성을 보장합니다. 모든 보고서는 본 부록을 기준으로 지표를 산정하며, 사용 지표의 산식(Formula)은 각주에 병기합니다.

## A-1. 표기/집계 공통 원칙
- 기간 표기: 분석기간 `YYYY-MM-DD ~ YYYY-MM-DD`.
- 표본 표기: 비교 표에 **N(표본 수)** 및 세그먼트(국가/플랫폼 등) 명시.
- 스코프 일치(Scope Alignment): 국가/지역·플랫폼(iOS/Android/Web) 조건 일치. 혼합 비교 시 **유저수 가중 평균**.
- 반올림: 비율은 소수 1자리, 금액은 천 단위 구분. 예외 시 각주로 사유 명시.
- 추정치(Estimate): 외부 도구 추정 수치는 **Estimate** 표기 + 산정 방식 1줄.
- ID 정합: 가능 시 크로스디바이스 식별(로그인/추정) 각주 명시.

## A-2. 핵심 지표 정의(공통)
1) **MAU (Monthly Active Users, 월간 활성 사용자)**  
   - 정의: 최근 **30일** 또는 **달력월** 기준 **고유 활성 사용자(Unique Active Users)**  
   - GA4: `active_users` (기간 필터)  
   - 각주 예시: *본 보고서는 달력월 기준 MAU 사용*

2) **WAU/DAU (주간/일간 활성 사용자)**  
   - 정의: 최근 **7일/1일** 고유 활성 사용자  
   - GA4: `active_users`

3) **Conversion Rate (CVR, 전환율)**  
   - 권장(유저 기준): `CVR = Conversions ÷ Active Users × 100%`  
   - 대안(세션 기준): `Conversions ÷ Sessions × 100%` *(분모 기준 각주 표기)*  
   - GA4: 전환 이벤트 + `active_users` 또는 `sessions`

4) **ARPU (Average Revenue Per User, 유저당 평균 매출)**  
   - 산식: `ARPU = Revenue ÷ Active Users`  
   - GA4: `total_revenue` / `active_users`  
   - 각주: 통화·**세전/세후** 기준 병기

5) **ARPPU (Average Revenue Per Paying User, 유료 유저당 평균 매출)**  
   - 산식: `ARPPU = Revenue ÷ Paying Users(결제 경험 보유 고유 사용자 수)`

6) **Retention Rate (잔존율)**  
   - 정의: D0 코호트(가입/첫 방문/첫 결제 등) 대비 특정 시점 재활성 비율  
   - 예시: `D+7 잔존율 = (D0 중 D+7 활성) ÷ (D0) × 100%`  
   - 관측 단위(일/주/월)와 **코호트 기준 이벤트** 명시

7) **Churn Rate (이탈률)**  
   - 산식: `Churn = 1 − Retention` *(동일 관측 단위 적용)*

## A-3. B2B 전용 지표(해당 시)
8) **NDR (Net Dollar Retention, 순매출 유지율)**  
   - 산식: `NDR = (시작 ARR + Expansion − Contraction − Churn) ÷ 시작 ARR × 100%`  
   - 의미: 구독 기반 매출의 순유지 정도

9) **ACV (Average Contract Value, 평균 계약 금액)**  
   - 산식: `ACV = 총 계약 금액 ÷ 계약 기간(년)` 또는 `연간 신규 계약 평균`

## A-4. 백분위/순위 계산 원칙
- **Percentile(백분위)**: 동값 처리 `method='average'` 적용  
- **Rank(순위)**: 동순위는 **평균순위(Average Rank)** 처리  
- **주의**: **표본 N < 8**일 때 퍼센타일 해석 주의 문구를 표/각주에 자동 표기

## A-5. 보고서 각주 템플릿
- CVR(유저 기준): `CVR = Conversions ÷ Active Users × 100% (달력월, KR, iOS+Android)`  
- ARPU: `ARPU = total_revenue ÷ active_users (KRW, 세전)`  
- Retention: `D+7 잔존율: D0=첫 결제일, 관측 단위=일 단위`

## 개정 이력(부록 A)
- v2.3.2 (2025-08-12): 초판 작성
