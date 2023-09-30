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

-

# Sorterings metoder

# Garbage collection

# Design patterns

# Spørsmål
