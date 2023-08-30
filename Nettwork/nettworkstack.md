# Nettwork layers

Applikasjons nivå
	- Dette nivået. Bestemmer hvilken protokoll som skal brukes til å overføre dataene. Dette kan være HTTP for overføring av websider eller SMTP for sending av epost
	- Her får man data fra bruker før den skal pakkes inn og sendes videre. I en HTTP spørring vil den pakkes inn med headere som brukeragent, aksepterte innholdstyper og andre relevante metadata
	- Så sendes data videre til transport nivået
	- Her blir også data marshalled
		○ Dette vil si at dataen blir konvertert til en datastrøm
		○ Dette er nødvendig for at forskjellige systemer skal kunne forstå og behandle dataene som utvekselet mellom dem


Encapsulering
	- Skjer i alle lagene nedenfor her bortsett fra link nivået
	- Her blir data pakket fra ett høyere lag og sendt videre


Transport nivå
	- Her tas data imot fra applikasjonsnivået som er pakket inn i forhold til protokollen, eks HTTP eller SMTP.
	- Her skjer multipleksing
		○ Det er prosessen ved å ta flere datastrømmer og pakke de inn i en stor felles datastrøm
		○ Når dataen skal pakkes ut brukes portnummer til å skille på datastømmene
	- Er dataen for stor for å sendes i en pakke, vil dataen bli delt i flere segmenter som kan sendes individuelt.
	- Her pakkes dataen videre inn med portnummer for avsender og mottaker, sekvensnummer og feilkontrollinformasjon. I TCP inneholder headeren også informasjon om vindusstørrelse og andre mekanismer for flow control og feilkontroll
	- Transport nivået velger så TCP eller UDP avhengig av behov
	- Hvis TCP b lir valgt må en kobling etableres av en threeway handshake for å synkronisere sekvensnummer og bekrefte at begge er klare for å motta data
	- Segmentene blir pakket inn med transport headere (TCP eller UDP format) og sendes videre til nettverksnivået
	- Her er også jobben å gjøre en upålitelig kanal med tap, korrupsjon, overtagelse og duplisering til en pålitelig kanal, gjennom å designe ulike protokoller
		○ RDT 1.0 - nettverks om er pålitelig, trengs ikke noen sikkerhetsrammer
		○ RDT  2.0 - nettverk med transmisjons feil. Her har vi checksum for å se transmisjonsfeil, sammen med positive og negative acknowledgements
		○ RDT 3.0 - Nettverk tap av segmenter. Her har vi timere / timeouts og retransmisjon for da pakkene blir borte. Og vi har også segmentnummer for å kunne se om en pakke blir borte som skulle ha kommet mellom to andre pakker.
		○ RDT 4.0 - Nettverk med overtakelse av segmenter. Større sekvensnummer
		
		
	
Nettverks nivå
	- Dette nivået er ansvarlig for å rute og levere pakker mellom avsender og mottaker. IP er hoved protokollen her. 
	- Segmentet fra transport nivået blir mottatt, disse inneholder transport headere (TCP og UDP) og data fra applikasjonsnivået
	- Her blir segmentene pakket inn i IP datagram som har IP headere som versjonen IPv4 eller 6, total lengde, checksum, kilde og mål IP adresse hvilken type protokoll osv.
	- Nettverksnivået bestemmer ruting og sendingen av pakkene, her må pakker sendes til riktige rutere og nettverksenheter basert på IP adresser. 
	- OSPF brukes for å finne korteste veier i nettverket og er en routing funksjon som enheter i nettverket som rutere bruker for å finne de korteste veiene i nettverket og bruker denne informasjonen til å lage ett routing table, spesielt i rutere. Som inneholder en tabell for neste hopp for datapakkene basert på IP adressene deres.
	- Her brukes link state med djikstra eller vector med bellman ford

Link nivå
	- Link nivået er ansvarlig for å pakke inn data i rammer og håndtere informasjonen mellom direkte tilkoblede noder i nettverket
	- Mottar IP datagram fra nettverk nivået
	- Her blir det lagt til link headere og trailere. Kilde MAC adresse, Mål MAC adresse, ethertype og frame check sequence
	- Når nye headere er lagt til pakkes datagrammet inn i en ramme
	- Linknivået kan også være ansvarlig for flow control og feilkontroll, feil for å snappe opp feil i sending og flow control for å ikke sende for mye data så det blir buffer overflow hos mottaker
	- Så sendes rammen til fysisk nivået
	- Her har vi DHCP som automatisk konfigurerer IP adresser til en host som kobles til nettverket
	- ARP protokollen er også her, som er en spørring med IP adresser som vil få ett svar med IP adressen og MAC adressen til den som blir spørt etter.

Fysisk nivå
	- Her skal dataen overføres via det fysiske medium, kabel, fiber eller trådløst
	- Tar imot rammer fra link nivå
	- Her overføres rammene til signaler som kan overføres fysisk
	- Så sendes dataen over fysiske medium
	- Dette laget håndterer også synkronisering og timing
	- Så vil mottaker få data og gå motsatt vei gjennom nettverks stacken.


