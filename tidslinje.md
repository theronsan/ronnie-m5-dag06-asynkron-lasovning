# Tidslinje: rita vad som händer

Välj snutt 5 och snutt 10. Fyll i tabellerna steg för steg. Skriv vad som ligger i varje del **efter** varje steg.

Förklaring:

- **Anropsstacken** är den kod som körs just nu.
- **Microtask-kön** är promise-callbacks som väntar på att få köra.
- **Task-kön** är timer-callbacks och liknande som väntar på att få köra.
- Regel: när stacken är tom körs först ALLA microtasks, sedan EN task, sedan tomma microtasks igen, och så vidare.

## Snutt 5

| Steg | Vad händer                          | Stacken                | Microtask-kön          | Task-kön               | Utskrift hittills |
| ---- | ----------------------------------- | ---------------------- | ---------------------- | ---------------------- | ----------------- |
| 1    | setTimeout anropas                  | setTimeout             | tom                    | console.log("timeout") |                   |
| 2    | Promise.resolve().then(...) anropas | Promise.then           | console.log("promise") | console.log("timeout") |                   |
| 3    | console.log("sync")                 | console.log("sync")    | console.log("promise") | console.log("timeout") | sync              |
| 4    | Stacken tom: vad körs först?        | console.log("promise") |

| tom | console.log("timeout") | sync promise |
| 5 | Nästa | console.log("timeout") | tom | tom | sync promise timeout |

// Egen notering: synkron kod körs först, sedan körs Microtasks, därefter körs Tasks

## Snutt 10

| Steg | Vad händer                       | Stacken | Microtask-kön | Task-kön | Utskrift hittills |
| ---- | -------------------------------- | ------- | ------------- | -------- | ----------------- |
| 1    | console.log("1")                 |         |               |          |                   |
| 2    | första setTimeout                |         |               |          |                   |
| 3    | Promise.resolve().then(3)        |         |               |          |                   |
| 4    | andra setTimeout                 |         |               |          |                   |
| 5    | console.log("6")                 |         |               |          |                   |
| 6    | stacken tom, microtask-kön först |         |               |          |                   |
| 7    | första tasken                    |         |               |          |                   |
| 8    | andra tasken                     |         |               |          |                   |
| 9    | microtask 5                      |         |               |          |                   |

## Min förklaring i en mening

Varför kommer en promise-callback före en timer med 0 ms?

En Promise-callback körs före en timer med 0 ms eftersom Promise-callbacks ligger i microtask-kön, som töms innan nästa task körs.
