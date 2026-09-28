# Patrick Nill — 3-touch range breakout

## Forrás és bizonyítottság

- [IQCapital interjú Patrick Nill-lel (2026. augusztus 28.)](https://www.youtube.com/watch?v=2hyqdVF0JVk&t=610s), 51:38.
- A videó leírása fair value tartományokat, három érintéses szabályt, belépést, stopot és célárat nevez meg. A fejezetek: [range / fair value / 3:1 (2:36)](https://www.youtube.com/watch?v=2hyqdVF0JVk&t=156s), [három érintés (19:37)](https://www.youtube.com/watch?v=2hyqdVF0JVk&t=1177s), [stop fegyelem (33:18)](https://www.youtube.com/watch?v=2hyqdVF0JVk&t=1998s).
- A webes átirat jelenleg nem érhető el; az alábbiak **a készítő leírásából és fejezetcímeiből**, nem egy teljes, ellenőrzött szabálykönyvből származnak. A címben szereplő versenyeredményt nem tekintjük függetlenül igazolt teljesítménynek.

## Kutatási hipotézis

Fair value tartomány felismerése után a három érintéses feltétellel érettnek tekintett range kitörését figyelni. A „fair value to fair value” és a 3:1 arány a fejezet címében szerepel; hogy ez pontosan a belépést, a célárat vagy a kockázat/hozam arányt határozza-e meg, még ellenőrizni kell. Ez **nem kész MT5 belépési algoritmus**.

## Pontosítandó szabályok

1. Hogyan húzza meg a fair value tartományt, milyen instrumentumon és idősíkon?
2. A három érintés pontosan melyik oldalt érinti, az első érintés számít-e, és szükséges-e zárás a tartományon belül?
3. Kitörés után azonnali vagy visszatesztelt belépés? Milyen gyertya és milyen invalidáció kell?
4. Hová kerül a kezdeti stop és a célár; mit jelent pontosan a 3:1?
5. Milyen időszakokban kereskedik, és hogyan kezeli a hamis kitörést, spreadet, híreket?
6. A 33:18-nál jelzett stopfegyelem mikor tiltja a stop elmozdítását?

## Backtest log

| Dátum | Instrumentum | Idősík | Időszak | Kötések | Eredmény | Megjegyzés |
| --- | --- | --- | --- | --- | --- | --- |
| 2026-09-28 | — | — | — | — | — | Szabályok és teszteredmények még nincsenek igazolva. |
