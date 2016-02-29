# BEKK Kode Kalender

Hensikten er å lage en quiz-applikasjon for kodeoppgaver - alá eksisterende
kodekalendere - men trenger ikke nødvendigvis å være forbeholdt spesifikke
sesonger, men kan bli brukt som generelle quiz-skjema.


## Datagrunnlag

Alle spørsmål vil bli sendt inn som JSON-format, som i enkleste fall kan være
en flatfil i et repo, eller på sikt være et API-endepunkt eller data fra en server.

Skjema er tiltenkt noe lignende som dette:

```js
const data = [
  {
    "name": "Example name",
    "tags": ["algorithm", "math", "haskell"], // kategorier/tags for typen oppgave

    // Kan være type "text", "list", "multiline" eller lignende. For å gi mer
    // tilpasset svartyper
    "type": "text",

    // Spørsmålstekst i markdown (med kodeeksempler etc)
    "question": "# Markdown document",

    // En liste med hint og en tilknytted kostnad, for de tilfellene det kan
    // være aktuelt å ha med hint.
    "hints": [ // (valgfri)
      {
        "hint": "Some hint text (markdown)",
        "cost": 10,
      },
      {
        "hint": "Some hint text (markdown)",
        "cost": 50,
      },
      {
        "hint": "Some hint text (markdown)",
        "cost": 100,
      }
    ],

    // Vanligvis vil det gå ned X poenger i sekundet, trekt fra den totale scoren
    // som er mulig å få per spørsmål. En deadline vil være etter gitt antall
    // sekunder så vil ikke lenger scroen bli redusert (er på minimumsverdi).
    "totalPoints": 10000
    "deadline": 3600,
    "pointsReducedPerSec": 1,
    "deadlinePoints": 100, // hvor mye som er minimum-poeng etter deadline er over.

    // Bonus (valgfri)
    // Basert på plassering, skal man få poengbonus?
    "bonus": [
      {
        "place": 1,
        "bonus": 100
      },
      {
        "place": 2,
        "bonus": 80
      },
      {
        "place": [3, 10], // intervall av plassering
        "bonus": 30
      },
      {
        "place": [11, 20], // intervall av plassering
        "bonus": 10
      }
    ],
    "penalty": 10 // Poeng i minus dersom feil svar.
  }
];
```
