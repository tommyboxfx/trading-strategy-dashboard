# Den / LastOrangePuma — PVP POC + RSI konfluencia

## Forrásállapot

A tulajdonos által 2026-10-03-án átadott „Multi Timefirame Periodic Volume Profile POC (Den)Stratregia.docx” alapján készült összefoglaló. A szabályok így már dokumentáltak, de a dokumentum eredete és a készítő hivatalos szabálykönyvével való egyezése nincs külön ellenőrizve. Saját backtest még nincs; az erős POC-ra, magas találati arányra és megbízhatóbb idősíkokra vonatkozó állítások a forrás véleményei.

## Indikátorok és két külön variáns

- Fő grafikon: Multi-Timeframe Periodic Volume Profile — PVP POC; a dokumentum napi vagy heti profilokat említ.
- RSI-panel: RSI és rá alkalmazott Divergences and Alerts. A pontos script-verzió, RSI-paraméter és a panelre helyezés technikai módja ellenőrzendő.
- Korábban megadott nevek: `8LIW/Div`, `8LIQ/Golden Pocket`, `8LIQ/PVP POC`. Ezek megfeleltetése a dokumentum indikátorneveinek még nem igazolt. Golden Pocket nem szerepel kötelező belépési szűrőként.

A dokumentum két eltérő belépési rendszert ír le. Ezeket külön kell tesztelni, mert az egyik gyertyazárást vár, a másik érintéskor lép be.

## A variáns — POC + klasszikus divergencia + gyertyamegerősítés

| Feltétel | Long | Short |
| --- | --- | --- |
| Helyszín | Fontos POC az ár alatt, teszt vagy enyhe alászúrás | Fontos POC az ár felett, teszt |
| Divergencia | Ár alacsonyabb mélypont, RSI magasabb mélypont | Ár magasabb csúcs, RSI alacsonyabb csúcs |
| Megerősítés | Bullish engulfing, hammer vagy határozott zárás POC fölött | Bearish engulfing, shooting star vagy határozott zárás POC alatt |
| Belépés | Megerősítő gyertya zárása után | Megerősítő gyertya zárása után |
| Stop | Divergenciás swing low alatt | Divergenciás swing high fölött |
| Cél | Következő felső POC; alternatív ellenállás/korábbi csúcs vagy 2R/3R | Következő alsó POC; alternatív támasz/korábbi mélypont |

Az első rész H1/H4/D1 idősíkokat említ. Korábbi napi, heti vagy érintetlen (naked) POC is választható; a kiválasztás és az érintetlenség pontos definíciója hiányzik. A stop elhelyezése nem garantál kis veszteséget: a veszteség a méretezéstől és a teljesüléstől is függ.

## B variáns — M15 RSI 70/30 → második fraktál → POC-érintés

Elsődleges idősík M15; M1/M5/M30 kontextusként szerepel, konkrét szűrési szabály nélkül.

| Lépés | Long | Short |
| --- | --- | --- |
| 1. Trigger | RSI 30 alá kerül, első mélypont | RSI 70 fölé kerül, első csúcs |
| 2. Trigger | RSI vissza 30 fölé, majd magasabb második mélypont | RSI vissza 70 alá, majd alacsonyabb második csúcs |
| Újraindítás | Alacsonyabb második mélypont érvénytelenít; ez lesz az új első mélypont | Magasabb második csúcs érvénytelenít; ez lesz az új első csúcs |
| Belépés | A két trigger után az alsó legközelebbi POC érintése | A két trigger után a felső legközelebbi POC érintése; kis tolerancia megengedett |
| Kilépési lehetőség | RSI felfelé keresztezi az 50-et | RSI lefelé keresztezi az 50-et |

**Lényeges eltérés:** a B variáns két RSI-swinget ír le, de az ár megfelelő alacsonyabb mélypontját/magasabb csúcsát nem követeli meg kifejezetten. Ez önmagában nem igazolja a klasszikus ár–RSI divergenciát. Az A variáns feltételét nem adjuk hozzá automatikusan.

A B rész Fibonacci 61,8% retracement, 100%/161,8% extension és BTC-nél 88,6% szintet említ alternatív célként. A Fibonacci horgonypontok és a célok közötti választás hiányzik. A B variáns önálló stop-szabályt nem ad; az A swing-stop átvétele külön teszthipotézis lenne.

## Automatizálás előtt pontosítandó

1. RSI periódus/árforrás; melyik idősík RSI-ja adja a triggert és az 50-es kilépőt?
2. RSI-fraktál bal/jobb oldali gyertyaszáma, megerősítési késése, egyenlő swingek kezelése. A jel csak akkor használható, amikor ténylegesen ismert.
3. Lezárt napi/heti vagy folyamatosan változó POC? Profil időzónája, volume-forrása, árbinjei; meddig él a naked POC?
4. A POC kiválasztásának időpontja, tolerancia tickben/pontban, újrateszt, jel lejárata és maximális belépésszám.
5. Az A gyertyamintáinak objektív definíciója; a B hiányzó stopja, pozícióméret és a Fibonacci horgonypontok.
6. Melyik célár/kilépési mód az alapváltozat? BE, részleges zárás, hírek és session-szűrés nincs meghatározva.

## Backtest log

| Dátum | Variáns | Piac / TF | Időszak | Kötések | PF | Max DD | Avg R | OOS / forward | Megjegyzés |
|---|---|---|---|---:|---:|---:|---:|---|---|
| 2026-09-27 | Nevek rögzítve | — | — | — | — | — | — | — | Logika és eredmények még hiányoznak. |
| 2026-10-03 | A és B dokumentálva | H1/H4/D1; M15 | — | — | — | — | — | — | Feltöltött leírás alapján; paraméterek és tesztek még hiányoznak. |
