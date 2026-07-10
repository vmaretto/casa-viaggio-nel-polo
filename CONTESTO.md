# CONTESTO — CASA · Il viaggio comincia da qui

> File di handoff per chi (persona o AI agent) deve capire o continuare questo progetto.
> Ultimo aggiornamento: 9 luglio 2026.

## Che cos'è

Pagina web narrativa/immersiva (one-page scroll) che presenta **CASA**, il Polo per **Cibo, Ambiente, Salute e Agricoltura** (nome di lavoro). È una presentazione istituzionale con animazioni scroll-driven, pensata per essere condivisa via link.

- **Sito live**: https://casa-viaggio-nel-polo.vercel.app (deploy automatico da GitHub via Vercel)
- **Repository**: https://github.com/vmaretto/casa-viaggio-nel-polo
- **Cartella locale**: `/Users/vmaretto/Documents/Claude/Artifacts/casa-viaggio-nel-polo`

## File del repository

| File | Scopo |
|---|---|
| `index.html` | L'intera presentazione in un unico file "bundled" (~2 MB): markup, JS, font e immagini incorporati |
| `llms.txt` | Tutto il contenuto testuale in markdown — versione per AI agent (standard llms.txt) |
| `leggimi.html` | Versione testuale semantica e accessibile (light/dark), linkata via `rel=alternate` |
| `CONTESTO.md` | Questo file |

## Architettura di index.html (IMPORTANTE per chi edita)

Il file è un **bundle autogenerato** (esportato da uno strumento di design "DC"), NON un HTML normale:

1. **Righe 1–170 circa**: HTML esterno con spinner di caricamento, script runtime e manifest.
2. **Riga ~171** (`script type="__bundler/manifest"`): JSON con gli asset (immagini JPEG e font woff2) in **base64**, indicizzati da GUID. I riferimenti nel markup sono `url("<guid>")` risolti a runtime in blob URL.
3. **Riga ~179** (`script type="__bundler/template"`): il documento vero e proprio come **stringa JSON** — quindi con escaping: `\"` per i doppi apici, `\n` per i newline, `</...>` per i tag di chiusura. Contiene tutto il markup delle sezioni, gli stili e la classe `Component extends DCLogic` con la logica delle animazioni.

**Regole d'oro per editare**:
- Modificare SEMPRE tenendo conto dell'escaping della riga template (usare script Python con `str.replace` su stringhe esatte, verificando `count == 1` prima di sostituire).
- `data-rv-delay="320"` e simili NON sono unici nel file: fare match posizionali dentro la sezione giusta, non globali.
- Dopo modifiche al JS interno: estrarre la classe, de-escapare e validare con `node --check`.
- Il placeholder `{{ nomePolo }}` viene sostituito a runtime con "CASA".
- Dopo modifiche di contenuto testuale, **rigenerare `llms.txt` e `leggimi.html`** perché restino allineati.

## Struttura della presentazione (sezioni, in ordine)

Copertina · Apertura in 6 battute (il colpo / la prova-numeri / chi paga il conto / il vuoto e la finestra / perché proprio adesso / serve CASA) · Perché ora e la visione (sezione scroll-driven con particelle) · I quattro ambiti · Il metodo (ciclo: formare-operare-osservare-tradurre) · Il modello · L'ecosistema · Accordo UNIUST-Tuscia · Patrimonio esistente · I servizi · Dimensione europea e mediterranea · Cosa ottiene chi entra · Roadmap · Direzione scientifica · Chiusura.

Il testo completo è in `llms.txt`.

## Sistema di animazioni

- **Reveal** (`[data-rv]` + `data-rv-delay`): IntersectionObserver; gli elementi si rivelano entrando nel viewport e **si resettano uscendone**, così le animazioni si ripetono a ogni passaggio (scelta voluta dal committente).
- **Contatori** (`[data-count]` + `data-prefix`/`data-suffix`): conteggio animato, anch'esso ripetibile.
- **Copertina**: Ken Burns sullo sfondo (layer separato dalla parallasse JS), alone `heroGlow` pulsante dietro il titolo, titolo dal blur, sottotitolo con le 4 parole colorate in cascata (Cibo #D8A94E, Ambiente #7EBDAE, Salute #D08B80, Agricoltura #AAB322 — le iniziali spellano CASA).
- **Sezione journey** ("Perché ora e la visione"): canvas con 4 nuvole di particelle che convergono al centro durante lo scroll; etichette posizionate via JS.
- `prefers-reduced-motion` e prop `effettiRidotti`: tutto appare subito senza animazioni.

## Palette e tipografia

- Sfondi: verde scuro `#0F2B30`, crema `#F7F5EE`, sabbia `#EFEBDD`, petrolio `#3E595C`
- Accento primario: verde oliva `#AAB322`
- Ambiti: oro `#D8A94E` (cibo), verde acqua `#7EBDAE` (ambiente), rosa `#D08B80` (salute), oliva `#AAB322` (agricoltura)
- Font: **Cormorant Garamond** (corsivo, titoli) + **Outfit** (testo), entrambi incorporati nel bundle.

## Cronologia delle modifiche fatte in questa sessione

1. **Setup**: estratto il file bundled dallo zip di handoff, rinominato `index.html`, creato repo GitHub e collegato a Vercel (il primo push richiese `http.postBuffer` più alto; ora il file è piccolo e non serve più).
2. **Contenuti**: rimossa la riga contatto "FIB / InnovaliaTech" dalla chiusura; riscritta la descrizione UNIUST in due punti ("Università non statale di InnovaliaTech: costruisce programmi ibridi tra discipline e tecnologie. Parte dai sistemi autonomi con applicazioni nell'agroalimentare, per poi estendersi al campo della salute." — NON menzionare più "rilascia i titoli", "L-28", "Medicina"); sezione "Chi paga il conto": soggetti diretti ("Il sistema… Le filiere… La competitività…"); tolta la linea bianca sotto "2 · I numeri".
3. **Animazioni ripetibili**: reveal e contatori si ri-attivano a ogni ingresso nel viewport.
4. **Mobile** (media query `max-width: 768px` iniettata nello style del template):
   - "Il metodo": disattivato `position: sticky` (si sovrapponeva agli step);
   - journey: canvas confinato nella fascia alta dello schermo, testo in basso, effetti potenziati (aloni radiali, glow, doppio anello) — su richiesta esplicita del committente di qualcosa di "entusiasmante";
   - etichette dei 4 ambiti come pillole scure con bordo colorato (leggibilità sulle nuvole luminose);
   - fix "torna su": usare `overflow-x: clip` (MAI `hidden`, che crea uno scroll container su body e rompe scroll e ancore) + `id="top"` sulla copertina.
5. **Copertina ridisegnata** (mobile + desktop): rimosso l'occhiello duplicato, "benvenuti a" + titolo dal blur + cascata colorata + filo dorato; centratura con `100svh`.
6. **Accessibilità AI**: immagini ricompresse (6,2 MB → 2 MB; la texture 12067px mostrata a 460px è passata da 2,3 MB a 13 KB), creati `llms.txt` e `leggimi.html`, `<title>` reale, meta description, `link rel=alternate`.

## Preferenze del committente (Vittorio)

- Lavora per iterazioni rapide guardando il sito **dal telefono** (spesso condivide screenshot WhatsApp con annotazioni).
- Vuole effetti **scenografici e "wow"**, non soluzioni minimali: se qualcosa non funziona su mobile, va **ripensato in bello**, non semplicemente nascosto.
- Le etichette/testi devono sempre restare **leggibili** (accessibilità prima di tutto).
- Ogni modifica: **commit + push immediato** (il deploy Vercel è automatico dal branch `main`).
- Lingua di lavoro: italiano.

## Come verificare le modifiche

Server locale: `python3 -m http.server 8123` nella cartella del progetto, poi testare su viewport 375×812 (mobile) e ~1280×800 (desktop). Attenzione: le animazioni scroll-driven usano `window.scrollY`; il primo caricamento può richiedere un reload se il runtime parte male (caso raro osservato in dev, non riprodotto in produzione).
