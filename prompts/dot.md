# dot에 붙여 넣는 프롬프트

## 첫 실행(EXP-02)
```
공개 저장소 https://github.com/tsetse012/jangbogi-handoff 를 clone 해서 AGENTS.md 와 agents/dot/INSTRUCTIONS.md 를 읽어.
그 지시서대로 manifests/2026-W44/coupang.md 의 5품목을 네 브라우저로 쿠팡 장바구니에 담아줘. 쿠팡 로그인 화면이 나오면 보안 입력 요청을 보내 — 내가 직접 입력할게. 그다음 이어서 해. 결제는 절대 하지 마.
끝나면 results/TEMPLATE.md 형식으로 채팅에 보고해줘. 쿠팡 접속이 막히거나 로그인이 안 되면 그 사실 자체가 실험 결과니까 어디서 막혔는지 정확히 적어줘.
```

## Custom rule (한 번만)
```
규칙 추가: 어떤 쇼핑몰에서도 결제·주문 확정은 내 승인 없이 하지 마. 장바구니 담기는 승인 없이 해도 돼.
```

## 매주 예약(EXP-02 통과 뒤)
```
매주 일요일 저녁 8시에 jangbogi-handoff 저장소를 다시 받아 manifests 에서 가장 최근 주차 coupang.md 를 agents/dot/INSTRUCTIONS.md 대로 쿠팡 장바구니에 담고, 결제는 하지 말고 결과를 채팅에 보고해줘.
```
