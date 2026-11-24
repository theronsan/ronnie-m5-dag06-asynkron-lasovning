# Förutsägelser: asynkron kod

Regler:

1. Titta på snutten i `snuttar/sNN.js` (eller på sidan `index.html`). **Kör den inte än.**
2. Skriv din gissning i tabellen: utskrifterna i den ordning du tror att de kommer, separerade med `|`.
3. Kör snutten (knappen _Kör_). Skriv vad som faktiskt skrevs ut.
4. Hade du rätt? Skriv en regel med egna ord för varje snutt du gissade fel på.

| Snutt | Min gissning (i ordning)                      | Faktisk utskrift                              | Rätt? | Min regel om jag hade fel                                         |
| ----- | --------------------------------------------- | --------------------------------------------- | ----- | ----------------------------------------------------------------- |
| 1     | 1 2 3                                         |                                               | Ja    |                                                                   |
| 2     | A B C                                         | A C B                                         | Nej   | Allt som har en timeout oavsett om den är 0 eller 1000 körs sist? |
| 3     | Start Noll Kort Lång                          | Start Noll Kort Lång                          | Ja    |                                                                   |
| 4     | efter inuti promise then: klart               | inuti promise efter then: klart               | Nej   |                                                                   |
| 5     | sync promise timout                           | sync promise timeout                          | Ja    |                                                                   |
| 6     | först? 6 7                                    | först? 6 7                                    | Ja    |                                                                   |
| 7     | fel städar lyckades                           | fel slut på mjölk städar                      | Nej   |                                                                   |
| 8     | beställer sätter mig bullen klar kaffet klart | beställer sätter mig bullen klar kaffet klart | Ja    |                                                                   |
| 9     | väntar på båda bulle kaffe resultat           | väntar på båda ["kaffe","bulle"]              | Nej   |                                                                   |
| 10    | 1 6 0 2 3 4 5                                 | 1 6 3 2 4 5                                   | Nej   |                                                                   |
| 11    | a c b                                         | c ab                                          | Nej   |                                                                   |

## Tre meningar med egna ord

1. JavaScript väntar inte på `setTimeout`, utan ... JavaScript kör annan kod under tiden
2. En promise har tre tillstånd: ... Pending, Fulfilled, Rejected
3. `then` körs alltid ... efter att en promise har blivit fulfilled
