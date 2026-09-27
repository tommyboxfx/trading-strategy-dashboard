# Daily / Weekly / Monthly Pivot Strategies

**Állapot: kutatási ötlet.** Saját mérési eredmény még nincs. A pivot itt számított támasz/ellenállás, nem a ZigZag swing-pivotja.

## Mit számolunk?

Traditional P = (előző időszak H + L + C) / 3; R1 = 2P − L; S1 = 2P − H; R2 = P + (H − L); S2 = P − (H − L). Napi, heti és havi szinthez mindig a már lezárt előző nap/hét/hónap adatait használjuk. A Traditional, Fibonacci, Camarilla és Woodie külön módszer, így ezeket nem szabad egy tesztben összekeverni. [TradingView pivotképletek és beállítások](https://www.tradingview.com/support/solutions/43000521824-pivot-points-standard/).

## Önállóan tesztelhető hipotézisek

1. **Napi S1/R1 visszafordulás:** érintés vagy kis átszúrás, M5 zárás a szint belső oldalán, belépés csak megerősítés után; összevetés puszta érintéssel.
2. **Heti pivot reclaim:** először átmegy a heti P szinten, majd M15 gyertyával visszazár és retestet ad. Külön long/short és hét napja szerinti mérés.
3. **Havi R1/S1 áttörés és retest:** egymástól külön vizsgálni a megerősített áttörést és a fals kitörés utáni visszafordulást.
4. **D/W/M szinttorlódás:** például heti P és napi S1/R1 előre meghatározott távolságon belül. A torlódás hozzáadott értékét ugyanazon napok egyetlen szintjéhez mérjük.

## Rögzítendő szabályok

TradingView: kézzel beállított Daily/Weekly/Monthly, Traditional típus, „Use Daily-based Values” állapota. MT5: azonos instrumentum és session OHLC-je, szerveridő, hét/hónap határa, futures settlement vagy utolsó kötés, CFD esetén brokeradat. Szinttolerancia ATR-ben vagy tickben; stop, célár, időablak, költség és hírablak előre rögzítve. A TradingView dokumentációja szerint a daily-based és intraday adatok eltérhetnek, ezért a platformok közti egyezést ellenőrizni kell.

Egy [2019-es lund-i FX mesterszakos kutatás](https://www.lunduniversity.lu.se/publication/8979805) nem talált támogatást a hagyományos pivot-reakció általános prediktív erejére három devizapár mintáján. Ez indokolja, hogy a reakciós és az áttöréses irányt egyaránt vizsgáljuk; nem eredmény a mi piacainkra.

## Backtest log

| Dátum | Variáns | Piac / TF | Időszak | Kötések | PF | Max DD | Avg R | OOS / forward | Megjegyzés |
|---|---|---|---|---:|---:|---:|---:|---|---|
| 2026-09-27 | Kutatási vázlat | — | — | — | — | — | — | — | Saját eredmény nincs. |
