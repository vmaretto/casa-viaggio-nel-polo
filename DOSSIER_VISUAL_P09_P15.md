# DOSSIER REVIEW VISUAL — p09 → p15 (senza voce narrante)

Review rigirata su richiesta: gli esperti (Art Director + Motion Designer per pagina) hanno valutato
**solo l'aspetto visivo** — composizione, tipografia, colore, dettagli, coreografia del movimento.
**Esclusi**: voce narrante, sincronizzazione audio/testo, contenuti business (in standby, voce rifatta alla fine).

Screenshot di riferimento: stati finali 1920×1080 in scratchpad/shots/rev2/.
Sostituisce, per la parte visiva, DOSSIER_REVIEW_P09_P15.md.

---

## P09 — Come opera · VOTO 5.5/10

Tipografia Cormorant ottima, ma lo stato finale sembra un fotogramma interrotto: un cerchio solo, 4 tacche da 1px, 60% del frame vuoto.

1. **[ART] Nodi ridotti a tacche ~2×24px** di colori incoerenti → veri nodi: dot pieno 10px colore ambito + ring 22px stroke 1.5px alpha 40% + label fase Outfit 13px tracking .14em uppercase a 28px dal nodo. Nodo attivo 100%, gli altri al 45% — il ciclo deve leggersi anche da fermo.
2. **[ART] Blocco testo non centrato nel cerchio** (baseline "Trasferire" ~y540 vs centro ~y560, ~280px vuoti sotto la caption) → ricentrare sul centro ottico (geometrico −12px), "Trasferire" 110→128px.
3. **[ART] Anello con luminanza incoerente + anello fantasma disassato in basso** (effetto doppia esposizione) → un solo anello stroke 1px, gradiente conico da #aab322 pieno (nodo attivo) a rgba(247,245,238,.14); eliminare o rendere concentrico (alpha .06) il secondo anello.
4. **[MOTION] La staffetta non lascia traccia: i 4 pallini assenti nel finale** → i pallini si posano sui 4 nodi e restano: arrivo scaglionato 4×120ms, scale 0→1 cubic-bezier(0.16,1,0.3,1) 600ms, glow 8px che decade in 900ms.
5. **[MOTION] Chiazza luminosa statica fuori composizione** → radial 900px ancorato al nodo attivo, opacità .10, migra da nodo a nodo (1.2s ease-in-out).

## P10 — Per chi è CASA · VOTO 4.5/10

Concept radiale giusto, esecuzione no: icone clip-art (bocciate), geometria sbilenca, **caption tagliata dal bordo destro**.

1. **[ART] BUG BLOCCANTE — caption in basso a destra troncata a x=1920** ("…in capacità ut[ili]") → centrare a x=960, y=1010, Cormorant italic 26px, max-width 1100px (eventualmente 2 righe).
2. **[ART] Sostituire i glifi clip-art** → concept "quattro ingressi, uno spazio": quarto di cerchio wireframe (arco 90°, r 44px, stroke 1.5px colore assegnato) orientato verso il centro — i 4 quarti idealmente ricompongono il cerchio CASA; dentro, numerale Cormorant italic 64px "1"–"4" paper 90%. Zero icone.
3. **[ART] Geometria radiale sbilenca** (quote/gap arbitrari, diagonali che finiscono nel vuoto) → 4 anchor su cerchio invisibile r 560px, angoli 45°/135°/225°/315°; linee stroke 1px rgba(247,245,238,.12) dal bordo del cerchio CASA (r 110) a 24px dal blocco testo.
4. **[ART] Titoli con opacità incoerenti** (2 pieni, 2 al ~55%) → tutti Cormorant 40px #f7f5ee 100%; sottotitoli Outfit 16px alpha .65 (non serif italic: troppo corsivo ovunque).
5. **[MOTION] Sequenza senza direzione + firma pallini assente** → entrata oraria da NE, stagger 260ms; linea radiale 450ms ease-out, poi arco+numerale scale .85→1 fade 500ms cubic-bezier(0.16,1,0.3,1); chiusa: 4 pallini firma in basso centro (y=1030, gap 18px).

## P11 — Chi rende possibile · VOTO 5/10

Impalcatura elegante, tradita dal vuoto a destra e da una violazione del requisito non negoziabile.

1. **[ART] Il box verde InnovaliaTech è visivamente ASSENTE** — riga indistinguibile dalle altre. Requisito committente violato → border 1.5px solid #aab322, fill rgba(170,179,34,.08), padding 20px 28px, radius 4px; opacità 100% nello stato finale, non segue il fade delle altre righe. **Intervento n°1 dell'intera revisione.**
2. **[ART] Metà destra del frame morta** (righe finiscono a x≈900 su 1920) → spostare l'asse spina x≈618→760 e/o descrittore a destra di ogni riga (Outfit 15px, rgba(247,245,238,.45), colonna fissa x=1180).
3. **[MOTION] Stato finale con righe "spente"** (solo Convenzioni a piena luce, le altre al ~40%) → dopo lo stagger (140ms/riga, 600ms, cubic-bezier(0.22,1,0.36,1)) settle di TUTTE le righe a rgba(247,245,238,.88); etichette ruolo al 55%. La gerarchia finale la fa il box verde, non l'opacità.
4. **[ART] Asterischi orfani CMCC*/CREA*** (nessuna nota in vista) → nota a piè pagina Outfit 12px al 40% a y=1020 (o rimuoverli). Pallini d'ambito del trio troppo piccoli (~6px) → 9px, opacità 100%.
5. **[MOTION] Spina verticale che non conduce** (glow solo sull'ultimo nodo) → line-draw scaleY 0→1 900ms cubic-bezier(0.65,0,0.35,1), ogni nodo si accende al passaggio (fill #aab322, glow 12px che decade); stato finale: tutti e 5 accesi.
6. **[SISTEMA] Manca la firma 4 pallini** prevista per le pagine di elenco.

## P12 — Patrimonio · VOTO 6/10

Idea dei gradini giusta, ma la scala zigzaga e il finale è sbilanciato sull'ultima card.

1. **[ART] La scala non scende: zigzaga** (offset ≈255/375/300/435px, card 3 rientra) → progressione monotona x = 260/380/500/620 (passo 120px), larghezza card costante 1080px.
2. **[MOTION] Solo "Relazioni" viva nel finale, le altre fantasmi al 35–50%** → stagger 160ms, translateY 24px→0 + fade 550ms cubic-bezier(0.22,1,0.36,1); settle: titoli 90% paper, keyword 60%, fill uniforme rgba(247,245,238,.03) su tutte. Nessuna card "vincitrice".
3. **[ART] Ritmo verticale irregolare** (gap ≈75/30/90px) → gap costante 56px; "Capacità scientifiche" su una riga (h=88px come le altre).
4. **[ART] Parentesi destra sotto soglia** (linea ~1px, testo verticale ~13px) → linea 1.5px rgba(170,179,34,.55), testo Cormorant italic 18px #aab322 90%; piedini agganciati a top card 1 / bottom card 4.
5. **[MOTION] Parentesi senza gerarchia temporale** → disegnarla per ultima: line-draw 700ms ease-out dopo la 4ª card, poi fade testo verticale (300ms), poi caption (+200ms).

## P13 — Roadmap · VOTO 7/10

Diagonale elegante, ma la gerarchia luminosa lavora contro la lettura del percorso.

1. **[ART] La curva si spegne verso la meta** (acido→grigio nell'ultimo terzo) → invertire il gradiente: rgba(170,179,34,.35) al 2026 → #aab322 pieno sull'endpoint. Ora racconta "slancio che muore".
2. **[ART] Etichette scollate dai nodi** ("2026/Fondare" ~90px sopra il pallino) → blocchi a 32px dal nodo + tick verticale 16px/1px colore nodo che collega baseline→nodo.
3. **[ART] Contrasto sotto soglia sulle tappe non attive** (~3:1) → numerali non attivi ≥ rgba(247,245,238,.55), descrizioni ≥ .62 (≥4.5:1).
4. **[MOTION] Nodi senza evento** → per tappa: curva line-draw 0.9s cubic-bezier(0.65,0,0.35,1) fino al nodo, nodo scale 0→1.3→1 in .35s, blocco testo translateX(−24px)+fade .5s cubic-bezier(0.16,1,0.3,1); pausa .4s tra tappe; endpoint: pulse singolo (scale 1→1.5→1, .8s), non loop.
5. **[ART] Quadrante alto-sinistra morto** (~450px vuoti) → alzare la curva di ~80px o farla partire fuori campo (x=−40).

## P14 — Direzione scientifica · VOTO 6/10

Impaginato pulito, ma il ritratto è un corpo estraneo cromatico e il baricentro è sbagliato.

1. **[ART] La foto rompe la palette** (unici blu del film) → duotone a prescindere dalla foto definitiva: grayscale(1) contrast(1.08) brightness(1.05) + overlay #071d21 multiply 25% + velo caldo rgba(216,169,78,.12).
2. **[ART] Blocco fuori baricentro** (~300px morti in basso) → giù di 60px (centro ottico 54%) e/o firma 4 pallini in basso (8px, gap 20px, y≈900) che fa eco a "quattro ambiti".
3. **[MOTION] Zoom 15s su cerchio ~180px impercettibile** → ritratto a 280px o Ken Burns interno alla maschera (inner scale 1.08→1.18, 15s linear, origin 50% 35%). Lo zoom si fa sul contenuto, mai sul contenitore.
4. **[ART] Anello tratteggiato fragile** → anello solido 1.5px rgba(216,169,78,.6) a 6px dal bordo (eventuale doppio: 1px pieno + 1px al 30% esterno).
5. **[MOTION] Entrata piatta** → headline fade+rise 20px (1s) → cornice si disegna 0→360° 1.2s mentre la foto va da blur(8px) a fuoco → nome (.6s) → credenziale (.6s, delay .2s); poi parte lo zoom.
6. **[NOTA] Oro credenziale ≈ colore ambito cibo #d8a94e** → se l'oro-prestigio deve esistere, differenziare (es. #c9a35a) o accettare consapevolmente.

## P14b — Prossime azioni · VOTO 7/10

Pulita, a due micro-passi dal riferimento.

1. **[ART] Titolo orfano vs lista a x≈470: nessuna griglia** → allineare il titolo alla colonna dei cerchi (x=470) e alzare la lista ~40px (o gap titolo→riga 01 da ~90 a 64px).
2. **[ART] Numerali 01–03 troppo piccoli** → numerale 14→20px, cerchio 64px, stroke rgba(170,179,34,.85), width 1.25px.
3. **[ART] Hairline incoerenti** (3 sotto, nessuna sopra la 01) → aggiungere hairline sopra la 01 o togliere quella dopo la 03.
4. **[ART] Descrizioni sottotono** → alpha .6→.78, size 16→18px, line-height 1.5 (scala 30/18).
5. **[MOTION]** titolo fade+rise 8px 600ms cubic-bezier(0.16,1,0.3,1); righe stagger 260ms: cerchio stroke-dashoffset 450ms, numerale +150ms, titolo slide-in 12px, hairline scaleX 0→1 origin left 500ms.

## P15 — Finale C·A·S·A · VOTO 6/10

Lockup tipograficamente bello, ma due violazioni di sistema: fondo beige e **filo dei 4 pallini assente nel frame finale**.

1. **[ART] Fondo beige = rottura del sistema** → ink #071d21 con radial sottile come p14b; lettere nei colori d'ambito PIENI (su ink le varianti spente muoiono); frase paper; etichette colore ambito .85.
2. **[ART/MOTION] Pallini assenti sopra le lettere: il payoff del film non chiude** → 4 dot Ø10px a 28px sopra la cap-height, centrati sull'asse ottico di ogni lettera; se già "partiti", deve restare la traccia: scie verticali gradiente (colore→trasparente, h 120px, opacity .35) o hairline d'orizzonte a y=380.
3. **[ART] Spaziatura ottica del lockup irregolare** (A–S più stretto ~15–20px) → equalizzare i vuoti ottici a ~105px dai terminali reali; ricentrare etichette AMBIENTE/SALUTE sul centro ottico della lettera.
4. **[ART] I 3 pilastri sono un sussurro** → 16→19px, opacity .55→.78, letter-spacing .02em, gap 64px con "·" acido .4; gruppo su di 24px.
5. **[MOTION] Coreografia finale** → (a) pallini planano sulle lettere 800ms cubic-bezier(0.22,1,0.36,1) stagger 120ms; (b) ogni lettera fade+rise 16px innescata dall'atterraggio del suo pallino; (c) etichette +300ms; (d) hold 1.2s; (e) partenza: dot scalano a 2px e filano verso il punto di fuga (960,~430) in 1200ms ease-in, trail che decade 600ms. Frase e lockup fermi: il movimento è solo dei pallini.

---

## Temi trasversali (tutte le pagine)

- **T1 — "Stato finale = ultima battuta"**: p09, p11, p12 (e in parte p10) congelano l'ultimo step dell'animazione invece di risolversi in un tableau equilibrato: tutti gli elementi devono fare "settle" a piena leggibilità, la gerarchia la fanno colore/box, non l'opacità residua.
- **T2 — Firma 4 pallini mancante**: assente in p09, p10, p11, p14, p15 — il filo conduttore si spezza proprio nelle pagine chiave. (Nota: nel film la firma è cue-driven; verificare nel flusso reale prima di aggiungere, ma nel frame finale DEVE esserci.)
- **T3 — Box verde InnovaliaTech invisibile su p11**: priorità assoluta.
- **T4 — Caption troncata su p10**: bug bloccante.
- **T5 — Doppio accento acido/oro** (p13 vs p14): decidere se l'oro-prestigio è intenzionale.
