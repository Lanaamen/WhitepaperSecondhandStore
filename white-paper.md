# White Paper
# Release Pipeline för Secondhand Startup

## Sammanfattning


## Företagsbeskrivning och historia
Företaget är en liten startup som säljer secondhand-prylar online. De saknar en tydlig plan för hur kod ska gå från utveckling till produktion. Releaseprocessen går ofta för snabbt och det finns för få tester, vilket gör att saker kraschar i produktion. Eftersom teamet är litet jobbar folk mest själva och kommunikationen kring releaser är dålig. Som resultat dyker buggar upp hos användarna, vilket skapar problem och stress för teamet. Problemen uppstår främst på grund av tidsbrist, brist på struktur och tydliga processer. Teamet är litet och saknar tydlig ansvarsfördelning, vilket gör att kod ofta deployas utan tillräcklig testning.

## Lösningsförslag
Företaget använder en webbapplikation byggd med JavaScript (Node.js) och en databas som MongoDB. Koden hanteras via GitHub och deployment sker via GitHub Pages.

Företaget behöver en release-pipeline som fungerar som en grind mellan utveckling och produktion. När en utvecklare pushar kod till repot startar pipelinen automatiskt. Först testas att koden kompilerar och byggs. Fungerar inte detta stoppas pipelinen direkt så att felet inte går vidare.

Efter det körs automatiska tester som kontrollerar att funktionalitet och olika delar av systemet fungerar tillsammans. Om testerna misslyckas stoppas pipelinen igen.

När de automatiska testerna är godkända sker en manuell QA, där någon i teamet testar viktiga funktioner som till exempel login och köp. Pipelinen tillåter inte deployment innan detta är godkänt.

När alla steg är klara kan koden deployas till produktion. För detta företag passar Continuous Delivery bäst, eftersom koden alltid är redo att släppas men kräver ett sista godkännande innan den går live.

Ansvarsfördelningen blir tydlig. Utvecklarna pushar kod, pipelinen hanterar tester automatiskt, och teamet ansvarar för QA och deployment. Gates i pipelinen säkerställer att inget går vidare om något steg misslyckas, vilket minskar risken för buggar i produktionen.

För att lösa problemen behöver företaget införa tydliga DevOps-processer, som CI/CD, automatiserade tester, kodgranskning och en strukturerad release-process. Detta gör att kod alltid testas innan den når produktion och att teamet kan arbeta mer effektivt och strukturerat.

## Exempel på pipeline för release-processen
1. Kod pushas till repo
   * Utvecklarna skickar ny kod till GitHub
   * Pipeline startar automatiskt
2. Bygg & kompilering
   * Koden kompileras automatiskt
   * Om bygg eller kompilering misslyckas stoppas pipeline
3. Automatiserade tester
   * Enhetstester: små funktioner testas
   * Integrationstester: t.ex. betalning och lager
   * Om tester misslyckas stoppas pipeline
4. Manuell QA
   * Teamet testar kritiska funktioner, t.ex. login och köp
   * Pipeline släpper inte vidare förrän QA är godkänd
5. Deployment till produktion
   * Om allt ovan är godkänt deployas koden 

## Verktyg & Deployment
När de gäller continuous delivery och continuous deployment passar continuous delivery bäst för detta startupföretag. Detta eftersom koden kräver ett manuellt godkännande innan den släpps till produktion, vilket gör att teamet har kontroll över när releaser sker. Continuoues deployment saknar denna extra kontroll och deployas automatiskt till produktion så fort alla tester är godkända.



Exempel på YAML-fil