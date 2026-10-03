# Piaci rezsimváltás — okok, felismerés és stratégiaválasztás

**Állapot:** kutatási keretrendszer / idea. **Frissítve:** 2026-10-03. Nem önálló belépési stratégia, hanem a sweepes, trendfolytató és fordulópontot kereső rendszerekhez vizsgálandó szűrő. Nincs hozzáadott backtesteredmény.

## Mit nevezünk rezsimváltásnak?

A piac viselkedésének tartósabb megváltozását a kiválasztott időtávon: például visszatérésre hajlamos oldalazásból irányos trendbe, vagy nyugodt környezetből nagy volatilitású, rosszabbul végrehajtható piacba váltást.

Három külön tengelyt követünk:
1. **Irányosság:** trendelő vagy visszatérésre hajlamos.
2. **Volatilitás:** alacsony, normál vagy magas a saját múltjához képest.
3. **Végrehajthatóság:** spread, slippage és — ahol hozzáférhető — könyvmélység.

Az emelkedésből esésbe fordulás nem feltétlen rezsimváltás. Magas volatilitás nem feltétlen trend. H1-en lehet oldalazás, miközben M5-ön erős trend fut. A rezsimet instrumentumhoz, időtávhoz és sessionhöz kötjük.

## Mi idézheti elő?

| Mechanizmus | Lehetséges hatás | Mit különböztessünk meg? |
| --- | --- | --- |
| Váratlan makroadat, jegybanki döntés vagy kommunikáció | Átárazódik a várt kamatpálya, növekedés vagy kockázati prémium | A várakozáshoz képesti meglepetés számít; egy hírmozgás önmagában nem tartós váltás |
| Likviditási kínálat visszahúzódása | Ugyanaz a megbízás nagyobb árhatással, szélesebb spreaddel járhat | Finanszírozási likviditás és kereskedési könyvmélység nem ugyanaz |
| Tőkeáttétel leépítése, margin call | Kényszerű pozíciózárás felerősítheti az első sokkot | Nem minden esés likvidálási spirál; OHLC nem mutatja közvetlenül az okot |
| Várakozásváltozás utáni tartós portfólió-átrendezés | Az első mozgást további pozícióépítés követheti | Folyamatosságot megfigyelhetünk, intézményi szándékot nem bizonyítunk chartból |
| Piacszerkezet vagy résztvevők változása | Változhat a likviditás, az összekapcsoltság és a sokkok terjedése | Hosszabb szerkezeti változás és napi sessionváltás eltér |
| Intraday részvétel változása | Nyitás, zárás vagy sessionváltás körül más aktivitás | Rendszeres napszaki mintát ne nevezzünk automatikusan új strukturális rezsimnek |

**Forrásalap:** a Fed kutatása a döntések mellett a jövőbeli kamatpályáról szóló kommunikáció árhatását vizsgálja. A BIS margin/likviditás anyagai a stresszt erősítő tőkeáttételi folyamatokat tárgyalják. Az IMF FX-kutatása az elvárások, portfólió-átrendezés és likviditási nyomás kapcsolatát írja le. Ezek mechanizmusok, nem a saját jelzőrendszerünk teljesítménybizonyítékai.

## Átmeneti sokk vagy tartós rezsim?

A 2016. október 7-i font flash event jelentős részben gyorsan visszaforduló, több tényezővel összefüggő likviditási esemény volt. A nagy gyertya ezért önmagában nem elég.

Érdemes külön jelölni:
- **Sokk:** azonnali volatilitási / végrehajtási romlás.
- **Átmenet / bizonytalan:** eltérő irányú jelek; nincs megbízható besorolás.
- **Fennmaradó viselkedés:** több lezárt megfigyelési ablakban is ugyanaz a minta.
- **Normalizálódás:** csökkenő volatilitás és javuló végrehajtás; nem feltétlen a régi trend visszatérése.

A hírnaptár előre jelzi az esemény időpontját, de nem a meglepetés irányát. A rezsim többnyire késéssel felismerhető; biztos előrejelzést nem ígérünk.

## Felismerhető jelek — saját teszthipotézisek

| Megfigyelés | Mérési ötlet | Korlát |
| --- | --- | --- |
| Növekvő irányosság | Efficiency Ratio: abs(Close[t] − Close[t−N]) / sum(abs(Close[i] − Close[i−1])); nulla nevezőnél nem értelmezett | N és idősík előre rögzítendő; zajos, késik |
| Változó mozgásméret | ATR/ár vagy realizált volatilitás gördülő múltbeli percentilise | Az ATR nem irányjel; csak addig ismert múltból számoljunk |
| Kitörés fennmaradása | Referencia-range-en kívüli zárások, visszateszt, további szélsőértékek | Referenciaszint, időablak és lejárat előre választandó |
| Gyors visszatérés a range-be | Sweep utáni reclaim aránya, ideje és következő elmozdulás | Ugyanaz az esemény ne kapjon utólag eltérő címkét |
| Értékterület / POC vándorlása | Egymást követő lezárt profilok árszintváltozása ATR-ben | Profilhorgony és felbontás változása hamis jelet adhat |
| Rosszabb végrehajtás | Spread és tényleges slippage saját sessionhöz viszonyítva | A broker spread nem a teljes piac könyvmélysége |
| Divergencia utáni folytatás | Előre definiált divergenciajel után új szélsőérték gyakorisága | Nem bizonyít önmagában trendrezsimet; indikátorparamétertől függ |

Az ADX opcionális irányossági kiegészítés, nem univerzális kapcsoló. Nem alkalmazunk minden piacra egyetlen „ADX > 25” vagy ATR-határt. A POC, Fibo, MSS, RSI/Den és BPR chartjelzések; nem a rezsimváltás gazdasági okai.

## Mit jelent a saját stratégiáinknak?

| Megfigyelt környezet | Elsődlegesen vizsgálandó ág | Mire figyeljünk? |
| --- | --- | --- |
| Visszatérő range, mérsékelt költségek | NY/PDH-PDL/HTF sweep forduló; POC felé visszatérés | Legyen reclaim vagy a választott korai belépőnek megfelelő invalidáció |
| Irányos mozgás, sekély korrekció, fennmaradó kitörés | Korrekció utáni Elliott/Fibo folytatás; irányba illeszkedő ICT-FVG/BPR | Divergencia önmagában ne indítson ellenirányú trade-et |
| Impulzus végi konfluencia | Den-divergencia + POC + PWH/PWL + Fibo végzóna külön változata | A helyszín nem bizonyítja, hogy a trendrezsim véget ért |
| Volatilitási és költségsokk | Előre rögzített várakozás / ordertiltás / csökkentett kockázat vizsgálata | Fix szűk stop, market fill és historikus spreadfeltételezés torzíthat |
| Vegyes / bizonytalan | Kihagyás vagy külön átmeneti kategória | Nem kell minden gyertyát trend/range címkébe kényszeríteni |

Ez kutatási illeszkedés, nem automatikus kereskedési utasítás. A magas volatilitás nem tilt minden stratégiát; az adott setup költség- és stopérzékenységét kell mérni.

## Egyszerű első megvalósítás

H1 kontextus + M5/M15 belépő csak javasolt kezdő változat.

1. Irányosság: egy előre kiválasztott ER-ablak.
2. Volatilitás: egy előre kiválasztott ATR/ár vagy realizáltvolatilitás-ablak.
3. Költség: spread saját session szerinti múltbeli eloszlása; valós fill esetén slippage is.
4. Külön jelző: előre kijelölt range kitörése utáni fennmaradás vagy reclaim.
5. Besorolás csak lezárt gyertyán; megtartott „bizonytalan” kategóriával.

Nincs végleges küszöb. Az ablakokat és a határokat tanuló mintán választjuk, majd befagyasztjuk. Külön belépési/kilépési határ és előre rögzített fennmaradási idő csökkentheti az állandó kapcsolgatást, de késést okoz. Hírsokk-kizárás külön szűrő; ne keverjük a trend/range osztályozóval.

Később change-point vagy Hidden Markov modell összehasonlítható az egyszerű szabályokkal. A HMM állapotnak nincs önmagában garantált „trend” jelentése. Csak valós időben elérhető filtered állapot használható; a jövőbeli adatokkal simított állapot nem belépési jel.

## Tesztterv — amikor eredmények érkeznek

- Ugyanaz a stratégia szűrő nélkül vs rezsimszűrővel; változatlan entry/SL/TP/költségek.
- Külön mérjük a kihagyott nyerőket, elkerült veszteségeket és a kötésdarabszámot.
- Nettó R, DD, PF, MAE/MFE, slippage, rezsimenkénti és átmeneti teljesítmény.
- Jelzési késés és téves állapotváltások gyakorisága.
- Időrendben elkülönített tanuló/OOS/forward szakasz. A rezsimcímke csak az akkor ismert adatokból képződhet.
- Kevesebb kötés elfogadható, de a magasabb historikus PF kisebb mintán nem elég. Nem cél évi pontosan 20 trade.

A veszteséges széria figyelmeztetés lehet, de önmagában nem bizonyít rezsimváltást: költség, adat, végrehajtás, véletlen és túlillesztés is vizsgálandó.

## Források

1. [Fed: Do Actions Speak Louder Than Words?](https://www.federalreserve.gov/econres/feds/do-actions-speak-louder-than-words-the-response-of-asset-prices-to-monetary-policy-actions-and-statements.htm) — döntés és kommunikáció árhatása.
2. [BIS: Margins and haircuts as a macroprudential tool](https://www.bis.org/speeches/20160608-margins-and-haircuts-macroprudential-tool) — tőkeáttétel, likviditás és stressz.
3. [BIS: Under pressure — market conditions and stress](https://www.bis.org/publications/qr-202209/under-pressure-market-conditions-and-stress) — volatilitás, piaci és finanszírozási likviditás.
4. [BIS: The sterling flash event of 7 October 2016](https://www.bis.org/publications/sterling-flash-event-7-october-2016.pdf) — intraday sokk esettanulmánya.
5. [IMF: Risk and Resilience in the Global Foreign Exchange Market](https://www.elibrary.imf.org/display/book/9798229023184/CH002.xml) — várakozás, pozícióátrendezés és FX-likviditás.

## Backtest log

| Date | Variant | Instrument / timeframe | Period | Trades | PF | Max DD | Avg R | OOS / forward | Notes |
| --- | --- | --- | --- | ---: | ---: | ---: | ---: | --- | --- |
| 2026-10-03 | Rezsimfelismerés / stratégiaválasztás | Kiválasztandó | — | — | — | — | — | — | Forrásalapú összefoglaló és saját teszthipotézisek; mérési eredmény nincs. |
