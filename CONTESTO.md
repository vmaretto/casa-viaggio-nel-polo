# CONTESTO — CASA · Il viaggio comincia da qui

> File di handoff per chi (persona o AI agent) deve capire o continuare questo progetto.
> Ultimo aggiornamento: 15 luglio 2026. **L'architettura vecchia (bundle 2 MB con template JSON escapato) NON esiste più.**

## Che cos'è

Presentazione web narrativa a 15 scene full-screen di **CASA**, il Polo per **Cibo, Ambiente, Salute e Agricoltura**. Il deliverable attivo è **`wow.html`**: un unico file HTML pulito e leggibile (markup + CSS + JS inline, ~2.500 righe), niente bundle, niente escaping.

- **Anteprima live**: https://casa-viaggio-nel-polo.vercel.app/wow.html (deploy automatico Vercel da `main`)
- **Repository**: https://github.com/vmaretto/casa-viaggio-nel-polo — branch di lavoro **`revisione-strategica-spazio-casa`**; l'anteprima si pubblica copiando `wow.html` su `main`
- **Cartella locale**: `/Users/vmaretto/Projects/Progetto CASA/casa-viaggio-nel-polo`
- ATTENZIONE: `index.html` su `main` è ancora la **vecchia** presentazione (bundle). Va sostituita con `wow.html` **solo ad approvazione finale** del committente.

## File chiave

| File | Scopo |
|---|---|
| `wow.html` | Il deliverable attivo: 15 scene `<section class="scene">` con `id="p01"…"p15"` e `data-title` |
| `PAGINE_APPROVATE_DALLA_CHAT.md` | Testo di riferimento vincolante (15 pagine, **in ordine inverso**) |
| `CASA_MASTER.md` | Identità, posizionamento, lessico |
| `index.html` | VECCHIA presentazione (bundle) — da sostituire solo a fine progetto |
| `assets/originale/` | Font woff2 locali (Cormorant Garamond, Outfit) e immagini |

## Testo: fonte e deviazioni approvate

Il testo segue `PAGINE_APPROVATE_DALLA_CHAT.md`, MA con deviazioni **approvate dal committente in chat**:
- Titolo p08: "L'Internet delle Risorse (IoR)"
- Slide 03 riscritta come diagnosi; slide 04 con definizione "un luogo fisico di un ettaro"
- Slide 05 sottotitolo "Diecimila metri quadri, tre zone…"
- Slide 10 titolo "Sei partner, nessuno basta da solo." con descrizioni corte
- Tagli su come-opera / per-chi / Valentini

Ogni altra modifica al testo richiede approvazione esplicita del committente.

## Struttura (id · data-title)

p01 Copertina · p02 Il problema · p03 Gli effetti attraversano gli ambiti · p04 Cosa manca davvero? · p05 Per questo nasce CASA · p06 Lo spazio CASA · p07 Dentro CASA · p08 Il principio di CASA (IoR) · p09 Come opera CASA · p10 Per chi è CASA · p11 Chi rende possibile CASA · p12 Il patrimonio di partenza · p13 Roadmap · p14 Direzione scientifica · p15 CASA (finale).

Scene chiave:
- **p01**: copertina **SENZA la parola CASA** — arriva a sorpresa in p05 (regia voluta dal committente, pensata anche per la futura versione palco con voce narrante e musica). Non "correggerla".
- **p04**: casa tratteggiata con pallini etichettati che corrono sul perimetro
- **p05**: anello di particelle con "casa" · **p06**: foto con 3 marker numerati ancorati ai luoghi + card in vetro
- **p07**: orbita dei 4 ambiti · **p08**: diagramma IoR con dimming per passo
- **p11**: righe aperte con gerarchia tipografica 42/30/26/22

## Meccanica di presentazione

- Desktop: `scroll-snap` per scena; frecce/spazio avanzano per **fragment**; attivare una scena da scroll fa partire la **cascata automatica** dei fragment (620 ms per scene cumulative, 3.4 s per scene a pannelli — costanti `stepMs` nel JS).
- Mobile: tutto statico impilato (media query, fragment sempre visibili).
- `F` = fullscreen; nav a pallini laterale.

## Modalità statica (screenshot / stampa)

- `?static`: tutte le scene attive, ultimo fragment, contatori a valore finale
- `?static&scene=pXX`: isola una singola scena
- Pipeline screenshot: Chrome headless con `--window-size` e `--virtual-time-budget` su un `python3 -m http.server` locale — **MAI `file://`**. NB: il mobile in headless ritaglia male → verificare mobile in un browser vero.

## Design system

- Palette: ink `#0f2b30` / `#071d21`, paper `#f7f5ee`, sand `#efebdd`, acid `#aab322`; ambiti cibo `#d8a94e`, ambiente `#7ebdae`, salute `#d08b80`, agricoltura `#aab322`
- Alternanza sfondi: p03/p09 crema, p12 sabbia, p15 beige finale con lettere C·A·S·A colorate. Sulle scene chiare le variabili `--food/--environment/--health/--acid` sono **ridefinite scurite** per contrasto WCAG.
- Font: Cormorant Garamond (corsivo, titoli) + Outfit (testo), woff2 locali in `assets/originale/`
- Regole dalle review: caps solo sui kicker numerati; **una** enfasi per scena; spazio al posto dei contenitori; max ~40 parole per scena.

## Flusso di lavoro col committente (Vittorio)

- Iterazioni rapide: guarda da telefono e PC, condivide screenshot annotati.
- Vuole effetti **wow** ma slide che **respirano** (aria, poche parole).
- Il testo approvato è vincolante salvo sua approvazione esplicita.
- Ogni modifica = **commit + push immediato su entrambi i branch** (lavoro + `main` per l'anteprima).
- Review periodiche con subagent (communication advisor + UI/UX designer) sui **PIXEL** (screenshot), non sul codice.

## Prossimi passi noti

1. Approvazione finale → promozione di `wow.html` a `index.html` su `main`
2. Versione palco: buio, musica americana, voce narrante, avanzamento manuale
3. Possibile CTA finale quando ci sarà un target definito
