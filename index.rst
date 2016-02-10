.. toctree::
    :maxdepth: 1
    :hidden:

    workflow
    performance_budget


WOM
===

Het doel van de WOM is het garanderen van een ondergrens aan de **kwaliteit**
van de software en gerelateerde IT diensten die Nens levert en zorgen dat die
software zo **snel** mogelijk in productie komt.

Klanten kopen geen software van Arjen of Reinout maar van Nens. Hoe zorgen we
er voor dat de **kwaliteit van de software** een **eigenschap** wordt van de
**organisatie** in plaats van van een persoon?

Uitgangspunten:

1. Gebruik **ervaring en expertise** in de organisatie.

2. Stel een **performance budget** in.


1. Gebruik ervaring en expertise
--------------------------------

Maak gebruik van de ervaring en expertise in de organisatie:

* *Elke* ontwikkelaar dient *voordat* hij of zij begint met een feature het
  ontwerp van deze feature met een (of meerdere) senior ontwikkelaar(s) door
  te spreken. Dat kan met een potloodkrabbel en vijf minuutjes sparren of via
  een RFC op github of tijdens de lunch of aan de bar, wat je maar wilt.

* Een pull request (PR) wordt gereviewed door een senior ontwikkelaar.

* We kennen :doc:`één manier van software ontwikkelen <workflow>` om
  uitwisseling van ontwikkelaars zo goedkoop mogelijk te maken.

Senior ontwikkelaars zijn: Arjan, Reinout, Jack, Sander, Carsten, Berto
(Python) en Ernst (Javascript).


2. Performance budget
---------------------

Een :doc:`performance budget <performance_budget>` als proxy voor kwaliteit:

    Aan het eind van 2016 moet *elke* HTTP request die het pand binnenkomt van
    buiten binnen **300 ms** een response opgeleverd hebben.
