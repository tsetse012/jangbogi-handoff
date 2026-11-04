# 피클에 붙여 넣는 프롬프트

## 첫 실행(EXP-01)
```
깃허브 저장소 tsetse012/jangbogi-handoff 를 열어서 AGENTS.md 와 agents/pickle/INSTRUCTIONS.md 를 읽어. 저장소가 안 열리면 https://raw.githubusercontent.com/tsetse012/jangbogi-handoff/main/agents/pickle/INSTRUCTIONS.md 로 읽어.
그 지시서대로 manifests/2026-W44/coupang.md 명세서의 5품목을 쿠팡 장바구니에 담아줘. 결제는 절대 하지 말고, 담기만 하고 결과를 results/TEMPLATE.md 형식으로 보고해줘.
```

## 다음 주부터(명세서만 바꿀 때)
```
jangbogi-handoff 저장소의 manifests/<주차>/coupang.md 를 agents/pickle/INSTRUCTIONS.md 대로 쿠팡에 담아줘. 결제 금지, 담기만. 끝나면 TEMPLATE 형식으로 보고.
```

## 매주 예약(L2, EXP-01 통과 뒤)
```
매주 일요일 저녁 8시에 jangbogi-handoff 저장소 manifests 폴더에서 가장 최근 주차의 coupang.md 를 agents/pickle/INSTRUCTIONS.md 대로 쿠팡 장바구니에 담고, 결제는 하지 말고 결과를 보고해줘.
```

## 가격 조사 — 4몰(2026-11-01~, 담지 않음)
쇼핑몰(`컬리`·`이마트몰`·`네이버 컬리N마트`·`쿠팡`) × 목록(`a`·`b`)마다 **따로 한 번씩** 돌린다. 한 번에 한 몰·한 목록.
```
깃허브 저장소 tsetse012/jangbogi-handoff 를 열어서 AGENTS.md 와 agents/pickle/PRICECHECK.md 를 읽어. 저장소가 안 열리면 https://raw.githubusercontent.com/tsetse012/jangbogi-handoff/main/agents/pickle/PRICECHECK.md 로 읽어.
이번 쇼핑몰은 「컬리」, 조사 목록은 manifests/pricecheck/2026-10-30-top50-a.md 야. PRICECHECK.md 의 「쇼핑몰별 표」에서 컬리 줄의 사이트·고르는 순서·delivery 값만 써서 25행 가격을 조사해줘.
장바구니 담기·결제·멤버십 가입은 하지 마. 끝나면 본문은 짧게(배송비 안내 문구 원문 한 줄 포함), 맨 끝에 json 코드블록 정확히 1개로 보고해줘.
```

## 컬리 장바구니 담기 — 계산 총액 검증(EXP-03, 2026-11-02~)
담기만 하고 결제·주문서 진입은 하지 않는다. 장바구니 화면 금액을 그대로 읽어 오는 게 목적.
```
깃허브 저장소 tsetse012/jangbogi-handoff 를 열어서 AGENTS.md 와 agents/pickle/CART-KURLY.md 를 읽어. 저장소가 안 열리면 https://raw.githubusercontent.com/tsetse012/jangbogi-handoff/main/agents/pickle/CART-KURLY.md 로 읽어.
그 지시서대로 manifests/2026-W45/kurly.md 명세서의 5품목을 컬리 장바구니에 담아줘. 담기 전에 장바구니에 이미 있는 상품은 지우지 말고 적어만 둬. 「주문하기」는 누르지 마. 끝나면 장바구니 금액 요약 칸의 모든 줄을 화면 그대로 적고, 맨 끝에 json 코드블록 정확히 1개로 보고해줘.
```

## 이마트몰 장바구니 담기 — 계산 총액 검증(EXP-04, 2026-11-02~)
담기만 하고 결제·주문서 진입·배송 시간 선택은 하지 않는다. 장바구니 화면 금액을 그대로 읽어 오는 게 목적.
```
깃허브 저장소 tsetse012/jangbogi-handoff 를 열어서 AGENTS.md 와 agents/pickle/CART-EMART.md 를 읽어. 저장소가 안 열리면 https://raw.githubusercontent.com/tsetse012/jangbogi-handoff/main/agents/pickle/CART-EMART.md 로 읽어.
그 지시서대로 manifests/2026-W45/emart.md 명세서의 4품목을 이마트몰(SSG닷컴) 장바구니에 담아줘. 담기 전에 장바구니에 이미 있는 상품은 지우지 말고 적어만 둬. 「주문하기」는 누르지 말고 배송 시간도 고르지 마. 끝나면 장바구니 금액 요약 칸의 모든 줄을 화면 그대로 적고, 맨 끝에 json 코드블록 정확히 1개로 보고해줘.
```

## 남은 재료 왕복(2026-11-04~) — 명세서 끝 「다음 주 요청서에 붙일 재고」 블록이 있을 때
담은 뒤 같은 대화에 이어서(또는 다음 주에) 붙인다. 피클은 메모리가 있으니 블록 보관을 맡긴다.
```
방금 명세서 맨 끝 「다음 주 요청서에 붙일 재고」 json 블록을 값 그대로 기억해 둬. 다음 주에 내가 장보기 얘기를 꺼내면 먼저 그 블록의 재료마다 하나씩 「지난주 남은 감자 640g — 지금 얼마나 남았어요?」처럼 물어봐. 숫자가 아닌 답(반쯤·조금)은 g 나 개로 다시 묻고, 블록에 없는 재료는 넣지 마. 다 물으면 {"on_hand": [{"key": "potato", "qty": 숫자, "unit": "g"}]} 형식 json 코드블록 1개로 줘 — 0 인 재료는 빼고, key·unit 은 블록 그대로.
```
