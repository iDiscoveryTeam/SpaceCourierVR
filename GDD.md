# SpaceCourier VR

**Genere RougueLike**

L'obiettivo di fine partita e' portare a casa dei soldi per la tua famiglia
La famiglia si ritrova all'interno dell'Hub che si evolve mano a mano che il giocatore termina le partite.
piu' soldi porti a casa maggiore sara' l'evoluzione dell'Hub

Come si fanno i soldi?
Siamo dei corrieri spaziali e non ci facciamo scrupoli: bambini? animali? armi? pentole?
Consegnamo qualsiasi cosa, l'unico problema sono i nemici che ci facciamo lungo la strada.

I giocatori si ritrovano a dover affrontare scelte etiche e morali.
Una consegna standard non provochera' di certo molti nemici ma non li fara' sopravvivere economicamente
Una cosegna illegale, decisamente tutto un altro discorso; alta la ricompensa ma soprattutto alto il rischio

Il giocatore si sveglia all'interno della sua astronave (Valutarne i potenziamenti persistenti nelle partite)
Il giocatore puo' decidere fra alcune dotazioni all'inizio di ogni partita

# GameLoop del gioco:

1. Scegliere la consegna da effettuare
1. Ritirare il pacco
1. Dirigersi al punto di consegna guidando
1. Sopravvivere agli scontri
1. Riparare la nave
1. Consegnare il pacco

# Gameplay

> ## Il Pacco

Due tipologie di pacco:
1. Grande
    - Sopra la nave limitando la visuale della torretta
    - Dietro (come i rimorchi dei camion) limitando i movimenti
1. Piccolo
    - Inserito sempre all'interno della nave

Modi di consegna:

1. Consegna:
    - Lanciare i pacchi attraverso un portale
    - Attraccare ad un porto sul pianeta e trasferire manualmente il pacco
    - Automatico per i pacchi grandi, una volta raggiunta la posizione di consegna

1. Ritiro:
    - Prendere al volo i pacchi passati attraverso un portale
    - Attraccare ad un porto sul pianeta e caricare il pacco sulla nave
    - I pacchi grandi vengono agganciati automaticamente, possono perdere vita durante il trasporto se vengono colpiti

> ## L'Astronave

### Moduli

1. Bacheca per accettare una missione
1. Torretta
1. Modulo di guida:
    1. Sedile di guida
    1. Modulo per aggiornamenti
1. Rastrelliera per armi (Da decidere)
1. Portellone per l'esterno
1. Oblo

### Potenziamenti

I potenziamenti alla nave rimangono tra una partita e l'altra

1. Gancio traino: permette di collegare alcuni Pacchi Grandi
1. Trasporto superiore: consente di trasportare alcuni Pacchi Grandi

### Riparazione

La riparazione della nave avviene solo fuori combattimento, quando si e' fermi.
Alcuni componenti si possono riparare dall'interno dell'astronave, altri dall'esterno.
Sono necessari dei componenti specifici per ogni riparazione che si ottengono comprando o facendo le consegne.
Ci sono delle zone specifiche in cui appare il danno come sulla scocca della nave, in cui bisogna fare un minigioco per ripararlo.
Riparare la nave consuma questi componenti.

> ## Il Giocatore

Ad inizio di ogni partita sceglie una dotazione compresa di armi e equipaggiamento.
Il movimento del giocatore all'interno dell'astonave e' totalmente libero e senza gravita'.
Bisognara' aggrapparsi alle maniglie per potersi trascinare e muovere (come nei giochi di scalate).

1. Inventario
1. Modulo per aggiornamenti
1. Mappa (Da valutare)

> ## Elementi da definire
1. Il giocatore ha una mappa?
1. Come viene composto l'inventario del giocatore?
    - Arma a corto raggio (es. pistola), nella fondina di destra. ES. Porti la mano sulla cintura, grab ed hai la pistola
    - Arma Pesante (es. fucile o randello), dietro la schiena.
    - Lanciabili (es. granata), nella fondina di sinistra.
    - Equipaggiamento (es. scarpe anti-gravita'), guardabile da orologio sul braccio (tipo pip-boy).
1. Quale metodo di movimento utilizza il giocatore? (teletrasporto o cammininata libera? entrambe?)
1. Mettiamo la rastrelliera per armi sull'astronave? oppure rischia di snaturare l'essenza delle dotazioni?
    - Il giocatore puo' trovare, comprare o ricevere armi in giro?
1. Esporazione del pianeta se e come vogliamo implementarla?
    - Attraverso la nave, guidi sulla superfice del pianeta e quando c'e' un punto di interesse puoi interagire in diversi modi:
        - Ti cali solo in quella zona ed esplori solo quell'area
        - Guardi dall'alto e con un minigioco (tipo macchina del grab (possibile potenziamento)) devi recuperare degli oggetti
    - Devi attraccare per consegnare un pacco e scendere dalla nave:
        - Esplorazione di un mondo / citta' con nemici e/o amici
            - Problematica -> difficile da implementare e richiede un vero motivo per esporarla, il giocatore perche' decide di esporare la zona e non tirare dritto tra una consegna e l'altra?
