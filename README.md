# Timer Intervalli

Timer a intervalli per allenamento (HIIT, Tabata, boxe, circuiti), ispirato all'app iOS Timer Plus.
Web app installabile (PWA), pubblicata con GitHub Pages. Tutti i dati restano sul telefono.

## File

| File | Contenuto |
|---|---|
| `index.html` | L'app completa (HTML, CSS e JavaScript) |
| `manifest.json` | Dati per l'installazione sul telefono |
| `sw.js` | Service worker: funzionamento offline e aggiornamenti |
| `icon-192.png`, `icon-512.png` | Icone |
| `esercizi.json` | Libreria di esercizi (per ora vuota) |

## Libreria di esercizi

L'app legge `esercizi.json` a ogni avvio: gli esercizi compaiono come suggerimenti quando si scrive il nome
di un esercizio in un intervallo. Per aggiornare la libreria basta sostituire questo file; gli esercizi
creati sul telefono non vengono toccati.

Formato:

```json
{
  "versione": 1,
  "esercizi": [
    {
      "id": "squat",
      "nome": "Squat",
      "gruppo": "Gambe",
      "attrezzo": "Corpo libero",
      "nota": "Talloni a terra, schiena dritta",
      "durata": 40,
      "perLato": false
    }
  ]
}
```

Solo `id` e `nome` sono obbligatori. `durata` è in secondi.

## Aggiornare l'app

A ogni rilascio cambiano il numero di versione in `index.html` (`VERSIONE`) e il nome della cache in `sw.js`.
Sul telefono, se l'app installata non si aggiorna, chiuderla del tutto e riaprirla (a volte serve due volte).
