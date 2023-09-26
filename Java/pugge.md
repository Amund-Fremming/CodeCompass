**Datastrukturer:**

- Arrays
  - Samling av elementer identifisert av indeksnummer, i java har de fast størrelse
  - Operasjoner eller innsetting er ikke dynamisk, du må selve flytte elementer
  - Søking i O(n) eller O(log n ) med sortert array og binærsøk
- Linked lists
  - Samling av noder der hver node holder data og referanse til neste node. Finnes også dobbelt linked noder
  - Operasjoner O(n), sette inn og slette O(1) om du har referanse til noden. O(n) søking
- Trees (spesielt binære søketrær)
  - Samling med rot node og samling av barnenoder
  - Binært søketre: En node har opptil to barn der venstre er alltid mindre enn foreldrenoden og høre alltid større
  - Operasjoner gjøres alt i O(logn) for BST
- Stacks & Queues
  - Stack, LIFO, Operasjoner O(1)
  - Queue, FIFO: Alle operasjojner O(1)
- Hash Maps
  - Nøkkel verdi par, bruker hashfunksjon for å plassere verdier i en array
  - Operasjoner sette inn O(1), men ved kollasjoner kan det skje O(n)

**Algoritmer:**

- Sorteringsalgoritmer (QuickSort, MergeSort, etc.)
  - Quicksort: Divide and conquer algoritme som velger en pivot og plasserer alle elementene mindre enn pivot til venstre og større til høyre og gjentar dette rekursivt. I snitt O(n log n)
  - Mergesort: også en divide and conquer algo. Deler array i to halvdeler, sorterer hver halvdel og fletter dem sammen, også rekursivt. O(n log n)
  - Insertion sort, O(n^2) inserter en og ett element inn i sortert del
  - Selection sort, O(n^2) finner minste element og putter det i sortert del
- Søkealgoritmer (binærsøk, DFS, BFS)
  - Binær søk, sortert liste, vi deler i to og sjekker midt elementet, hvis det vi søker etter er større forkaster vi venstre side og fortsetter, og motsatt andre veien.
  - DFS: Går så langt man kan fra en gren ut i grafen man kan før man går tilbake
  - BFS: Går innom alle node på nåværende dybde først
- Dynamisk programmering
- Divide og hersk-teknikker
- Greedy algoritmer

**Objektorientert programmering:**

- Grunnleggende konsepter (arv, polymorfisme, inkapsling, osv.)
  - Enkapsulering: data av en klasse skjules for andre klasser, evt get og set
  - Abstraskjon: Skjule komplekse implementering detaljer og bare vise essensielle funskjonene til objektet. Fokusere på hva e objekt gjør og ikke hvordan
  - Inheritance: Ny klasse kan arve egenskaper og metoder fra en eksisterende klasse, hjelper å oppnå gjenbruk av kode
  - Polymorfisme: Evnen til å ta flere former, hund kan extende dyr som har en methode lyd, som den vil implementere på sin egen måte
- Designmønstre (f.eks. Singleton, Factory, Observer)
  - Sikrer at en klasse kun har en instans og gir et globalt punkt for tilgang til denne instansen
  - Facotory: En fabrikk som lager objekter til deg istendenfor å bruke new ber du fabrikken lage objekter.
  - Observer: Fungerer som en nyhetsvarsling, der du abonnerer på oppdateringer, når det skjer noe nytt blir alle abonenter varslet

**Java-spesifikke emner:**

- Java Collections Framework (ArrayList, HashMap, etc.)
- Tråder og concurrency
- Unntakshåndtering
- Streams og lambdauttrykk

**Systemdesign:**

- Grunnleggende konsepter (lastbalansering, databasedesign, caching)

## Mer info

**Spørsmsål**

- Checked og unchecked exceptions
  - Checked må fanges, ofte tilfeller applikasjon må ha plan for som å lese tom fil
  - Unchecked må ikke fanges, ofte programmeringsfeil
- Hva er forskjellen på == og equals i java?
  - == sjekker om to referanser peker på samme objekt i minnet
  - Equals er en metode og sjekker om innholdsmessige likeverdighet
  - == på primitive typer int char og double sammenlikner du faktiske verdiene, siden disse ikke er objekter så == sammenlikner faktisk verdi. Brukes du WQrapper klasser vil verdier ofte over 127 ikke være == like men de før være like pga integer caching.
- Hva er garbage collecttion?
  - Det er en prosess i JVM som automatisk sletter objekter som ikke lenger er i bruk for å frigjøre minnet
- Hva er forskejllen på ArrayList og LinkedList
  - Arraylist baseres på en tabell som er dynamisk, mens linkedlist er baser på en dobbel linket liste.
  - Arraylist gir bedre ytelse for innsetting og sletting
- Hva er forskjellen mellom abstract klasse og interface?
  - En abstrakt klasse kan ha metodeimplementasjoner og abstrakte m,etoder, mens ett interface bare kan ha abstrakte metoder. En klasse kan bare arve en abstrakt klasse men kan implementere flere interface
- Hva er trådsikkerhet og hvordan oppnår du det i java?
  - Trådsikkerhet sikrer at en metode eller klasseverdi oppfører seg som forventet når den akses av flere tråder samtidig. Dette kan oppnås ved å synkronisere blokker, semaphores eller locks
- Hva er forskjhellen på final, finally og finalize?
  - Final gis til en variabel som ikke skal kunne endres, som const i javascript. Finally er enden på en try catch block som er det siste som skal kjøres etter blokken, og finalize er en metode blir kalt på før objektet fjernes fra minnet
- Hva er singleton klasse og hvorfor vil du bruke den?
  - En singleton klasse er en klasse som sikrer at bare en instans av klassen eksisterer i JVM. Den er nyttig når du vil ha streng kontroll over globale variabler for dataforbindelser eller konfigurasjoner
- Hva er forskjellen på overlasting og overstyring av metoder i java?
  - Overlasting er da flere metoder i samme klasse har samme navn men forskjellige parametre. Overstyring er da en underklasse gir en spesifikk implementasjon av en metode som er definert i dens overklasse
