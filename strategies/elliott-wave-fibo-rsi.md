# Elliott Wave + Fibonacci + RSI

**Stage:** idea / specification. Existing EA logic needs its own measured test record before a performance claim.

## Structure catalogue

- Impulse 1–2–3–4–5; leading and ending diagonal.
- ABC corrections: zigzag, flat, expanded flat, running flat, triangle, double three and triple three.

## First testable variants

1. ZigZag wave structure + Fibonacci retracement entry; fixed stop and extension target.
2. Same rules with RSI confirmation on M1/M5.
3. Same rules after an HTF or previous daily high/low sweep and MSS.

Freeze ZigZag parameters, confirmed pivot timing, invalidation rules, fib levels, costs and time zone before testing. Avoid using pivots that become visible only after future candles: evaluate signals at the time an EA could actually place an order. Keep every parameter change as a separate variant.

## External research to replicate

- [Algorithm for Elliott Waves pattern detection](https://journals.sagepub.com/doi/10.3233/IDT-170319): compare confirmed pivot recognition against retrospective chart labels.
- [Algorithmic Fibonacci retracement zones](https://doi.org/10.1016/j.eswa.2021.115893): compare selected Fibo bands against predefined control bands. Neither paper verifies this EA's returns.

## Backtest log

| Date | Variant | Instrument / timeframe | Period | Trades | PF | Max DD | Avg R | OOS / forward | Notes |
|---|---|---|---|---:|---:|---:|---:|---|---|
| 2026-09-27 | Specification | — | — | — | — | — | — | — | No measured results supplied. |


## Elliott + Fibonacci kutatás — 2026-10-03

### Alapelvek és források

Az Elliott-számozás több lehetséges értelmezést engedhet; a választott számozás hipotézis, nem biztos jövőbeli mozgás. [EWI Waveopedia](https://www.elliottwave.com/waveopedia/).

Normál impulzusnál a 2. hullám nem haladhat túl az 1. kezdetén, a 3. nem lehet a legrövidebb az 1/3/5 közül, és a 4. nem fedheti át az 1. árterületét. A diagonál külön mintacsalád, külön szabályokkal. A 3. hullám hossza teljesen csak az 5. után ellenőrizhető; ezt nem szabad visszamenőleg belépési szűrővé alakítani. [Impulzus](https://www.elliottwave.com/waveopedia/impulse/), [diagonál](https://www.elliottwave.com/waveopedia/elliott-wave-pattern-diagonals/).

A Fibonacci arányok lehetséges zónákat adnak, nem garantált fordulópontokat. A 38,2%, 50%, 61,8% visszahúzódás és az impulzusok közötti arányok EWI irányelvek; az 50% nem Fibonacci-számarány. Az alábbi szűkebb belépési sávok és triggerkombinációk saját teszthipotézisek. [Fibonacci Relationships](https://www.elliottwave.com/waveopedia/fibonacci-relationships/).

### Négy külön setup

Minden példa bullish; short esetben tükrözendő. Az elnevezések feltételezett hullámhelyzetek.

| Variáns | Kontextus és Fibo | Belépési hipotézis | Stop / érvénytelenítés | Célhipotézis |
| --- | --- | --- | --- | --- |
| EW-2to3 | Feltételezett 1. hullám után korrekció. Külön teszt: 50–61,8%, illetve 61,8–78,6% visszahúzódás az 1. hullámon | M5/M15 zárás a korrekció legutóbbi megerősített belső csúcsa fölött; külön változatban visszateszt | Belépési stop a korrekció mélypontja alatt; hullámszámozás érvénytelen az 1. kezdetének áttörésekor | 1. hullám csúcsa, majd a 2. végétől az 1. hosszának 1× vagy 1,618× vetítése |
| EW-4to5 | Azonos fokozatú 1–2–3 jelölt után sekély korrekció; tesztsáv 23,6–38,2% a 3. hullámon | Korrekciós csatorna vagy belső csúcs zárásos törése | Stop a 4. mélypontja alatt; normál impulzusnál 1. árterületével átfedés érvénytelenít | Előző 3. csúcs, majd a 4. végétől az 1. hosszának 0,618×/1× vetítése |
| EW-ABC-end | HTF emelkedésen belüli lefelé ABC; zigzag esetben 5–3–5 belső szerkezet. C-hossz hipotézis A×1 vagy A×1,618, B végétől | C-n belüli bearish momentum gyengülése, majd bullish belső struktúratörés; külön sweep-változat | Stop C mélypontja alatt; új mélypont a fordulójel után érvényteleníti a trade-et | B csúcs vagy a korábbi impulzus csúcsa; külön fix 2R kontroll |
| EW-5-reversal | Feltételezett ötödik hullám végén új ár-csúcs, a 3.-hoz képest gyengébb RSI-csúcs | Bearish struktúratörés és visszateszt; divergencia önmagában nem belépő | Stop az 5. csúcsa fölött | Korábbi 4. zónája vagy fix R cél külön tesztben |

Az EW-4to5 egyenlőségi céljához: [EWI Equality](https://www.elliottwave.com/waveopedia/equality/). Az ABC nem mindig zigzag: flat és triangle esetén más belső struktúra kell; nem lehet minden korrekcióra 5–3–5-öt erőltetni. [Corrective Waves](https://www.elliottwave.com/waveopedia/corrective-waves/).

### Konfluencia — külön-külön mérendő kiegészítések

- **HTF trend:** H1/H4 kontextus, M15 setup, M5 trigger kipróbálható. A trendet objektíven rögzítsük: például megerősített magasabb csúcs/mélypont vagy egyetlen előre kiválasztott MA-szűrő. Ezek nem eredeti Elliott-követelmények.
- **RSI(14):** EW-2to3/ABC esetén az utolsó két korrekciós mélypont bullish divergenciája; EW-5-reversal esetén a 3./5. csúcsok közötti bearish divergencia. A 3. hullámban túlvett RSI önmagában nem shortjel. A momentum gyengülése és volumen jellemzői az EWI-nél irányelvek, az RSI-trigger itt külön hipotézis. [Wave Personality](https://www.elliottwave.com/waveopedia/wave-personality/).
- **Sweep + MSS:** a Fibo-zónán belül előző megerősített mélypont kisöprése, majd zárás a rögzített belső csúcs fölött. A sweep nem következik automatikusan Elliottból; saját kombináció.
- **POC / VAH / VAL / VWAP:** előre rögzített, lezárt profil szintje vagy session VWAP lehet helyszínszűrő. Távolsági toleranciát rögzítsünk tickben/ATR-ben. Nem bizonyított, hogy javítja az Elliott-setupot.
- **Volumen:** csökkenő korrekciós, majd növekvő kitörési volumen kipróbálható. FX/CFD tickvolume és kriptotőzsdei volumen külön adatsor; nem szabad összemosni.
- **Elliott-csatorna:** 1–3 pontokon húzott vonal és 2-n át párhuzamos a 4. becsléséhez; 2–4 alapvonal és 3-on át párhuzamos az 5. célzónájához. Erősen megnyúlt 3. esetén 1-en át párhuzamos is figyelhető. [Channeling](https://www.elliottwave.com/articles/how-to-use-elliott-wave-channels-in-your-analysis/).

### Számolási példa: EW-2to3 long

Feltételezett 1. hullám 100 → 120, hossza 20. 50–61,8% visszahúzódási zóna 110 → 107,64. A 2. jelölt mélypontja 108; megerősítés utáni belépés például 111, stop 107,5. Kockázat 3,5 ár-egység; első cél 120, azaz kb. 2,57R. A 2. végétől vetített 1,618×20 cél 140,36. Ez számolási példa, nem valós piaci eredmény. A stopot és a pozícióméretet spread/slippage figyelembevételével kell megadni.

### MT5 / MultiZigZag megvalósítás

A ZigZag indikátor nem önmagában Elliott-számozó. Az utolsó pivot és szakasz változhat, a pivot megerősítése késhet. [TradingView ZigZag dokumentáció](https://www.tradingview.com/support/solutions/43000591664-zigzag-indicator/).

A MultiZigZag_Elliott változatnál minden jelhez naplózzuk a pivot gyertyáját ÉS az ismertté válás időpontját. Csak az akkor ismert, megerősített pontokból számoljunk; a paramétereket és a wave degree-t teszt előtt rögzítsük. A korábbi saját 54–73% belépési sáv és 99–127% TP külön EA-variáns: a TP Fibo-horgonypontjait előbb ellenőrizni kell, nem megfeleltetni automatikusan az itt használt vetítéseknek.

Tesztelési sorrend: EW-2to3 alap → ugyanaz + RSI → ugyanaz + sweep/MSS → ugyanaz + POC. Utána külön EW-4to5, ABC és 5-reversal. Minden szűrőt az azonos alaphoz mérjünk; azonos költségek, érintetlen OOS szakasz, kötésdarabszám/PF/DD/Avg R és paraméterstabilitás. A sorrend implementációs javaslat, nem teljesítményrangsor.

| Date | Variant | Instrument / timeframe | Period | Trades | PF | Max DD | Avg R | OOS / forward | Notes |
|---|---|---|---|---:|---:|---:|---:|---|---|
| 2026-10-03 | EW-2to3 / 4to5 / ABC / 5-reversal | To be selected | — | — | — | — | — | — | Source-backed framework + explicitly labelled test hypotheses; no measured returns. |


## EW-5-confluence-reversal — a tulajdonos megfigyelése

A tulajdonos 2026-10-03-i megfigyelése: feltételezett öt hullámos impulzus végén M30 Den-divergencia, több POC-ból álló klaszter és előző heti csúcs találkozik; a heti csúcs kisöprése után fordulatot több alkalommal követett. Ez kvalitatív megfigyelés, nem számszerű backtest vagy igazolt találati arány.

### Megfigyelt short kontextus

1. Egy adott felfelé impulzus vagy korrekció feltételezett kifáradása. Az öt hullám egy lehetséges kontextus, nem kötelező teljes hierarchikus számozás. A fordulópontot árreakcióval kell megerősíteni.
2. M30-on Den divergenciajel. A használt `8LIW/Div` pontos típusa, RSI-beállítása és jelmegerősítése még rögzítendő; az M30 szándékos eltérés a Den dokumentum M15-ös alapváltozatától.
3. Előre ismert POC-klaszter az ár fölött: több lezárt profil POC-szintje szűk ársávban.
4. A zónában az előző lezárt hét maximuma (PWH).
5. Az ár PWH fölé szúr, majd fordul. Az esemény pontos meghatározása még hiányzik.

### Javasolt, külön tesztelendő trade-trigger

- A sweep után egy lezárt M5 vagy M15 gyertya visszazár PWH alá. A két idősík külön variáns.
- Ezután bearish MSS: zárás a korábban rögzített, megerősített belső swing low alatt.
- Belépés az MSS utáni első visszatesztre, előre definiált szinten (például a megtört swing low); alternatív, külön variáns a közvetlen MSS-zárás utáni market belépés.
- Stop a sweep maximuma fölött, előre rögzített tick-/ATR-pufferrel. Új maximum vagy jel-lejárat a belépés előtt érvényteleníti a setupot.
- Külön célvariánsok: korábbi 4. hullám zónája; következő alsó POC; fix 2R/3R. A célok között ne utólag válasszunk.

A trigger/stop/cél itt implementációs javaslat, nem a tulajdonos megfigyelésének vagy Den módszerének már igazolt részlete. Long tükörváltozat: lefelé öt hullám + bullish M30-divergencia + alsó POC-klaszter + előző heti minimum (PWL) sweep + visszazárás és bullish MSS. Ezt külön hipotézisként kell tesztelni.

### Konfluencia számszerűsítése és kontroll

- Klaszter: legalább hány POC (pl. 2 vagy 3), melyik napi/heti profilokból, mennyi köztük a maximális távolság? Rögzített tick- vagy ATR-tolerancia kell; ugyanazt a POC-t ne számoljuk többször.
- PWH/PWL és a klaszter közötti megengedett távolság, hét időzónája, divergencia és sweep közötti maximális gyertyaszám.
- A klaszter minden szintje a jel idején legyen ismert; kész heti profilból nem használható a később kialakuló POC visszamenőleg.
- Az ár és RSI divergenciapontjai legyenek egymáshoz rendelve. Az RSI gyengülése önmagában nem bizonyítja az ötödik hullám lezárását.
- Kontrollok: PWH/PWL sweep+MSS önmagában; +M30 divergencia; +POC-klaszter; végül +Elliott-feltétel. Így külön mérhető, ad-e többletet maga a hullámszűrés.

| Date | Variant | Instrument / timeframe | Period | Trades | PF | Max DD | Avg R | OOS / forward | Notes |
|---|---|---|---|---:|---:|---:|---:|---|---|
| 2026-10-03 | EW-5-confluence-reversal | M30 div / M5–M15 trigger (proposed) | — | — | — | — | — | — | Owner observation; exact rules and measured outcomes pending. |


## Elsődleges irány — a kilövő impulzus végének elcsípése

A tulajdonos pontosítása: **a futó, kilövő impulzus várható végzónáját keresi, még a kész fordulat előtt**. Mindkét irány elfogadott: impulzus utáni korrekció végén trendfolytató belépés, illetve a kilövő impulzus végének konfluenciás elcsípése. A teljes hullámhierarchia felismerése nem kötelező.

A kérdés: hol sűrűsödnek azok az előre ismert szintek, ahol az impulzus megállhat? A szint nem garantált ármegállító. A várható zónát és annak érvénytelenítését határozzuk meg, nem biztos tetőt/aljat.

### Végzóna becslése (short példa)

- Egyértelmű, rögzített swing horgonypontokból Fibo-vetítések. Ha az 1./4. pontok azonosíthatók, az 1. hosszának a 4. végétől vett vetítése; más esetben általános swing-vetítés, Elliott-címke nélkül. A használt 1×/1,618× stb. arányt és horgonypontot előre rögzítsük, ne utólag válasszuk a találó szintet.
- Előre ismert POC-klaszter és PWH/korábbi swing-high egy szűk zónában. A POC volume-koncentrációt mutat, önmagában nem bizonyít ott várakozó eladói likviditást.
- Az ár tovább emelkedik vagy új csúcsot üt, miközben M30-on Den bearish divergencia alakul ki: a momentum gyengülése illeszkedik a végzóna-hipotézishez.
- PWH fölötti sweep a zónában. A szúrás lehet kifáradás, de folytatódó kitörés is; ezért külön feladat a belépési szabály és a stop meghatározása.

### Belépő és stop — még kiválasztandó variánsok

A tulajdonos nem adott még végleges order-triggert. Nem tesszük kötelezővé az MSS-t vagy a visszatesztet. Összehasonlítható ötletek:

| Variáns | Belépő | Stop alapja | Fontos korlát |
| --- | --- | --- | --- |
| Anticipatív szintbelépő | Előre rögzített végzónában limit, csak az addig ismert divergencia mellett | Előre kijelölt zónahatár + puffer | A későbbi sweep-csúcs itt még ismeretlen; nem használható visszamenőleg stophoz |
| Első elutasítás | Sweep után első rögzített LTF visszazárás a szint alá | Addig ismert sweep-maximum + puffer | A később megerősített M30-divergenciát nem lehet korábbi belépéshez felhasználni |
| Fordulógyertya törése | Lezárt elutasító gyertya minimuma alatti sell stop | Gyertya/sweep maximum + puffer | Későbbi belépő; külön mérendő a célhoz fennmaradó távolság |

Longnál lefelé impulzus vége, bullish divergencia, alsó klaszter és PWL-sweep. Ezek kutatási variánsok, nem elfogadott végleges szabályok. A pénzbeli kockázatból és a stopból számoljuk a méretet. Az újabb csúcsok miatti folyamatos stop-tágítás helyett előre rögzített invalidáció és új setup kell.

Első összehasonlítás: szintklaszter önmagában → +divergencia → +sweep → opcionális Fibo/Elliott-szűrő, azonos belépési módszerrel. A megfigyelt kifáradási zóna találati minőségét és a trade eredményét külön mérjük; egy jól becsült fordulózóna is adhat rossz kötést rossz időzítéssel.


### A tulajdonos végső pontosítása — két elfogadott kereskedési irány

1. **Impulzus → korrekció → belépés az új impulzusra.** A Fibonacci-visszahúzódás, konfluencia és fordulójel a korrekció végének helyét/időzítését adja; a stop a korrekciós swing érvénytelenítési pontján túl van.
2. **Impulzusvégi sweep/order belépő, tágabb kezdeti stoppal.** M30 divergencia, előre ismert POC-klaszter és PWH/PWL segít a végzóna kiválasztásában. A sweephez kötött order pontos típusa (limit/stop/market) még nincs kiválasztva; nem kötelező utólagos MSS-visszateszt. A tágabb stop a nagyobb túlszúrás terét adja, előre meghatározott távolsággal/invalidation szinttel. Ugyanakkora pénzbeli kockázatnál kisebb pozícióméretet jelent, nem menet közbeni korlátlan stop-tágítást.

A stop-puffer tick- és ATR-alapú változata külön tesztelhető. A nagyobb stop előnyét a stopkivételek, a romló R és a nettó eredmény együtt mutatja meg; nem feltételezzük, hogy önmagában javítja a stratégiát.
