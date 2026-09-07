# Gli insulti come dovrebbero essere

Glossario di trentacinque insulti costruiti nominando la virtù che sta di fronte al vizio.
Pagina statica, un file solo, nessuna dipendenza esterna in esecuzione.

Online: <https://daniloaprigliano.github.io/insulti-al-rovescio/>

## Com’è fatta

| File | Cosa contiene |
| --- | --- |
| `index.html` | Tutto: stile, contenuto, lessico e comportamento. Nessun framework. |
| `fonts/` | Bodoni Moda, Source Serif 4 e Archivo in woff2 variabile, sottoinsieme latino e latino esteso. |
| `og.png` | Immagine di anteprima per WhatsApp, Telegram, Signal, Mastodon, Bluesky, LinkedIn. 1200 × 630. |
| `favicon.svg` e i png | Crocino di registro, stampato deliberatamente fuori registro. |

I caratteri stanno nel repo invece che su Google Fonts: la pagina non contatta nessun server
esterno, quindi funziona anche offline e non lascia l’indirizzo IP di chi legge a terzi.

## Aggiungere una voce

Le voci stanno nell’array `VOCI` dentro `index.html`. Ogni riga ha questa forma:

```js
{v:"vizio", r:"rovescio", var:["variante"], l:"registro", f:["forme per la macchina"],
 g:"Glossa, con <em>corsivo</em> per le parole greche e latine."}
```

`l` è la lastra, cioè il registro da cui viene la parola, e vale `clinico`,
`ecclesiastico`, `notarile`, `erudito` oppure `carta` per l’italiano corrente.
`f` sono le forme che la macchina può pescare per comporre le formule: vanno tenute
brevi e maneggiabili, perché possono ricevere un rafforzativo. Per una voce femminile
si aggiunge `fem:true`, così l’articolo e il rafforzativo si accordano.

I contatori della testata, delle lastre e delle carte si aggiornano da soli.

## Condividere una voce

Ogni voce ha il suo indirizzo, costruito sul lemma: `…/#acheropita`,
`…/#cenobita-del-talamo`. Aprendolo, la pagina passa al dizionario, azzera ricerca e
filtri, scorre fino alla voce e la marca in magenta per qualche secondo. Gli indirizzi
si generano da soli dal campo `r`, quindi cambiando un lemma cambia anche il suo
indirizzo: chi avesse in giro il vecchio link cade sulla pagina intera senza errori.

Toccando il lemma nel dizionario, o il richiamo `copia` sulla carta nel mazzo, finisce
negli appunti la scheda intera: lemma, vizio sostituito, glossa, varianti, registro e
l’indirizzo della voce. Gli asterischi e i trattini bassi del testo copiato sono la
marcatura di WhatsApp, che li rende grassetto e corsivo; altrove restano due segni
di troppo.

L’anteprima social resta quella della pagina intera. Per avere una scheda diversa per
ogni voce servirebbero trentacinque pagine generate, una per lemma, ognuna con i suoi
`og:title` e `og:description`, perché il frammento dell’indirizzo al server non arriva.

## Rifare l’immagine di anteprima

`og.png` è uno screenshot di una pagina costruita apposta, alle stesse misure e con gli
stessi caratteri. Per rigenerarla serve un browser headless: si apre la sorgente a
1200 × 630 e si salva la schermata. Cambiando `og.png` conviene ricordare che Facebook,
LinkedIn e X tengono l’immagine in cache per giorni, e che ognuno ha il suo debugger per
forzare il rinfresco.

## Indicizzazione

`index.html` contiene `<meta name="robots" content="noindex">`. Il link resta condivisibile
e l’anteprima social continua a funzionare, ma la pagina non finisce nei risultati di ricerca.
Per farla indicizzare basta togliere quella riga.

## Attivare Pages

Impostazioni del repo, sezione Pages, sorgente `Deploy from a branch`, branch `main`,
cartella `/ (root)`. La pubblicazione richiede un paio di minuti.
