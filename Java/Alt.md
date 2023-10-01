# OOP

**Innkapsling**

- Pakke inn data
- Skjule detaljer i implementasjonen fra brukeren av objektet
- Kontrollerer tilgjengeligheten av data (private, public, protected)

**Abstraksjon**

- Skjule komplekse realiteter mens vi eksponerer de nødvendige
- Interface og abstrakte metoder hjelper til med dette
- Bruker kan trykke increaseVolum() på kontrollen uten å vite hvordan metoden fikser lyden

**Polymofrisme**

- Polymorfisme betyr mange former, i OOP refererer dette til evnen et objekt har til å ta flere former
- Vanligste i java er der ett foreldre referanse brukes til å henvise ett barn objekt
- Vi kan dermed lage factory klasser eller klasser som tar inn mye forskjellige objekt, som kan kalle fellses metoder på disse

**Arv**

- Arv lar en klasse overta egenskaper og oppførsel fra en annen klasse
- Vi definerer da en ny klasse basert på en eksisterende klasse

**Interface og abstrakte klasser**

- Abstrakt klasse skal være en grunnleggende klasse for underklasser uten å måtte implementere noe
- Kan bare utvide en abstrakt klasse, men kan utvide flere interface
- Abstrakt klasse kan ha abstrakte metoder og ikke abstrakte metoder
- Interface har ikke variabler eller konstruktør, men det kan abstrakte metoder ha
- Interface spesifiserer hva en klasse skal gjrøe, men ikke hvordan
- Abstrakt klasse brukes når vi ænsker å ha en baseklasse som gir default implementering av noen metoder men også tvinger de avledede klassene å implementere noen andre

<br>

# Datastrukturer

**List**

- Liste av elementer, satt inn i rekkefølgen de settes inn i
- ArrayList: Implementasjon av tabeller
- LinkedList: Dobbel linket struktur, bedre for innsetting og sletting

**Set**

- En samling uten duplikater
- HashSet, kjapp innsetting og sletting

**Stacks and Queues**

- Stack er som en haug tallerkner, FILO
- Queue baseres ofte på FIFO
- Stack er utdatert så brukes ArrayDeque (Deque)
- Queue: LinkedList, prioritert kø: PriorityQueue

**Map**

- Nøkkel verdi par, mapper nøkkel til verdi O(1)
- Nøkler kan ikke ha lik verdi

**Trees**

- Tre struktur, en foreldre node, Binærtre har to barn, andre kan ha fler
- Binærtre: venstre er mindre en forelder og høyre er større
- TreeSet (Set), TreeMap(sorteres etter nøkkler)

# Sorterings metoder

- Insertion Sort
- Selection Sort
- Merge Sort
- Quick Sort
- Radix sort

# Garbage collection og Minne

- Brukes for å frigjøre plass til programmer som gjører så de utføres mest effektivt
- Fungerer med Mark and Sweep der programmer som ikke er markert som programmet ikke lenger kan få tak i blir fjernet
- Stack: lagres primitive datatypers variabler, funksjonskall og lokalvariabler lagres. for hver
- Lever på FIFO, Når funksjonen avsluttes fjernes den fra framen, her fjernes da funskjonen fra minnet
- Heap: Her lagres objekter
- I java fjernes minne som ikke brukes lenger av garbage collection, mens i C for eksempel må dette håndteres selv

# Design patterns

**Singleton**

- En klasse kun har en instans og gir en global metode for å få tilgang til denne instansen. Vi har da en tom konstruktør og en getInstance metode for å sjekke om instansen er null og hvis ikke lager vi en
- Factory method: Gir grensesnitt for å opprette objekter, men lar underklasser avjgjøre hilket objekt som skal instansieres
- Stategy: Definerer en familie algoritmer, kapsler dem og gjør dem utskiftbare. Strategien lar algoritmen variere uavhengig av klienter som bruker den
- Observer: Lar ett objekt subjekt varsle andre objekter kalt observers om endringer i sin tilstand
- Decorator:

# Spørsmål

**Hva er overlasting og overstyring i java**

- Overlasting er å ha flere metoder med samme navn, men forskjellige antall eller forskjellige parametere
- Overstyring er da vi bruker @Override til å overskrive andre metoder som toString for eks.

**Hva er forskjellen på equals og ==**

- == sjekker om to referanser peker på samme objekt i minnet, men på primitive typer som int og char sammenlikner vi faktisk verdiene
- Equals brukes for å sjekke innholdsmessig likeverdighet
