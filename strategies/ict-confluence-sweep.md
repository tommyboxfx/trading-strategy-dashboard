# ICT stratégiák — Sweep, FVG, BPR és időablakok

**Állapot:** kutatási ötlet. Nincs hozzáadott, ellenőrzött teljesítményeredmény. Frissítve: 2026-10-03.

## Kutatási cél és sorrend

Önálló ICT-szekció a meglévő NY-open, PDH/PDL és HTF sweep stratégiák mellett. A cél kevés, szigorúan kiválasztott setup. A „legjobb” itt a meglévő rendszerekhez való illeszkedést és a szabályok tesztelhetőségét jelenti; nyereségességi rangsort eredmények nélkül nem állítunk.

1. **Sweep → displacement/MSS → FVG**: egyszerű összehasonlítási alap.
2. **Sweep → ellenirányú displacement → BPR → első visszatérés**: kiemelt új setup a tulajdonos kérésére.
3. **Silver Bullet időszűrő**: külön London/NY AM/NY PM változatok.
4. **OTE vagy Order Block**: külön helyszínszűrők, nem automatikusan mind egyszerre.
5. **SMT / PO3 / IFVG / breaker**: későbbi bővítések, külön specifikációval.

Ez kutatási sorrend, nem bizonyított teljesítményrangsor. A BPR nem szükségszerűen jobb a sima FVG-nél.

## Ellenőrzött források és korlátok

- [A küldött Shorts: ICT Tip — Balanced Price Range (BPR)](https://www.youtube.com/shorts/SBmYQO3knKU). A keresőben a cím azonosítható; a videó és teljes felirata nem volt hozzáférhető. A konkrét stopot, belépőt vagy chartpéldát nem tulajdonítjuk ennek a videónak. A tulajdonos külön megerősítette a BPR témát.
- [ICT Mentorship 2023 — Market Maker Models](https://www.youtube.com/watch?v=iKsIbUblSWM&t=1473s), kb. 24:33–26:59: a szerző ellentétes irányú ármozgás/imbalance átfedésével magyarázza a BPR-t. [A videó beszédének szöveges átirata](https://my.infocaptor.com/hub/summaries/the-inner-circle-trader/ict-mentorship-2023-market-maker-models-iKsIbUblSWM); automatikus átirat, terminológiai hibák lehetnek. Nem teljes vizuális videóelemzés.
- [2022 ICT Mentorship — Episode 6](https://www.youtube.com/watch?v=Bkt8B3kLATQ), [hozzáférhető szöveges összefoglaló](https://glasp.co/youtube/Bkt8B3kLATQ): FVG és a kapcsolódó ármozgás kontextusa.
- [2023 ICT Mentorship — Silver Bullet Time Based Trading Model](https://www.youtube.com/watch?v=tRq1hyGGtl4), [szöveges összefoglaló](https://glasp.co/youtube/tRq1hyGGtl4): New York helyi idő szerinti ablakok és következő célterület.
- [If I Had To Restart Again As A Trader, At 20 Years Old — Part 3](https://www.youtube.com/watch?v=T6YE1CEWsHk), [a szerző beszédének átirata](https://youtubetotranscript.com/transcript?current_language_code=en&v=T6YE1CEWsHk): OTE kontextusa, 62–79% visszahúzódás, struktúra és cél. Nem elegendő önmagában a Fibonacci érintése.

Az ICT magyarázataiban szereplő intézményi szándék, „algorithmic delivery” és stopvadászat szerzői értelmezés. OHLC alapján nem bizonyított, ki kereskedett vagy hol vannak a stopok. A következő mechanikus szabályok saját kutatási specifikációk; nem minden pont eredeti ICT-előírás.

## Alapfogalmak — objektív definíció a teszthez

| Fogalom | Rögzítendő megfigyelés |
| --- | --- |
| Referenciaszint | Előző lezárt nap/hét high-low, vagy előre rögzített session határa. Broker nap és NY nap külön változat. |
| Sweep / reclaim | Az ár a referencia túloldalára kerül, majd meghatározott számú lezárt gyertyán belül visszazár. Minimum túlszúrás és lejárat előre rögzítendő. |
| Displacement | Erős ellenirányú mozgás. A gyertyatest/range ATR-arányát és az elvárt zárási helyet előre választjuk; az „erős” ne utólagos vizuális ítélet legyen. |
| MSS | A sweep előtt már ismert belső swing túloldalára történő zárás. Pivot megerősítési ideje naplózandó; jövőbeli pivot nem használható. |
| FVG | Három lezárt gyertya első és harmadik kanóctartománya közti rés. Bullish: High[1] < Low[3]; bearish: High[3] < Low[1]. |
| Order Block | Saját tesztszabály: utolsó ellenirányú gyertya/csoport a struktúrát törő displacement előtt. Full range vagy body külön változat. |
| Premium / discount | Egy előre kijelölt swing-range felső/alsó fele. A range és az 50%-os határ nem változtatható visszamenőleg. |
| SMT | Két előre kiválasztott piac megfelelő swingje eltér: egyik új szélsőértéket üt, másik nem. Nem RSI/Den-divergencia. |
| PO3 / AMD | Konszolidáció, egyik irányú kitérés, majd ellenirányú terjeszkedés kontextusa; nem minden nap kötelező alakzat. |

## ICT-BPR — kiemelt setup

### Zóna meghatározása

BPR: egy bearish és egy bullish FVG közös ársávja. Ez nem két azonos irányú FVG és nem önmagában oldalazó range.

Időrendben előbb legyen egy irányú FVG, majd ellenirányú FVG. A zóna csak a második FVG harmadik gyertyájának lezárásakor ismert.

Ha a két rés intervalluma [L1,U1] és [L2,U2]:

- **BPR alsó határ = max(L1,L2)**.
- **BPR felső határ = min(U1,U2)**.
- Csak akkor van pozitív szélességű BPR, ha az alsó < felső.
- Közép = (alsó + felső)/2.

Példa: bearish FVG 100–104, későbbi bullish FVG 102–106 → BPR 102–104, közép 103. Ez számolási példa, nem piaci eredmény.

Rögzítendő: azonos idősíkon keresünk-e, maximum hány gyertya lehet a két FVG között, minimum résszélesség, milyen előzetes érintés engedett. Kezdő változatban egy idősíkot használunk; MTF BPR külön modell. A „clean BPR” szűrő csak előre meghatározott érintési szabállyal értelmezhető.

### Long felépítése — short tükrözendő

1. Előre kijelölt PDL/PWL/session-low vagy HTF alsó zóna.
2. Lefelé kitérés/sweep, majd visszazárás a referencia fölé.
3. Bullish displacement; MSS opcionális változatként, az előre ismert belső csúcs fölötti zárással.
4. A bullish FVG átfed egy közeli korábbi bearish FVG-vel.
5. A második FVG lezárása után az ár a BPR fölött van; innen első visszatérés a zónába.
6. Végrehajtás az előre kiválasztott változat szerint; cél az előre kijelölt felső szint.

A short: felső szint sweep → bearish displacement → bullish réssel átfedő bearish FVG → BPR alulról történő visszatesztje. A zóna önmagában nem ad long/short irányt.

### Belépő, stop és cél — saját tesztváltozatok

| Változat | Belépő | Stop | Megjegyzés |
| --- | --- | --- | --- |
| BPR-Limit-Edge | Long a felülről elsőként elért BPR felső szélén; short az alsó szélén | Sweep-extreme túloldala + előre rögzített puffer | Korábbi érintési belépő, potenciálisan gyengébb R; nincs utólagos gyertya-megerősítés |
| BPR-Limit-50 | Limit a BPR közepén | Ugyanaz a strukturális stop | Jobb belépési ár lehet, de több kihagyott trade |
| BPR-Rejection | Lezárt gyertya érinti a zónát és visszazár longnál fölé, shortnál alá; belépő következő elérhető áron | Ugyanaz a strukturális stop | Későbbi ár; spread és slippage számít |
| BPR-ZoneStop | A kiválasztott limitbelépő | Long BPR alja alatt, short teteje felett + puffer | Külön, szűkebb stopkísérlet; nem ugyanaz az invalidáció, mint a sweep-extreme |

Az alsó szélen történő long limit / felső szélen történő short limit további változat lehet, de ne keverjük az elsőként elért szélnél belépővel. Nem kombináljuk a limit korai árát egy később ismert rejection/MSS-jellel.

Célváltozatok külön: legközelebbi előre kijelölt ellenoldali session-high/low; PDH/PDL; fix R kontroll. A célhoz elérhető nettó R-t a tényleges belépő és stop alapján számoljuk. Nincs automatikus 3R–5R ígéret. Lejárt order törlendő; ha a cél már belépés előtt teljesült vagy a sweep-extreme érvénytelenedett, nincs késői belépő.

A stop kezdetben rögzített. Tágabb stophoz kisebb méret tartozik ugyanakkora pénzbeli kockázat mellett. BE/részleges zárás külön trade-management változat; ne változtassuk együtt a belépési szűrővel.

### Mikor hagyjuk ki?

- Nincs pozitív átfedés, vagy a második FVG még nincs lezárva.
- A zóna létrejötte előtt már feltételezett „belépő”: visszatekintési hiba.
- A létrejött BPR-t a választott szabály szerint már felhasználták/érvénytelenítették.
- Nincs előre kijelölt cél, vagy a költségek után kevés a fennmaradó távolság.
- A sweep után folytatódik a kitörés, ellenirányú displacement nélkül.
- Hírhez kötött vagy szélsőséges spreadű időszak a saját előre rögzített kizárási ablakban.
- Egyszerűen nincs teljes setup. A kevés kötés elfogadható, nincs napi vagy éves kötéskvóta.

## További ICT-változatok

| Setup | Saját tesztelhető változat | Stop és cél |
| --- | --- | --- |
| 2022-jellegű sweep + MSS + FVG | HTF/session sweep, ellenirányú displacement és belső swing zárásos törése; az első kialakult FVG első visszatérése. Edge/50% külön belépő. | Sweep-extreme + puffer; előre kijelölt ellenoldali szint vagy fix R |
| Silver Bullet | Előre kiválasztott NY-időablakban létrejött FVG és meghatározott irány/cél. Sweep+MSS követelmény külön szigorított változat, nem minden Silver Bulletre kötelező eredeti szabály. | Az alapmodell strukturális stopja; a setupablak és az exitidő nem ugyanaz |
| OTE | Kijelölt displacement swing 62–79% korrekciója, opcionális 70,5% belépő. Meglévő struktúra és cél kell. | Swing-kezdőpont túloldala; előző szélsőérték vagy kijelölt cél |
| OB + FVG | Az alapmodellhez objektíven kiválasztott OB és FVG átfedés hozzáadása; első mitigation külön | OB- vagy sweep-stop külön; az alapmodell célja |
| IFVG / breaker | Későbbi kutatás: zárásosan érvénytelenített FVG/OB ellenirányú újratesztje | Még specifikálandó; nem keverjük BPR-rel |
| PO3 / SMT | Kontextus/szűrő azonos alapmodellhez | Nem önálló mechanikus belépő ebben a specifikációban |

### Silver Bullet időzóna

A forrás New York helyi idővel dolgozik: **03:00–04:00, 10:00–11:00, 14:00–15:00**. Ez nem egész évben fix UTC vagy „EST”.

A robotban America/New_York szerinti naptár és külön broker-server konverzió kell. Europe/Belgrade helyi időt dátum alapján számoljuk; az amerikai és európai óraátállítás eltérő heteiben változik a különbség. A 09:30-as amerikai részvénypiaci nyitás és a 10:00-as Silver Bullet ablak eltérő esemény. A session-szűrő hozzáadása önmagában nem teszi eredetileg ICT Silver Bulletté a saját stratégiánkat.

## Kapcsolódás a saját konfluenciához

A **POC-klaszter + Den/M30 divergencia + heti sweep + Fibonacci** külön saját kombináció. ICT-BPR/FVG opcionális végrehajtási zónaként adható hozzá. A POC nem BPR, a Den-divergencia nem SMT; ugyanazon mozgásból számolt több jel nem feltétlen független megerősítés.

Két külön irány marad:
- Impulzus végzónájában anticipatív sweep/order belépő, előre tágabb stoppal.
- Sweep után displacement és BPR/FVG visszatérésre váró megerősített belépő.

BPR csak a második rés kialakulása után létezik, ezért nem nevezhető a még ki nem alakult impulzus tetőjének előzetes felismerésének.

Kapcsolódó jegyzetek: [NY-open sweep](ny-open-liquidity-sweep.md), [PDH/PDL sweep](previous-daily-high-low-sweep.md), [HTF sweep](htf-liquidity-sweep.md), [Elliott végzóna](elliott-wave-fibo-rsi.md), [Den](den-lastorangepuma-indicator-suite.md).

## Mérés és implementáció

Még nem kérünk új tesztfájlokat; a szabályokat előkészítjük a későbbi eredményekhez.

- Kontroll: ugyanazon instrumentum/időszak/session/költség mellett sweep+MSS alap → +FVG → FVG helyett BPR. Mindkét gap, pivot és jel ismertté válási időpontját naplózzuk.
- BPR-edge vs BPR-50 vs rejection külön; először azonos strukturális stoppal és exitmóddal.
- Szűrők külön: időablak, HTF-zóna, POC, Den, OTE, SMT. Ne mindet egyetlen optimalizálásban adjuk hozzá.
- Napló: referenciaszint, sweep ideje, MSS ismert ideje, FVG-k három gyertyája, BPR képződése/ára, első retest, order/fill, SL/TP, spread/slippage, MAE/MFE, nettó R, kihagyás oka.
- Ha egy gyertyában entry/SL/TP is érintett, tickadat kell a sorrendhez. Limitérintés nem mindig fill; bid/ask oldal és költségek szükségesek.
- Több modellen ugyanaz a trade ne számítson többször. Kevés kötésnél több év, érintetlen OOS és több rezsim szükséges; nincs bizonyított minimum találati arány.

## Backtest log

| Date | Variant | Instrument / timeframe | Period | Trades | PF | Max DD | Avg R | OOS / forward | Notes |
| --- | --- | --- | --- | ---: | ---: | ---: | ---: | --- | --- |
| 2026-10-03 | ICT-FVG / ICT-BPR / Silver Bullet / OTE | Kiválasztandó | — | — | — | — | — | — | Kutatási specifikáció; nincs hozzáadott mérési eredmény. |

## Korábbi vázlat megőrizve

Purpose: controlled research bucket for filters added to the sweep edge. Test sweep, MSS/CHOCH, displacement, FVG, valid Order Block, OTE, Killzone, SMT / PO3 context independently. Add one filter at a time; compare against the same base model and retain only demonstrated out-of-sample improvements.
