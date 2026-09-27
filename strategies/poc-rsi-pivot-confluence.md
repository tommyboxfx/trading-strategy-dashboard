# POC + RSI Divergence + Pivot Confluence

**Állapot: kutatási ötlet.** A három összetevőből önmagában nem következik előny. Az együttállást csak azonos napok és azonos kilépések mellett szabad a kevesebb feltételt tartalmazó alaphoz hasonlítani.

## Kezdeti long / short hipotézis

1. **Long:** az előző kész session POC-ja vagy VAL-ja legfeljebb előre kijelölt ATR-távolságra van a napi S1-től vagy heti/havi pivot-szinttől; ár leszúr alá és visszazár.
2. Megerősített **regular bullish RSI divergencia:** új, alacsonyabb ár-pivot low és magasabb RSI-pivot low, ugyanazzal az előre beállított RSI-időszakkal és pivotbal/pivotjobb gyertyaszámmal. A jelzés legkorábbi ideje a jobb oldali megerősítő gyertyák zárása.
3. Opció: bullish M5 MSS vagy POC visszafoglalása; a belépés/stop/célár külön verzióként rögzítendő. Shortnál tükrözött szabályok: VAH/POC + R1, magasabb high és alacsonyabb RSI high.

## Hozzáadott érték lépcsőzetes tesztje

| A | B | C | D |
|---|---|---|---|
| Szintreakció önmagában | + lezárt POC/VAH/VAL | + megerősített divergencia | + MSS |

Ugyanazon instrumentum, időszak, session, belépés, stop és TP mellett hasonlítsuk az A→B→C→D változatot, és vezessük azt is, hány jelzés marad. A „confluence” távolságát ATR/tick alapján előre határozzuk meg, ne utólag szemre. A pivot önmagában lehet hatástalan: [Lund University FX-vizsgálat](https://www.lunduniversity.lu.se/publication/8979805). A divergenciát a [TradingView](https://www.tradingview.com/support/solutions/43000589127-rsi-divergence-indicator/) is megerősítést igénylő jelként írja le. A POC/VA a [TradingView definíciója](https://www.tradingview.com/support/solutions/43000502040-volume-profile-indicators-basic-concepts/) szerint profilfüggő.

## Nyitott kérdések

Melyik piac és feed az első? Előző napi SVP vagy lezárt heti fixed-range POC? Regular vs hidden RSI divergencia? Trend- vagy countertrend-környezet? Az NY open körüli setupot külön kezeljük az egész napos stratégiától. Ezekre az adatokhoz igazodva, előre rögzített első tesztváltozatot választunk.

## Backtest log

| Dátum | Variáns | Piac / TF | Időszak | Kötések | PF | Max DD | Avg R | OOS / forward | Megjegyzés |
|---|---|---|---|---:|---:|---:|---:|---|---|
| 2026-09-27 | Kutatási vázlat | — | — | — | — | — | — | — | Saját eredmény nincs. |
