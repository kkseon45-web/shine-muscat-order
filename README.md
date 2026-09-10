# 부모님표 샤인머스켓 주문 페이지

`index.html` 하나와 `img/` 폴더로 이루어진 정적 페이지입니다. 서버 없이 GitHub Pages에 그대로 올리면 됩니다.

## GitHub Pages로 올리기 (5분)

1. github.com 에서 새 저장소 만들기 → 이름 예: `shine-muscat` (Public)
2. 이 폴더의 `index.html`, `img/` 를 업로드 (웹에서 "Add file → Upload files" 로 드래그해도 됩니다)
3. 저장소 **Settings → Pages → Branch: main / (root)** → Save
4. 1~2분 뒤 `https://<깃허브아이디>.github.io/shine-muscat/` 주소가 열립니다
5. 이 주소를 카톡으로 뿌리면 끝. 카톡 미리보기에 사진과 가격이 같이 뜹니다.

터미널로 하려면:

```bash
cd ~/shine-muscat
git init && git add . && git commit -m "샤인머스켓 주문 페이지"
git branch -M main
git remote add origin https://github.com/<깃허브아이디>/shine-muscat.git
git push -u origin main
```

그 다음 3번(Settings → Pages)만 해주면 됩니다.

## 가격·연락처 바꾸기

`index.html` 맨 아래 `<script>` 안 "설정" 블록만 고치면 계산기와 주문 문자가 같이 바뀝니다.

```js
var PHONE   = '010-3517-3194';   // 주문 문자·전화 받는 번호
var PRICE   = 12000;             // 1박스 가격
function shippingFee(q){         // 택배비 규칙
  if(q >= 4) return 5000;
  if(q >= 2) return 4000;
  return 3000;
}
```

가격 표시 부분(12,000원, 택배비 표)은 화면 글자라서 `index.html` 의 `price-band` 섹션에서 숫자를 같이 바꿔주세요.
계좌번호는 `입금 안내` 섹션과 `copyAcct` 버튼의 숫자 두 곳에 있습니다.

## 주문 흐름

- 수량 +/- → 상품 금액 + 택배비 = 입금 금액이 자동 계산됩니다 (하단 고정 바에도 표시)
- 받는 분·주소·연락처·입금자명 입력 → **문자로 주문 보내기** 를 누르면 문자 앱이 내용이 채워진 채로 열립니다
- 카톡으로 보내는 사람은 **카톡으로 보내기** → 내용이 복사되고, 카톡에 붙여넣기만 하면 됩니다
- 컴퓨터처럼 문자 앱이 없는 환경에서는 자동으로 내용이 복사되고 번호를 안내합니다
- **계좌번호 복사** 버튼으로 계좌를 바로 복사할 수 있습니다
