# Den / LastOrangePuma — három TradingView indikátor

**Forrásállapot:** az alábbi neveket a dashboard tulajdonosa adta meg. Az indikátorok teljes leírását, pontos paramétereit és Den belépési/kilépési szabályait még nem sikerült ellenőrizni. A Whop-oldal vagy indikátorképek később hozzáadhatók. Ez a bejegyzés nyilvántartás, nem teljes stratégiaspecifikáció vagy teljesítményállítás.

## Az általa használt indikátorok

1. `8LIW/Div` — a pontos jelzés és divergenciatípus még tisztázandó.
2. `8LIQ/Golden Pocket` — a Fibonacci-tartomány és annak számítási pontjai még tisztázandók.
3. `8LIQ/PVP POC` — a profil időkerete, a POC számítása és a jelszabály még tisztázandó.

A nevekből nem következtetünk automatikusan konkrét belépési feltételekre. Egy [nyilvános TradingView-fórumban](https://www.reddit.com/r/TradingView/comments/1py0p3u/multitimeframe_periodic_volume_profile_pvp_poc/) említik a PVP POC nevet és lehetséges készítőként a LastOrangePuma profilt, de ez közvetett utalás, nem az indikátor hivatalos dokumentációja.

## A pontos stratégia rögzítéséhez

- Melyik indikátor adja a kontextust, melyik a trigger, és mindhárom szükséges-e ugyanazon gyertyán?
- Piac, idősík, session és indikátorbeállítások; regular/hidden divergencia és jelzés megerősítési késése.
- Golden Pocket kezdő/végpontja, PVP profil lezárása és a POC melyik időpillanatban ismert.
- Long és short feltételek, stop, célár, BE, érvénytelenítés, spread/slippage.
- Külön összehasonlítás: egyes indikátorok → kettős kombinációk → teljes háromszűrős setup.

## Backtest log

| Dátum | Variáns | Piac / TF | Időszak | Kötések | PF | Max DD | Avg R | OOS / forward | Megjegyzés |
|---|---|---|---|---:|---:|---:|---:|---|---|
| 2026-09-27 | Nevek rögzítve | — | — | — | — | — | — | — | Logika és eredmények még hiányoznak. |
