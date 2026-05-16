# Browser-Assisted Collection

API 연동 대신 사용자가 이미 로그인한 광고 관리자 화면을 Codex 브라우저로 읽기 전용 확인하는 절차다. 목적은 자동 조작이 아니라 데이터 수집과 화면 상태 점검이다.

## When To Use

Use when the user says:

- "로그인된 화면에서 봐줘"
- "브라우저로 광고 관리자 확인해줘"
- "CSV 뽑기 어렵고 화면은 열 수 있어"
- "네이버/카카오/쿠팡/메타 관리자 화면을 같이 보자"

Do not use when:

- 사용자가 계정 접근 권한을 갖고 있지 않다.
- 플랫폼이 자동화 접근을 명확히 금지하거나 차단한다.
- 비밀번호, 2FA, 주민번호, 결제정보 같은 민감정보 입력이 필요하다.
- 사용자가 예산 변경, 캠페인 ON/OFF 등 계정 변경을 승인하지 않았다.

## Safety Defaults

- Read-only by default.
- Ask the user to log in themselves.
- Do not request, store, or echo passwords, 2FA codes, recovery codes, customer lists, or payment details.
- Do not click save, submit, publish, delete, pause, enable, budget, bid, or billing controls.
- If the page exposes personal data, summarize aggregate metrics only.
- If a platform blocks automation, switch to screenshots or CSV export.
- If Google says "브라우저 또는 앱이 안전하지 않을 수 있습니다" or "This browser or app may not be secure", do not keep trying in that automated login page. Ask the user to open Google Ads in their normal Chrome profile, log in manually, and then let Codex read the already-open tab.

## Collection Flow

1. Ask the user to open the relevant logged-in dashboard or confirm the URL they want inspected.
2. Confirm the date range: last 7 days, last 30 days, this month, previous month, or custom.
3. Capture the visible summary metrics:
   - spend
   - impressions
   - clicks
   - conversions
   - revenue
   - CTR, CPC, CVR, CPA, ROAS if shown
4. Capture campaign/ad group/product/keyword rows that are visible on screen.
5. Note any visible warnings:
   - tracking inactive
   - rejected creative
   - limited by budget
   - learning phase
   - product out of stock
   - item winner issue
   - low balance
   - policy warning
6. If more detail is needed, ask the user whether to change filters or export CSV.
7. Convert observed data into the common metric mapping in `SKILL.md`.
8. In the report, mark browser-observed data as `화면 확인 기준`.

## Platform Pages To Inspect

Google Ads:

- Campaigns overview
- Conversion goals
- Search terms
- Asset groups or PMax insights
- Recommendations only for signals, not automatic adoption

Suggested browser steps:

1. Open the Google Ads account dashboard after the user logs in.
2. Confirm date range at the top of the page.
3. Go to Campaigns and read visible columns: cost, clicks, conversions, cost/conv., conv. value, ROAS if present.
4. Sort only if the user approves changing the visible table. Prefer reading the current table first.
5. Open Goals or Conversions only to verify conversion action names and status.
6. For PMax, inspect asset group or insights pages for search categories and asset warnings.
7. Do not apply Recommendations automatically.

Login fallback:

- If Google blocks login with an unsafe browser/app warning, stop using that login flow.
- Ask the user to open [https://ads.google.com/aw/campaigns](https://ads.google.com/aw/campaigns) in their regular Chrome profile.
- The user should choose the Google Ads account and open Campaigns.
- After the user says "준비됨" or "로그인 완료", claim or inspect that already-open tab read-only.
- If account selection is visible, ask the user to choose the intended ad account; do not infer the account from personal identifiers.

Meta Ads:

- Campaign/ad set/ad table
- Events Manager
- Pixel/CAPI diagnostics
- Lead form results if relevant

Suggested browser steps:

1. Open Meta Ads Manager after the user logs in.
2. Confirm date range and attribution setting if visible.
3. Read campaign table columns: amount spent, results, cost per result, reach, impressions, CPM, CTR, CPC, purchases/leads, purchase ROAS if present.
4. Check breakdown level: campaign, ad set, or ad. State which level was visible.
5. Open Events Manager only to verify Pixel/CAPI status, event match quality, and duplicate event warnings.
6. For lead campaigns, inspect lead form names and result volume, not individual personal lead details.
7. Do not toggle campaign/ad set/ad status.

Naver:

- Campaign and keyword performance
- Search terms or keyword detail
- Shopping ad product performance
- Extension assets

Suggested browser steps:

1. Open Naver Search Ad manager after the user logs in.
2. Confirm date range, campaign type, and whether the view is campaign, ad group, keyword, or product.
3. Read visible columns: cost, impressions, clicks, CTR, average CPC, conversions, CPA, revenue, ROAS if present.
4. For search ads, inspect keyword or search term rows if available.
5. For shopping ads, inspect product rows and visible product status.
6. Note brand/non-brand separation, device split, and any low exposure or review warnings visible.
7. Do not change bids, budgets, or keyword status.

Kakao:

- Campaign/ad group/creative performance
- Pixel & SDK status
- Kakao Talk Channel-related conversion status

Suggested browser steps:

1. Open Kakao Moment or Kakao Business dashboard after the user logs in.
2. Confirm date range and campaign objective.
3. Read campaign/ad group/creative table columns: spend, impressions, clicks, CTR, CPC, conversions/results, CPA, reach, frequency if visible.
4. Check whether the landing is external website, Kakao Talk Channel, Biz Form, or another Kakao destination.
5. Inspect Pixel & SDK status only for event names and warnings.
6. For message/channel campaigns, capture aggregate channel add, message, click, or conversion counts if visible.
7. Do not edit targeting, daily budget, bid, creative, or channel message settings.

Coupang:

- Product-level ad performance
- ROAS and spend by product
- Stock, item winner, budget warnings

Suggested browser steps:

1. Open Coupang Ads dashboard after the user logs in.
2. Confirm date range and campaign type.
3. Read campaign/product rows: spend, impressions, clicks, orders/conversions, ad revenue, ROAS, CPC if visible.
4. Capture visible product status warnings: out of stock, item winner issue, policy issue, budget exhausted.
5. Inspect high-spend low-ROAS products and low-click high-impression products.
6. Do not create/delete campaigns or change target ROAS, budget, product selection, or campaign status.

Daangn:

- Local campaign performance
- region or neighborhood performance
- calls, chats, visits, reservations if shown

Suggested browser steps:

1. Open Daangn Business dashboard after the user logs in.
2. Confirm date range, ad type, and target region.
3. Read campaign/ad rows: spend, impressions, clicks, calls, chats, visits, reservations, CTR, cost per result if visible.
4. Inspect region/neighborhood performance if visible.
5. Check business profile basics: store name, category, address, hours, phone, photos, review signals if visible.
6. Do not change target region, budget, creative, business profile, or campaign status.

## Page Interaction Rules

Allowed without extra confirmation:

- Read visible text and table values.
- Take a screenshot for the user's own diagnostic context.
- Open non-mutating detail pages such as campaign detail, conversion diagnostics, pixel status, product detail status, or report view.
- Use browser find/search within the current page.

Ask before:

- Changing date range.
- Applying filters.
- Sorting tables.
- Opening exports or downloads.
- Navigating to a different ad account or client account.

Never do unless explicitly requested and reconfirmed:

- Save, submit, publish, delete, pause, enable, duplicate, import, or apply recommendations.
- Change budget, bid, target ROAS/CPA, targeting, creative, product selection, keyword status, or campaign status.
- Open billing, payment, personal lead details, customer match lists, or account security pages.

## Output Note

When browser-assisted collection was used, include this short note:

```text
데이터 출처: 사용자가 로그인한 광고 관리자 화면을 읽기 전용으로 확인했습니다. 화면에 보이는 집계 지표 기준이며, 정밀 분석에는 CSV export가 추가로 필요할 수 있습니다.
```
