# SpaceCourier VR — Game Design Document

**Versione:** 0.2 — Draft  
**Data:** Maggio 2026  
**Team:** Discovery Indie Game  
**Piattaforma target:** PC VR (Meta Quest / SteamVR)  
**Genere:** Roguelike / Action / VR Simulation  

---

## Indice

1. [Concept & Vision](#1-concept--vision)
2. [Pillars di Design](#2-pillars-di-design)
3. [Storia & Setting](#3-storia--setting)
4. [Game Loop](#4-game-loop)
5. [Gameplay — Il Pacco](#5-gameplay--il-pacco)
6. [Gameplay — L'Astronave](#6-gameplay--lastronaute)
7. [Gameplay — Il Giocatore](#7-gameplay--il-giocatore)
8. [Sistema Economico & Missioni](#8-sistema-economico--missioni)
9. [Hub & Progressione Persistente](#9-hub--progressione-persistente)
10. [Nemici & Combattimento](#10-nemici--combattimento)
11. [Esplorazione dei Pianeti](#11-esplorazione-dei-pianeti)
12. [UI/UX & VR Design](#12-uiux--vr-design)
13. [Audio & Visual Direction](#13-audio--visual-direction)
14. [Tecnologia & Scope](#14-tecnologia--scope)
15. [⚠️ Lacune & Punti Aperti](#15-lacune--punti-aperti)

---

## 1. Concept & Vision

SpaceCourier VR è un roguelike in VR in prima persona ambientato nello spazio. Il giocatore veste i panni di un corriere spaziale senza scrupoli: consegna pacchi di ogni genere — legali o illegali — per portare a casa abbastanza crediti da mantenere la propria famiglia.

Ogni "partita" rappresenta una settimana lavorativa. L'obiettivo è sopravvivere, consegnare, guadagnare. La morte del personaggio (o la distruzione della nave) azzera i progressi della run, ma l'Hub familiare e parte dei crediti restano.

> **Ispirazione di riferimento:** *Hardspace: Shipbreaker*, *Viscera Cleanup Detail*, *No Man's Sky*, *Unpacking* (per il tatto degli oggetti in VR), *Hades* (per la narrativa roguelike).

> ⚠️ **LACUNA:** Mancano titoli di riferimento concordati dal team. Definire 2–3 giochi target come benchmark di qualità e di feel.

---

## 2. Pillars di Design

| Pillar | Descrizione |
|--------|-------------|
| **Scelta Morale** | Ogni consegna porta a un dilemma etico. Maggiore è il rischio morale, maggiore è la ricompensa. |
| **Tensione Fisica VR** | Il giocatore interagisce fisicamente con la nave, i pacchi, le armi. L'immersione è il cuore dell'esperienza. |
| **Progressione Significativa** | La morte resetta la run, ma non la famiglia. Il giocatore sente che ogni sforzo conta. |
| **Gestione del Rischio** | Ogni scelta — quale missione accettare, se riparare ora o dopo, quale arma portare — ha peso reale. |

---

## 3. Storia & Setting

### Ambientazione

Il gioco è ambientato in un futuro prossimo spaziale, in cui le corporazioni di logistica dominano le rotte interplanetarie. Il giocatore è un corriere freelance, un "mulo dello spazio", che vive sulla propria astronave e lavora per chiunque paghi abbastanza.

### Il Protagonista

Il personaggio è un **Clone/Sintetico** — ogni run è tecnicamente un nuovo individuo, narrativamente giustificando il respawn roguelike. Il giocatore precedente "non ce l'ha fatta"; il nuovo clone porta le stesse memorie e l'eredità dell'Hub.

### La Famiglia

La famiglia del protagonista vive nell'**Hub**, una stazione spaziale (o base planetaria) che cresce e si evolve con i crediti portati a casa. La famiglia non combatte, non aiuta direttamente: è la motivazione emotiva del giocatore.

> ⚠️ **LACUNA:** Il ruolo narrativo della famiglia è accennato ma non definito. Rispondere a:
> - Chi sono i membri della famiglia? (nomi, personalità, relazioni)
> - Come interagisce il giocatore con loro? (dialoghi, cutscene, lettere?)
> - L'Hub evolve visivamente? Con quali milestone?
> - La famiglia reagisce alla morte del clone? Come viene spiegato il respawn ai familiari?

---

## 4. Game Loop

### Loop Principale (Una Run = Una Settimana Lavorativa)

```
[HUB] → Sveglia sulla nave → [BACHECA MISSIONI] → Scegli consegna
      → [VIAGGIO] Guida la nave → [RITIRO PACCO] → [VIAGGIO] Dirigiti alla destinazione
      → [SCONTRI] Sopravvivi ai nemici → [RIPARAZIONE] Se necessario
      → [CONSEGNA] Lascia il pacco → [GUADAGNO] Ricevi crediti
      → Ripeti fino a fine settimana o morte
      → [FINE RUN] Porta crediti all'Hub → Upgrade persistenti
```

### Loop Secondario (Sessione Singola)

1. Scegliere la consegna dalla bacheca
2. Ritirare il pacco (pickup fisico o automatico)
3. Pilotare la nave verso il punto di consegna
4. Sopravvivere agli scontri lungo la rotta
5. Riparare la nave (fuori combattimento)
6. Effettuare la consegna
7. Incassare e scegliere la prossima missione

> ⚠️ **LACUNA:** Non è definita la **struttura temporale** della settimana lavorativa:
> - Quante consegne si possono fare in una settimana?
> - C'è un timer reale o un contatore di missioni?
> - Quando "finisce" la settimana — dopo N consegne, dopo X ore di gioco, o c'è un evento trigger?

---

## 5. Gameplay — Il Pacco

### Tipologie di Pacco

| Tipo | Posizionamento | Effetto sul Gameplay |
|------|---------------|----------------------|
| **Grande** (opzione A) | Sopra la nave | Limita la visuale della torretta |
| **Grande** (opzione B) | Dietro, come rimorchio | Limita la manovrabilità della nave |
| **Piccolo** | Interno alla nave | Nessun impatto sulla guida |

### Modalità di Consegna

**Drop-off:**
- Lancio attraverso un portale spaziale (mini-gioco di precisione)
- Attracco al porto: trasferimento manuale fisico del pacco
- Automatico per Pacchi Grandi (agganciamento/sgancio)

**Pick-up:**
- Intercetta al volo pacchi lanciati da portali
- Attracco al porto: caricamento fisico
- Agganciamento automatico per Pacchi Grandi (possono subire danni durante il trasporto se colpiti)

### Categorie Merceologiche (e Rischio Associato)

| Categoria | Rischio | Ricompensa | Note |
|-----------|---------|------------|------|
| Beni comuni (pentole, cibo) | Basso | Bassa | Pochi nemici |
| Animali vivi | Medio | Media | Pacco fragile, richiede cura |
| Armi | Alto | Alta | Pirati, polizia spaziale |
| Sostanze illegali | Molto alto | Molto alta | Nemici aggressivi, legge |
| Persone / Bambini | Massimo | Massima | Dilemma morale forte |

> ⚠️ **LACUNA:** Non è definito il **sistema di reputazione** legato alle consegne eticamente discutibili:
> - Ci sono fazioni che reagiscono alle scelte del giocatore?
> - Ci sono conseguenze narrative (la famiglia commenta le scelte)?
> - Il giocatore può essere "schedato" da autorità spaziali per consegne illegali ripetute?

---

## 6. Gameplay — L'Astronave

### Caratteristiche Generali

La nave è l'unico mezzo di trasporto e rappresenta la "casa mobile" del giocatore. La sua distruzione (esaurimento dei Punti Struttura) termina la run. I potenziamenti acquisiti durante la run vengono persi, ma quelli persistenti (acquistati tra le run) restano.

### Moduli della Nave

| Modulo | Funzione | Stato |
|--------|----------|-------|
| Bacheca Missioni | Accettare e visualizzare le consegne | Definito |
| Torretta | Arma principale per gli scontri spaziali | ⚠️ Da definire |
| Sedile di Guida | Pilotare la nave | Definito |
| Modulo Aggiornamenti | Potenziare la nave durante la run | Definito |
| Portellone Esterno | Accesso all'esterno della nave | Definito |
| Oblò | Visuale esterna senza uscire | Definito |
| Rastrelliera Armi | Stoccaggio armi sulla nave | ⚠️ Da definire |

### Potenziamenti Persistenti (tra le Run)

| Upgrade | Effetto |
|---------|---------|
| Gancio Traino | Permette di agganciare Pacchi Grandi posteriori |
| Trasporto Superiore | Consente di trasportare Pacchi Grandi sul tetto |

> ⚠️ **LACUNA:** La lista dei potenziamenti persistenti è minima. Espandere con:
> - Scudo/Hull upgrades (aumento Punti Struttura base)
> - Motori più veloci
> - Torretta avanzata
> - Modulo di riparazione automatica
> - Slot cargo aggiuntivi
> - Costo in crediti di ogni upgrade
      - _Utilizzare invece dei crediti, dei progetti (con consegne o esplorazione otttieni progetti che ti permettono il potenziamento)_

### Riparazione

- Avviene **solo fuori combattimento**, da fermi
- Alcuni danni si riparano dall'**interno**, altri dall'**esterno** della nave (richiede uscire)
- Richiede **componenti specifici** (ottenibili tramite acquisto o ricompense missione)
- Le zone danneggiate sulla scocca presentano un **mini-gioco** di riparazione
- Consumo di componenti ad ogni riparazione

> ⚠️ **LACUNA:** Il sistema di danno fisico non è specifiato:
> - Quante zone di danno ha la nave? (es. motori, scudo, torretta, scafo)
> - Ogni zona ha effetti gameplay distinti se danneggiata?
> - Descrivere il mini-gioco di riparazione (saldatura? puzzle di cavi?)

---

## 7. Gameplay — Il Giocatore

### Morte e Respawn

- Se i Punti Ferita del giocatore si esauriscono → **fine run**
- Il gioco **non salva i progressi della run** corrente
- Viene generato un nuovo **Clone/Sintetico** per la run successiva

### Dotazione Iniziale

Ad ogni run, il giocatore sceglie un loadout tra opzioni predefinite

Come viene composto l'inventario del giocatore?
- Arma a corto raggio (es. pistola), nella fondina di destra. ES. Porti la mano sulla cintura, grab ed hai la pistola
- Arma Pesante (es. fucile o randello), dietro la schiena.
- Lanciabili (es. granata), nella fondina di sinistra.
- Equipaggiamento (es. scarpe anti-gravita'), guardabile da orologio sul braccio (tipo pip-boy).

### Movimento in VR

**All'interno della nave (microgravità):**
- Movimento libero aggrappandosi alle maniglie (climbing locomotion, stile *Lone Echo*)
- Nessuna gravità artificiale di default

**Su pianeti / stazioni con gravità:**
- Scelta tra **teletrasporto** o **camminata libera** (da decidere se entrambi o solo uno)

> ⚠️ **LACUNA — DECISIONE CRITICA:** Il metodo di locomozione è fondamentale per il comfort VR e l'accessibilità. Decidere:
> - Si supportano entrambe le modalità (teletrasporto + smooth locomotion) con toggle nelle impostazioni? (raccomandato per accessibilità)
> - Il movimento con maniglie nella nave è sempre fisico o c'è un'alternativa per chi soffre di motion sickness?

### Inventario e Orologio (Pip-Boy Style)

Il giocatore ha al polso un **orologio multifunzione** che mostra:
- Mappa spaziale
- Stato dell'equipaggiamento
- Modulo di aggiornamento mid-run

> ⚠️ **LACUNA:** L'inventario fisico non è completamente definito:
> - Quante armi può portare contemporaneamente?
> - Il giocatore può raccogliere armi/oggetti durante la run (drop da nemici, loot)?
> - Come funziona il modulo di aggiornamento mid-run? Costa crediti? È legato a eventi?

---

## 8. Sistema Economico & Missioni

### Struttura delle Missioni

Ogni missione ha:
- **Mittente** (chi ha il pacco)
- **Destinatario** (dove consegnare)
- **Tipo di merce** (categoria merceologica)
- **Ricompensa in crediti**
- **Livello di rischio** (indica quanti/quali nemici aspettarsi)
- **Condizioni speciali** (es. "consegna entro X tempo", "non aprire il pacco")

> ⚠️ **LACUNA:** Il sistema di generazione missioni non è definito:
> - Le missioni sono generate proceduralmente o handcrafted?
> - Quante missioni appaiono in bacheca simultaneamente?
> - Ci sono missioni secondarie o narrativamente rilevanti (storyline di clienti)?
> - Esiste un sistema di rating/reputazione con clienti o fazioni?

### Flusso dei Crediti

```
Crediti guadagnati dalla run
        │
        ├──► Riparazioni e acquisti MID-RUN (componenti, armi)
        │
        └──► Crediti portati all'Hub
                    │
                    ├──► Upgrade persistenti della nave
                    └──► Evoluzione dell'Hub / Famiglia
```

> ⚠️ **LACUNA:** Non c'è una tabella di costi/ricompense di riferimento. Definire:
> - Range di crediti per missione (per tipo di rischio)
> - Costo dei componenti di riparazione
> - Costo degli upgrade persistenti
> - Percentuale di crediti "salvata" in caso di morte

---

## 9. Hub & Progressione Persistente

### Cos'è l'Hub

L'Hub è la base "sicura" della famiglia del protagonista. Cresce visivamente e funzionalmente man mano che il giocatore porta crediti a casa tra le run. È il luogo in cui il giocatore si sveglia all'inizio di ogni run.

### Livelli di Evoluzione (Bozza)

| Livello | Crediti Richiesti | Cambiamenti Visivi/Funzionali |
|---------|-------------------|-------------------------------|
| 1 — Rifugio | 0 | Modulo base, famiglia in condizioni precarie |
| 2 — Casa | Da definire | Struttura migliorata, nuovo stanza/area |
| 3 — Stazione | Da definire | Officina, possibilità di upgrade nave più avanzati |
| 4 — Colonia | Da definire | Hub grande, accesso a missioni speciali |

> ⚠️ **LACUNA:** L'intera progressione dell'Hub è da progettare:
> - Quanti livelli di evoluzione ci sono?
> - Cosa si sblocca a ogni livello (gameplay, narrativa, cosmesi)?
> - I membri della famiglia hanno storie personali che evolvono?
> - Ci sono NPC nell'Hub che offrono servizi (mercante, armaiolo, meccanico)?

---

## 10. Nemici & Combattimento

### Tipologie di Nemici (Bozza)

| Tipo | Comportamento | Contesto |
|------|---------------|----------|
| Pirati Spaziali | Attaccano la nave durante il viaggio | Rotte ad alto traffico |
| Polizia Spaziale | Intercettano carichi illegali | Missioni rischiose |
| Clienti Arrabbiati | Attaccano se una consegna va male | Conseguenze missioni |
| Cacciatori di Taglie | Inseguono il giocatore dopo azioni illegali | Meta-progressione |
| Alieni | Attaccano per motivi di trama | Lore |

> ⚠️ **LACUNA:** Il sistema di combattimento è quasi completamente assente nel GDD:
> - **Combattimento navale:** come funziona la torretta? Mira manuale in VR? Auto-aim? Archi di fuoco?
> - **Combattimento a piedi:** quando il giocatore scende dalla nave, come si combatte? (shooting VR, mischia fisica?)
> - Quanti nemici per scontro? Pattern di attacco? Boss?
> - I nemici salgono mai a bordo della nave?
> - C'è un sistema di difficoltà scalabile (roguelike scaling)?

---

## 11. Esplorazione dei Pianeti

### Modalità di Interazione con i Pianeti

**Dalla nave (senza atterrare):**
- Volo a bassa quota sulla superficie
- Mini-gioco "gru/grab" per raccogliere oggetti di interesse
- Interazione con punti di interesse dall'orbita

**Con attracco (scendendo dalla nave):**
- Esplorazione a piedi di zone limitate (porto, avamposto, città)
- Incontro con NPC, nemici, venditori
- Recupero di oggetti, missioni locali

> ⚠️ **LACUNA — DECISIONE STRATEGICA:** L'esplorazione planetaria è il punto più aperto del design. Il team deve decidere lo **scope** prima di procedere:
> - **Opzione A (Low Scope):** Solo interazioni dalla nave. Niente atterraggi esplorativi. Più semplice da implementare, mantiene il focus sulla nave.
> - **Opzione B (Mid Scope):** Attracco per consegne con zone limitate e lineari (corridoi, porti). Esplorazione minima ma presente.
> - **Opzione C (High Scope):** Mondo aperto parziale. Rischio alto di feature creep — sconsigliato per un team indie senza roadmap chiara.
>
> **Problema chiave identificato nel GDD originale:** *perché il giocatore dovrebbe esplorare invece di fare consegne?* Serve un incentivo gameplay concreto (es. loot esclusivo, missioni secondarie, componenti rari).

---

## 12. UI/UX & VR Design

### Principi UI in VR

- Tutta la UI deve essere **diegetica** (nel mondo di gioco, non sovrimposta)
- L'orologio al polso è l'hub informativo principale
- Nessun HUD classico sovrapposto alla visuale

### Elementi UI Identificati

| Elemento | Tipo | Posizione |
|----------|------|-----------|
| Orologio Pip-Boy | Diegetico | Polso sinistro del giocatore |
| Bacheca Missioni | Diegetico | Sulla nave |
| Indicatori danno nave | Diegetico | Luci/display nella cabina |
| Mappa spaziale | Diegetico | Orologio / display nave |

> ⚠️ **LACUNA:** L'intera sezione UI/UX manca nel GDD originale. Definire:
> - Come il giocatore visualizza i Punti Ferita propri? (visuale periferica? display orologio?)
> - Come funziona la mappa spaziale? (3D olografica? 2D sul display?)
> - Come vengono presentate le missioni in bacheca? (fogli fisici? schermo touch?)
> - Comfort settings VR: vignetting durante il movimento, opzioni per motion sickness

---

## 13. Audio & Visual Direction

> ⚠️ **LACUNA — Sezione completamente assente.** Da definire:

### Visual Direction
- Stile artistico: realistico, stilizzato, cel-shaded?
- Palette cromatica dell'universo di gioco
- Design della nave (concept art)
- Design dei pianeti (quanti biomi? ambienti differenti?)

### Audio Direction
- Musica: temi per Hub, viaggio, combattimento
- Sound design VR: ogni interazione fisica deve avere feedback sonoro
- Doppiaggio: ci sono personaggi parlanti? (famiglia, clienti, radio di bordo?)
- Silenzio spaziale vs. atmosfera sonora

---

## 14. Tecnologia & Scope

### Stack Tecnologico

| Area | Tecnologia |
|------|-----------|
| Engine | Unity |
| VR SDK | Da definire (OpenXR / Meta XR SDK / SteamVR) |
| Fisica | Unity Physics / PhysX |
| Procedural Generation | Da definire (per missioni, rotte, nemici) |

> ⚠️ **LACUNA:** Manca completamente una sezione tecnica e di scope:
> - Quale SDK VR si usa? (OpenXR è raccomandato per cross-platform)
> - Target hardware: Quest standalone? PC VR? Entrambi?
> - Risoluzione/performance target (72fps? 90fps?)
> - Il mondo di gioco è procedurale o handcrafted?
> - Quanto tempo di gioco si stima per una run completa?
> - Quante run per completare la progressione dell'Hub?

### Team e Responsabilità

> ⚠️ **LACUNA:** Non è definita la struttura del team:
> - Chi è responsabile di ogni area (gameplay, arte, audio, tech)?
> - Qual è la timeline/milestone del progetto?
> - C'è un MVP (Minimum Viable Product) definito con le feature minime per un playtest?

---

## 15. ⚠️ Lacune & Punti Aperti

Riepilogo di tutte le decisioni aperte che il team deve discutere e risolvere prima di procedere con lo sviluppo:




⚠️⚠️
	1. vr o no?
	2.  se vr: standalone o no ?
	3. obbiettivo: 
		 - espandere conoscenze
		 - farsi conoscere ig/fiere
		 - lucrare non fine principale, ma possibilitá
	4. multiplayer o no? -> obbiettivo futuro?
	5. 



### 🔴 Priorità Alta (bloccanti per lo sviluppo)

- [ ] **Metodo di locomozione VR** — teletrasporto, smooth, o entrambi con opzione?
- [ ] **SDK VR e target hardware** — Quest standalone, PC VR, o entrambi?
- [ ] **Scope esplorazione pianeti** — Opzione A / B / C (vedi $11)
- [ ] **Sistema di combattimento** — meccaniche torretta e combattimento a piedi
- [ ] **Struttura della settimana lavorativa** — timer, contatore missioni, trigger di fine run

### 🟡 Priorità Media (necessari per il GDD completo)

- [ ] **Sistema di reputazione/fazioni** — conseguenze delle scelte morali
- [ ] **Generazione procedurale delle missioni** — come si popola la bacheca
- [ ] **Tabella economica** — costi, ricompense, bilanciamento
- [ ] **Lista completa upgrade nave** — persistenti e mid-run
- [ ] **Progressione Hub** — livelli, sblocchi, storia familiare
- [ ] **Sistema inventario** — slot, loot, armi raccoglibili mid-run

### 🟢 Priorità Bassa (da definire in fase di produzione)

- [ ] **Visual & Audio Direction** — stile artistico, musiche, doppiaggio
- [ ] **Mini-gioco riparazione** — design dettagliato
- [ ] **Titoli di riferimento concordati** — benchmark qualità
- [ ] **Struttura del team e milestone** — piano di produzione
- [ ] **Narrativa famiglia** — personaggi, dialoghi, archi narrativi
- [ ] **Design nemici** — comportamenti, pattern, boss

---

*Documento generato dal team SpaceCourierVR — da aggiornare iterativamente ad ogni sessione di design.*
