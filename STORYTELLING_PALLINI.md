# Il viaggio dei 4 pallini — storytelling e animazione

I quattro pallini **sono** i quattro ambiti: cibo `#d8a94e`, ambiente `#7ebdae`, salute `#d08b80`, agricoltura `#aab322`.
Sono il filo del film: non sono decorazione, sono i protagonisti che attraversano tutte le scene.

Da p01 a p09 il percorso è già in opera e collaudato (rilevato dal codice: cue in `cinema.html`, preset in `wow.html`).
Da p10 in poi va progettato — è quello che questo documento definisce.

---

## Le cinque regole del filo

1. **Mai un teletrasporto.** Ogni scena termina con i pallini in una *posizione d'uscita*; la scena dopo li fa partire **da lì**. Il livello dei pallini (`#cineDots`) è unico e persiste tra le scene: la continuità è tecnicamente possibile.
2. **Sempre quattro, sempre quegli stessi colori.** Mai tre, mai colori diversi.
3. **Il movimento è sempre lo stesso della prima parte del film**: una transizione di posizione (scorrono e si posano). Niente coreografie nuove inventate per una singola scena.
4. **Se spariscono, c'è un motivo narrativo** (entrano nella casa, si tuffano nel seme). Mai sparire "perché finisce la scena".
5. **Se si riuniscono in fila, i pallini fermi nelle posizioni precedenti si spengono subito**: in scena c'è una cosa sola.

---

## ATTO I — Nascono (p01 → p03) · *già in opera*

| Scena | Cosa fanno | Uscita |
|---|---|---|
| **p01 · Copertina** | Nascono accanto alle quattro parole (cibo, ambiente, salute, agricoltura), alternati ai lati | accanto alle parole |
| **p02 · Intreccio** | Si dispongono lungo la catena delle frasi; **impulsi di luce corrono da uno all'altro** = sono interdipendenti, non a coppie | raccolti sotto la frase di rottura |
| **p03 · Conseguenze** | Firma in riga bassa; a ogni numero **si accende il pallino dell'ambito colpito** e gli altri si attenuano | in firma, in basso |

## ATTO II — Entrano nella casa e diventano il nome (p04 → p05) · *già in opera*

| Scena | Cosa fanno | Uscita |
|---|---|---|
| **p04 · Casa tratteggiata** | Dalla firma **si spengono entrando nella casa**; poi riappaiono accesi sulle **quattro ancore** della casa | sulle quattro ancore |
| **p04b · Reveal C·A·S·A** | Dalle ancore salgono e diventano gli **accenti sopra le lettere**: il filo diventa il nome | accenti sulle lettere |
| **p05 · Nascita** | **Si tuffano nel seme** e spariscono dentro l'idea | assorbiti (invisibili) |

## ATTO III — Fanno funzionare la casa (p09 → p12)

| Scena | Cosa fanno | Uscita |
|---|---|---|
| **p09 · Come opera** *(già in opera)* | Riemergono nel quadrante e **uno si posa su ogni nodo** man mano che la fase si accende; alla fine percorrono l'anello e restano sui quattro nodi | sui quattro nodi |
| **p10 · Per chi** *(nuovo)* | Dai nodi **si aprono verso l'esterno** e si posano alle **quattro porte** (i quattro destinatari): stessa quadripartizione, nuovo significato | alle quattro porte |
| **p11 · Chi rende possibile** *(nuovo)* | Rientrano in **fila-firma** sotto il titolo, poi salgono e si posano accanto ai **garanti scientifici**: ambiente→CMCC, agricoltura+cibo→CREA (pallino bicolore), salute→S. Lucia | accanto al trio |
| **p12 · Patrimonio** *(nuovo)* | Scendono ed **entrano nella casa** — e stavolta la **accendono**: ognuno diventa la **lampada** di una finestra. *(callback di p04: prima entrarono al buio, ora accendono)* | lampade alle finestre |

## ATTO IV — La strada e la firma (p13 → p14b)

| Scena | Cosa fanno | Uscita |
|---|---|---|
| **p13 · Roadmap** *(nuovo)* | **Escono dalle finestre**, scendono sulla strada e avanzano in **convoglio verso la luce** all'orizzonte; si fermano come firma sul ciglio | firma sul ciglio |
| **p14 · Direzione scientifica** | Firma sotto il ritratto: eco dei "quattro ambiti" del titolo | firma |
| **p14b · Prossime azioni** | Firma in basso; **a ogni azione che si accende il pallino corrispondente pulsa** una volta | firma |

## ATTO V — Se ne vanno (p15)

| Scena | Cosa fanno |
|---|---|
| **p15 · Finale** | Salgono come **accenti sopra le lettere**; ogni lettera **implode dentro il suo pallino**; i quattro si mettono **in fila indiana** e partono come **cometa** verso l'orizzonte — il filo continua oltre il film |

---

## Gli agganci fra una scena e l'altra (il montaggio)

Ogni riga è un "passaggio di consegne": dove sono alla fine di una scena → come entrano nella successiva.

| Stacco | Escono da… | Entrano come… |
|---|---|---|
| p09 → p10 | quattro nodi del quadrante | si aprono verso le quattro porte (movimento diretto, nessun riposizionamento) |
| p10 → p11 | quattro porte | si raccolgono in fila-firma, poi salgono ai tre garanti |
| p11 → p12 | accanto al trio | scendono in riga davanti alla porta di casa, poi salgono alle finestre |
| p12 → p13 | lampade alle finestre | escono e scendono in convoglio sulla strada |
| p13 → p14 | firma sul ciglio | firma sotto il ritratto |
| p14 → p14b | firma | firma in basso |
| p14b → p15 | firma | salgono sopra le lettere come accenti |

---

## Nota tecnica per l'implementazione

- I preset esistenti già validi: `word`, `chain`, `pulse`, `sign`, `intohouse`, `anchors`, `accent`, `dive`, `operate-phase`, `operate-cycle`.
- Da scrivere nuovi, con la stessa meccanica (transizione di posizione su `left/top`): `doors` (p10), `credits-trio` (p11), `windows-lamp` (p12), `road-convoy` (p13), `actions-pulse` (p14b).
- Il finale (`accents-final` + uscita cometa) è già scritto e verificato.
- Ogni preset deve essere **rieseguibile al resize** (le posizioni sono in pixel) e i pallini DOM vanno spenti **senza ritardo** quando passano al canvas.
