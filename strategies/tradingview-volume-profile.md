# TradingView Volume Profile: POC / VAH / VAL / HVN / LVN

**Állapot: kutatási ötlet.** A POC a kiválasztott profil legnagyobb forgalmú ársora, a VAH/VAL az értékterület szélei. A TradingView-ban a value area tipikus alapértéke 70%. [Hivatalos fogalmak és példa](https://www.tradingview.com/support/solutions/43000502040-volume-profile-indicators-basic-concepts/).

## Tesztelhető profilok és ötletek

1. **Előző session POC retest:** a tegnapi kész SVP POC érintése után elutasítás vagy elfogadás; külön az első és a többszöri érintés. Cél lehet a VAH/VAL, de minden kilépést külön mérünk.
2. **VAL/VAH visszatérés az értékterületbe:** ár kívülre kerül, majd visszazár; a POC csak előre kijelölt cél, nem garantált mágnes. Összevetés az ugyanott bekövetkező folytatásos áttöréssel.
3. **Value-area breakout és retest:** kész előző napi VAH/VAL áttörése, retest és folytatás. NY nyitás körül külön vizsgálható.
4. **LVN gyors átmenet → következő HVN:** előre rögzített, lezárt fixed-range profil két csomópontja között; cél és stop csak a jelzéskor ismert adatokból.
5. **NY nyitás a tegnapi value area fölött/alatt:** a TradingView példája szerint a POC felé történő visszahúzódás és az eredeti irányba fordulás egy lehetséges hipotézis; ezt külön mérjük a nyitás utáni trendfolytatással.

## Profilválasztás és reprodukálhatóság

- [Session Volume Profile](https://www.tradingview.com/support/solutions/43000703072-session-volume-profile/): előző lezárt sessionből számolt szint; szükséges a fő/piac előtti/utáni kereskedési idő pontos kijelölése.
- [Fixed Range Volume Profile](https://www.tradingview.com/support/solutions/43000707985-fixed-range-volume-profile-drawing-tool/): előre rögzített kezdő- és végpont, például lezárt Asia-session vagy előző hét. A vizsgált gyertyánál későbbi adat nem szerepelhet benne.
- [Visible Range Volume Profile](https://www.tradingview.com/support/solutions/43000703076-visible-range-volume-profile/): a látható charttartománytól függ; kézi ötletkereséshez jó, automatizált historikus teszthez csak rögzített, időben reprodukálható ablakra cserélve használjuk.
- Developing POC csak az adott időpontig felépült profillal tesztelhető. A kész napi POC-val nem lehet a nap korábbi pontján belépést szimulálni.

TradingView részvényeknél kereskedési volument, index/forex/crypto CFD-nél tick volument, kriptónál base/quote volument használhat. Az MT5 broker volume-ja és a TradingView feedje eltérhet; XAUUSD, US100 és BTCUSD nem automatikusan ugyanazt a POC-t adja. A row size, value-area százalék, timeframe és időzóna legyen rögzítve. Ez adatdefiníció, nem önálló nyereségbizonyíték.

## Harlan Sterling két videójából kinyert tesztötlet

**1. [Swing POC pullback](https://www.youtube.com/watch?v=hQQI9DlhDRw):** a bemutató először a swing-struktúrából állapítja meg a trendirányt. Eső trendnél Fixed Range Volume Profile a legutóbbi swing hightól a swing lowig; az erre számított POC-hoz történő visszahúzódás és „tiszta reakció” után short. Emelkedő trendnél swing low→swing high profil, POC-visszahúzódás és long reakció. A videó nem definiálja számszerűen a swing megerősítését, a reakciót, stopot vagy célárat. Tesztben a profil végpontját és a jelzés legkorábbi idejét előre rögzítsük, hogy a később kialakult swing low/high ne szivárogjon vissza a múltbeli belépésbe.

**2. [Előző napi profil](https://www.youtube.com/watch?v=Im26BW44IDg):** a bemutató TradingView M15 charton bekapcsolja a session break jelölést, majd Fixed Range Volume Profile-t húz az előző teljes kereskedési napra. A kész POC, VAL, VAH visszatesztjénél a nagyobb idősík irányával egyező reakciót keresi. A videó példát mutat, nem teljes mechanikus stratégiát. Előbb külön mérjük a POC/VAL/VAH szintet, majd a HTF bias hozzáadott értékét, azonos stop és kilépés mellett.

**Forrásminőség:** oktató rövidvideók, saját tesztkimutatás nélkül. Az első videó végén elhangzó promóciós win-rate állítást nem tekintjük ellenőrzött eredménynek, ezért a dashboard eredménymezői üresek maradnak.

## Backtest log

| Dátum | Variáns | Piac / profil | Időszak | Kötések | PF | Max DD | Avg R | OOS / forward | Megjegyzés |
|---|---|---|---|---:|---:|---:|---:|---|---|
| 2026-09-27 | Kutatási vázlat | — | — | — | — | — | — | — | Saját eredmény nincs. |
