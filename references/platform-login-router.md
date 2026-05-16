# Platform Login Router

사용자가 어떤 광고 관리자에 로그인해야 하는지 모를 때 쓰는 라우터다. 한 번에 모든 링크를 던지지 말고, 사용자의 광고 유형과 목표를 물어서 가장 가능성이 높은 1-2개부터 안내한다.

## Opening Question

처음에는 이렇게 묻는다.

```text
어떤 광고를 먼저 진단할까요? 아래에서 가장 가까운 것을 골라주세요.

1. Google 검색/YouTube/PMax 광고
2. Instagram/Facebook 광고
3. 네이버 검색광고/쇼핑검색광고/파워링크
4. 카카오톡 채널/카카오모먼트/비즈보드
5. 쿠팡 상품광고
6. 당근 동네 광고
7. 잘 모르겠음
```

If the user chooses "잘 모르겠음", ask for one of:

- 광고비 결제 내역에 보이는 플랫폼명
- 캠페인 이름 또는 광고 관리자 화면 캡처
- 광고가 노출되는 위치: 네이버 검색, 인스타그램, 카카오톡, 쿠팡 상품페이지, 당근 동네 화면, YouTube
- 광고 목표: 검색 유입, 상품 판매, 리드, 전화/예약, 채널 친구, 앱 설치

## Routing Table

| User says / ad appears on | Send them to | Login identity | First screen to open |
|---|---|---|---|
| Google 검색, YouTube, PMax, Demand Gen, Google 쇼핑 | [Google Ads](https://ads.google.com/) | Google 계정 or MCC 접근 권한이 있는 계정 | Campaigns |
| Instagram, Facebook, Reels, Meta 리드 광고 | [Meta Ads Manager](https://adsmanager.facebook.com/) | 광고계정 권한이 있는 Facebook/Meta 계정 | Campaigns |
| 네이버 검색 결과 상단, 파워링크, 쇼핑검색광고 | [Naver Search Ads](https://searchad.naver.com/) or [Naver Ad Manager](http://manage.searchad.naver.com) | 네이버 검색광고 광고주 계정 | 광고관리, 캠페인, 키워드 성과 |
| 카카오톡, 다음, 카카오 비즈보드, 채널 친구, 메시지 광고 | [Kakao Business](https://business.kakao.com/) | 카카오비즈니스 권한이 있는 카카오계정 | 카카오모먼트 캠페인 |
| 쿠팡 상품 상세/검색/추천 영역 상품광고 | [Coupang Ads](https://ads.coupang.com/) | 쿠팡 판매자/공급자 광고 권한 계정 | 광고관리, 상품별 성과 |
| 동네 가게, 지역 타겟, 전화/채팅/방문 유도 | [Daangn Business](https://business.daangn.com/) | 당근비즈니스 권한 계정 | 광고 관리, 캠페인 성과 |

## Decision Rules

Use these rules when the user's answer is vague.

- 상품 판매가 목표이고 쿠팡 판매자라면 Coupang Ads부터 본다.
- 검색어별 성과를 보고 싶다면 Naver Search Ads 또는 Google Ads부터 본다.
- 인스타그램/페이스북 소재 성과, 리드폼, 픽셀/CAPI를 말하면 Meta Ads Manager부터 본다.
- 카카오톡 채널 친구, 메시지, 비즈보드, 카카오 픽셀을 말하면 Kakao Business부터 본다.
- 오프라인 매장, 동네 반경, 전화, 채팅, 예약을 말하면 Daangn Business부터 본다.
- B2B SaaS나 리드 광고는 Google Ads와 Meta Ads를 먼저 보고, 네이버 브랜드검색은 보조로 본다.
- 이커머스는 Google/Meta, Naver, Coupang 중 실제 매출 발생 플랫폼을 먼저 본다.

## Guided Login Response Template

선택지가 정해지면 이렇게 안내한다.

```text
좋습니다. 지금 상황이면 [플랫폼명]부터 보는 게 맞습니다.

1. 이 링크를 열어주세요: [공식 링크]
2. [로그인 계정 유형]으로 직접 로그인해 주세요.
3. 로그인 후 [첫 화면]으로 이동해 주세요.
4. 화면이 보이면 "로그인 완료"라고 말해 주세요.

제가 확인할 범위는 읽기 전용입니다. 성과표, 캠페인 상태, 추적 경고만 보고 예산/입찰/ON-OFF/저장 버튼은 누르지 않겠습니다.
```

## Examples

### Example 1

User:

```text
인스타 광고 성과를 보고 싶어요.
```

Response:

```text
그럼 Meta Ads Manager부터 보면 됩니다.

1. https://adsmanager.facebook.com/ 를 열어주세요.
2. 광고계정 권한이 있는 Facebook/Meta 계정으로 직접 로그인해 주세요.
3. Campaigns 화면이 보이면 "로그인 완료"라고 말해 주세요.

읽기 전용으로 캠페인/광고세트/광고 성과표와 Pixel/CAPI 경고만 확인하겠습니다.
```

### Example 2

User:

```text
네이버에서 검색하면 뜨는 광고를 봐야 해요.
```

Response:

```text
네이버 검색광고 화면을 보면 됩니다.

1. https://searchad.naver.com/ 를 열어주세요.
2. 네이버 검색광고 광고주 계정으로 직접 로그인해 주세요.
3. 광고관리 또는 캠페인/키워드 성과 화면으로 이동해 주세요.
4. 화면이 보이면 "로그인 완료"라고 말해 주세요.

읽기 전용으로 비용, 노출수, 클릭수, 전환, CPA/ROAS, 키워드 상태를 확인하겠습니다.
```

### Example 3

User:

```text
쿠팡에서 광고비가 많이 나가는데 뭐가 문제인지 모르겠어요.
```

Response:

```text
쿠팡 상품광고 성과부터 보는 게 좋습니다.

1. https://ads.coupang.com/ 를 열어주세요.
2. 광고 권한이 있는 쿠팡 판매자/공급자 계정으로 직접 로그인해 주세요.
3. 광고관리 또는 상품별 성과 화면으로 이동해 주세요.
4. 화면이 보이면 "로그인 완료"라고 말해 주세요.

읽기 전용으로 상품별 광고비, 매출, ROAS, 품절/아이템위너/예산 경고를 확인하겠습니다.
```

## Security Reminder

If the user shares an email link, shortened URL, or suspicious support link, do not use it. Ask them to open the official platform URL directly from the table above.
