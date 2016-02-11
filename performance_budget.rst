Performance budget
==================

Een manier om devops cultuur, systeemdenken en kwaliteit bedrijfsbreed te
stimuleren is een zogenaamd ‘performance budget’. Je legt jezelf een
gelimiteerd budget op mbt performance en neemt dat als uitgangspunt om
bottlenecks in je hele systeem te vinden en zo stapje voor stapje structureel
beter te worden.

Het heeft namelijk niet zo veel zin om het snelste frontend framework te
hebben als de queries in je backend 4 minuten duren. Een gebruiker klikt
ergens, wacht 4 minuten voordat de data er is die vervolgens in 3 ms wordt
gerenderd. De gebruiker zal niet onder de indruk zijn van die 3 ms aangezien
hij waarschijnlijk al na 3 seconden is weggeklikt.

Ons doel is dat eind 2016 geen enkel http request van buiten langer dan 300 ms
binnen blijft. Daar volgen dan bijvoorbeeld de volgende eisen uit:

* Om te weten hoe lang iedere request duurt moeten we die requests ten eerste
  loggen.

* Vervolgens moeten we alle requests die langer dan 300 ms duren in kaart
  brengen.

* Daarna moet je binnen twee stappen de bottleneck in kaart kunnen hebben.

* De eigenaar van de bottleneck onderzoekt de bronoorzaak van de traagheid en
  stelt een structurele fix voor.

* De fix wordt uitgerold.

* Rinse and repeat.

Concreet voorbeeld:

* Een monitoring / rapportage systeem meldt dat een request 3 minuten duurt.

* Ops klikt op het request en ziet dat het naar de lizard stack gaat.

* Ops klikt op de lizard stack en ziet dat er voor deze request een database
  query van 2:59 minuten was.

* De dba onderzoekt de query en ontdekt dat er geen gebruik wordt gemaakt van
  een index; hij overlegt met een developer en ze besluiten een index aan te
  maken, schrijven een test voor de fix en maken een PR aan voor de fix.

* De fix wordt gereviewed en uitgerold, afhankelijk van de ernst direct naar
  productie of eerst via staging.

In de praktijk zou het kunnen zijn dat er te veel requests zijn die langer dan
300 ms duren. In dat geval verhoog je de drempel voor het eerste half jaar
naar 1 seconde, 2 seconden of 30 seconden.

Als er requests zijn waar geen praktische fix voor is om ze sneller te maken
en ze geen negatieve invloed hebben op kritische bedrijfsprocessen kunnen
zulke requests ge-whitelist worden.

Het mooie van performance als driver te gebruiken is dat stabiliteit en
schaalbaarheid voorwaarden zijn voor performance. Je wordt dus gedwongen die
eerst op te lossen om vervolgens na te gaan denken over performance. Het is
ook een goede driver voor logging, monitoring en testing, kortom voor
kwaliteit.

na 3, 6, 9 en 12 maanden evalueren en bijsturen.


TODO
----

* Alle projecten moeten response tijd van elke request gaan loggen naar
  logstash (bijvoorbeeld met Dogslow).

* Wekelijkse rapportage in Kibana van slow requests.

* Follow up op basis van rapportage.


Bronnen
-------

* http://blog.dareboost.com/en/2015/10/performance-budget/

* Meer over waarom performance belangrijk is:
  http://www.smashingmagazine.com/2015/11/why-performance-matters-part-2-perception-management/
