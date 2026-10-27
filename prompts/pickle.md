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
