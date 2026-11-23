# Timer Intervalli

Timer a intervalli per allenamento (HIIT, Tabata, boxe, circuiti), ispirato all'app iOS Timer Plus.
Web app installabile (PWA), pubblicata con GitHub Pages. Tutti i dati restano sul telefono.

## Come si usa

- **Pagina principale:** tocca una scheda per modificarla, il pulsante verde ▶ per avviare l'allenamento.
  Scorri una scheda verso sinistra per Duplica ed Elimina; tienila premuta e trascinala per cambiare l'ordine.
- **Workout:** preparazione, blocchi e defaticamento. Ogni blocco ha i suoi intervalli di lavoro e riposo,
  le ripetizioni e un recupero finale. Con **Giri totali** si ripete tutto il workout o un tratto di blocchi,
  con un recupero tra i giri.
- **Intervalli di lavoro:** a tempo oppure a ripetizioni; per le ripetizioni si sceglie quanti secondi vale
  ognuna (2 s di partenza, regolabile nelle Impostazioni per i nuovi esercizi).
- **Esercizi:** dalla libreria (icona a forma di libro) o scritti a mano.

## File

| File | Contenuto |
|---|---|
| `index.html` | L'app completa (HTML, CSS e JavaScript) |
| `manifest.json` | Dati per l'installazione sul telefono |
| `sw.js` | Service worker: funzionamento offline e aggiornamenti |
| `icon-180.png`, `icon-192.png`, `icon-512.png` | Icone (180 px per iPhone) |
| `icona.svg` | Disegno originale dell'icona, da cui si ricavano i PNG |
| `esercizi.json` | Libreria di esercizi (799 esercizi) |

## Libreria di esercizi

`esercizi.json` contiene la libreria: 799 esercizi con nome e istruzioni in italiano (corpo libero, stretching,
mobilità e yoga, manubri, kettlebell, elastici, palla medica, corda). L'app lo rilegge a ogni avvio: per
aggiornare la libreria basta sostituire questo file, senza toccare `index.html`. Gli esercizi creati sul
telefono non vengono toccati.

Formato di un esercizio:

```json
{
  "id": "ti-plank",
  "nome": "Plank",
  "nomeEn": "plank",
  "gruppo": "Addome",
  "attrezzo": "Corpo libero",
  "muscoli": "addominali",
  "stretching": false,
  "perLato": false,
  "durata": 30,
  "istruzioni": ["Avambracci a terra…", "Allinea testa, schiena e talloni…", "Mantieni…"]
}
```

Solo `id` e `nome` sono obbligatori. `durata` è in secondi (0 = nessuna durata suggerita); con
`perLato: true` l'esercizio, scelto in un intervallo, diventa due intervalli (destra e sinistra).

Fonte: gli esercizi con id `ed-*` derivano da
[exercises-dataset](https://github.com/hasaneyldrm/exercises-dataset) di Hasan Emir Yıldırım (licenza MIT,
il testo della licenza è nel campo `licenza` del file); nomi e istruzioni sono stati riscritti in italiano.
Immagini e video del dataset non sono inclusi. Gli esercizi con id `ti-*` sono scritti apposta per questa app.

## Aggiornare l'app

A ogni rilascio cambiano il numero di versione in `index.html` (`VERSIONE`) e il nome della cache in `sw.js`.
Sul telefono, se l'app installata non si aggiorna, chiuderla del tutto e riaprirla (a volte serve due volte).
