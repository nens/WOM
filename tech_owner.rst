Tech owner
==========

Bij nens is veel vrijheid om met nieuwe technologieen te experimenteren en die in productie te nemen. Dat maakt ons flexibel maar ook kwetsbaar als we niet de verantwoordelijkheid oppakken die bij die vrijheid hoort.

Meestel begint het experimenteren met nieuwe technologie op basis van interesse of skills van 1 persoon. Maar zo gauw die technologie rijp is voor productie is het van belang de kennis van de technologie in de organisatie te borgen.

Om dat te doen moet degene die de technologie in productie wil nemen er voor zorgen dat hij een mede tech owner vindt. Tech owners zijn verantwoordelijk voor de adaptatie en inbedding van de technologie in het bedrijf.

Het is niet de bedoeling dat *iedere* library of dependency een tech owner moet krijgen. Er is een verschil tussen het gebruik van een Javascript helper library als lodash of moment en het virtualiseren van een datacentrum met Mesos.

**TODO:** verantwoordelijkheden tech owner uitschrijven.


Common tech
-----------

Technologie die iedereen verondersteld wordt te beheersen, hiervoor zijn geen tech owners:

    pip, git, buildout, django, postgresql, sphinx, ubuntu, vagrant + lxc, ...


Shared tech
-----------

Technologie die door een substantieel deel van ontwikkelaars wordt gedeeld en niet als risico wordt gezien:

    Redis, Django Rest Framework, PostGIS, Celery + Flower, Factory Boy, Numpy, Pandas, CSS, supervisor, gunicorn, nginx, TileStache, nose, Bootstrap, ...

**TODO:** misschien is het toch verstandigheid om aan enkele van deze techs wat namen te hangen?


Critical business tech
----------------------

Technologie die primaire business processen ondersteunt en dus kritiek is voor het bedrijf, hier zijn tech owners zeer belangrijk. Uiteindelijk is het doel om deze tech te 'promoveren' tot `shared tech`_.

**VMWare** 1. Daniel 2. Nils


**Angular** 1. Ernst 2. Fritz


**D3js** 1. Ernst 2. Fritz 3. Arjen


**React** 1. Gijs 2. ?


**Flask** 1. Arjan 2. Gijs


**Webpack** 1. Gijs 2. ?


**Grunt & Bower** 1. Fritz 2. Ernst


**Raster-store** 1. Arjan 2. ?


**Raster-server** 1. Arjan 2. ?


**Ansible** 1. Sander 2. Arjen


**HBASE** 1. Berto 2. Carsten


**Spark (Scala)** 1. Berto 2. ?


**Cloudera distro** 1. Berto 2. ?


**Mesos & Marathon** 1. Sander 2. ?


**Logstash & Kibana** 1. Sander 2. ?


**Docker** 1. Sander 2. ?


**TODO:**

* kandidatenlijst opstellen voor mensen die geinteresseerd zijn tech owner te worden van 1 van bovenstaanden (kan ook als nr 3 of 4 zijn).


Other tech
----------

**ArcGIS / QGIS** 1. ? 2. ?
