# Carl / ProRealAlgos — Touch & Turn Scalper

## Forrás

[This 1 Minute Scalping Strategy Works Everyday — ProRealAlgos](https://www.youtube.com/watch?v=BifyQ6ppdLU), Carl bemutatója, kb. 20 perc. A szabályok a videó angol automatikus átiratából származnak; az átiratban előfordulhatnak félrehallások. **Ez a videó Carl stratégiája, az AdrianOlajos Telegram-profilhoz való kapcsolat nincs igazolva.**

## A videóban bemutatott szabályok

1. A vizsgált instrumentum rendes piacnyitása után várja meg az első **15 perces gyertya** zárását. Jelölje annak maximumát és minimumát; Fibonacci-szinteket ezen a tartományon rajzolja fel.
2. D1-en az **ATR(14)** értékével szűr: az első M15 gyertya `high − low` mérete legalább `0,25 × D1 ATR(14)` legyen. A készítő ezt „liquidity/manipulation candle”-nek nevezi; ez a neve, nem bizonyíték intézményi manipulációra.
3. Ha az első M15 gyertya csökkenő, **buy limit** a gyertya minimumán; ha emelkedő, **sell limit** a maximumán. Belépés csak a nyitástól számított első **90 percben**. M1 idősíkot használ a megbízás kezeléséhez; a belépőár az M15 range széle.
4. Az átirat példája szerint csökkenő nyitógyertya esetén TP a tartomány aljától a teteje felé mért **38,2%**-os szint; emelkedő esetén a videó **61,8%**-os szintet nevez meg a magasról alacsony felé rajzolt Fibonacci-skálán. Ez a két rajzolási irány ugyanazt az arányos távolságot adhatja a belépő széltől, de MT5-ben külön ellenőrizni kell a rajzolási konvenciót.
5. A stop távolsága a belépő és TP közötti távolság **fele**, célzott hozam/kockázat **2:1**. A stop a tartományon kívülre kerül. A készítő egy nyertes és vesztes példát is mutat; az elmondott találati arány nem független backtest.

## MT5-teszt előtt eldöntendő

- Tőzsdei nyitás pontos időzónája, a nyitó gyertya és a DST kezelése; BTC/forex napi nyitásra nem szabad automatikusan átültetni.
- ATR(14) csak lezárt D1 gyertyákból vagy az aktuális nap részleges adataival? Előbbit kell megfontolni az előretekintési hiba elkerülésére.
- Az ATR-küszöb `>=` vagy `>`; az átirat mindkét kifejezést használja, ezért előzetesen rögzíteni kell a teszt szabályát.
- Limit megbízás törlése 90 percnél, legfeljebb napi hány belépő, és mi történik gap/spread/slippage esetén.
- Azonnali újrateszt az első M15 gyertya zárásakor: ha az ár már a kiválasztott szélen van, a limit teljesíthetősége függ a valós bid/ask ártól.
- Külön eredmények instrumentumonként, jutalékkal és valós kereskedési idővel.

## Backtest log

| Dátum | Instrumentum | Időszak | Kötések | Nettó | Profit faktor | Max. DD | Megjegyzés |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 2026-09-28 | — | — | — | — | — | — | Saját backtest még nem érkezett. |
