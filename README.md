# MACRO TERMINAL 📡

> NASA Mission Control 스타일 글로벌 매크로 금융 대시보드  
> 100% TradingView 실시간 위젯 기반 · 하드코딩 제로

---

## 🚀 GitHub Pages 배포 방법

### 1. 저장소 생성
```bash
# macro-terminal.html → index.html 로 이름 변경 후 업로드
git init
git add index.html README.md
git commit -m "feat: initial macro terminal dashboard"
git push origin main
```

### 2. GitHub Pages 활성화
1. Repository → **Settings** → **Pages**
2. Source: **Deploy from a branch**
3. Branch: `main` / folder: `/ (root)`
4. Save → `https://[username].github.io/[repo-name]/` 접속

---

## 📊 포함된 패널 구성

| # | 섹션 | 위젯 |
|---|------|------|
| 01 | 한국 증시 (KOSPI · KOSDAQ) | symbol-overview + news |
| 02 | 미국 증시 (S&P500 · NASDAQ · DOW · Sectors) | mini-overview + market-overview |
| 03 | **코스톨라니 달걀** 사이클 분석 | SVG + US10Y · VIX · DXY · GOLD |
| 04 | 글로벌 자금흐름 히트맵 | stock-heatmap (US/KR/Crypto) |
| 05 | 외환 (USD/KRW · JPY · CNY · EUR) | forex-cross-rates + currency-rates |
| 06 | 경제 캘린더 | events (US/KR/JP/CN/EU) |
| 07 | 원자재 & 채권 | Gold · Oil · US10Y · BTC |

---

## 🔧 커스터마이징 가이드

### 테마 변경 — CSS 변수 (`:root` 블록)
```css
:root {
  --bg-void: #03050d;     /* 전체 배경 */
  --cyan:    #00d4ff;     /* 주요 액센트 색상 */
  --green:   #00ffa3;     /* 상승/긍정 신호 */
  --amber:   #ffae00;     /* 경고/중립 신호 */
  --red:     #ff4d6d;     /* 하락/위험 신호 */
}
```

### 심볼 변경
TradingView 심볼 형식: `EXCHANGE:SYMBOL`
| 예시 | 심볼 |
|------|------|
| 삼성전자 | `KRX:005930` |
| KODEX 200 ETF | `KRX:069500` |
| Apple | `NASDAQ:AAPL` |
| Tesla | `NASDAQ:TSLA` |
| 달러인덱스 | `TVC:DXY` |

### 코스톨라니 달걀 현재 위치 설정
`setEggPhase()` 초기 호출 또는 `EGG_POSITIONS` 에서 좌표 조정:
```javascript
const EGG_POSITIONS = {
  A: { cx: 120, cy: 140 },  // 하강국면 (좌상단)
  B: { cx: 110, cy: 310 },  // 침체국면 (좌하단)
  C: { cx: 290, cy: 310 },  // 회복국면 (우하단) ← 현재 기본값
  D: { cx: 290, cy: 130 }   // 호황국면 (우상단)
};
```

### 섹션 추가
각 섹션은 `<!-- ── SECTION: NAME ── -->` 주석으로 구분됩니다.
패널 구조:
```html
<div class="panel span-2">          <!-- span-2: 2열 차지, 기본: 1열 -->
  <div class="panel-header">...</div>
  <div class="panel-body">
    <div class="widget-wrap h-400"> <!-- h-300~500: 높이 클래스 -->
      <!-- TradingView 위젯 삽입 -->
    </div>
  </div>
</div>
```

---

## ⚠️ 주의사항

- TradingView 위젯은 **인터넷 연결 필수** (GitHub Pages 배포 시 정상 작동)
- 로컬 `file://` 로 열면 일부 위젯이 CORS로 차단될 수 있음 → **반드시 서버 배포**
- 투자 조언이 아님. 최종 판단은 본인 책임

---

*Powered by [TradingView Widgets](https://www.tradingview.com/widget/)*
