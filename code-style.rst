Code stijl
==========


Python standaardregels
-----------------------

We schrijven af en toe open source software en werken veel met open source
software, dus het is goed ongeveer dezelfde stijl aan te houden als de rest
van de python/django wereld.

Nummer 1 is natuurlijk `pep 8
<https://www.python.org/dev/peps/pep-0008/>`_. Het merendeel van onze code
voldoet daar prima aan. En anders is het met de "pep8" tool snel genoeg
gefixt (noot: recent is het project hernoemd in "pycodestyle", dus het kan
zijn dat je die term tegenkomt).

De `Django coding style
<https://docs.djangoproject.com/en/1.10/internals/contributing/writing-code/coding-style/>`_
is ook goed om door te lezen. Zaken zoals `gebruik_underscores()` in plaats
van `gebruikCamelCase()` worden daar nog wat aangescherpt.

Wel is wat in de django coding syle staat niet wat we bij N&S normaliter
gebruiken. Nu is dit ook een punt waarop vaak discussie is, dus dat wordt een
part puntje verderop in dit document.

Voor docstrings is er de `pep 257
<https://www.python.org/dev/peps/pep-0257/>`_. Daar houden we ons aan, met
aantekening dat inmiddels de google conventies voor het omschrijven van de
argumenten, de return waarden en van de excepties ingeburgerd aan het raken
is. Zie de `napoleon extensie van Sphinx
<http://www.sphinx-doc.org/en/stable/ext/napoleon.html#module-sphinx.ext.napoleon>`_
De `google omschrijving
<http://google.github.io/styleguide/pyguide.html?showone=Comments#Comments>`_
toont de syntax qua "args, returns, raises". Hou je echter wel aan de pep 257
regel dat de eerste regel een commando moet zijn. Dus niet "fetches" maar
"fetch".

TODO: voor libraries die door meerdere mensen gebruikt worden, zouden we
daarvoor sphinx documentatie moeten gaan eisen? Lizard-security had het
bijvoorbeeld en was handig om het te verduidelijken. Voor
lizard-auth-server/client ben ik ermee bezig. Maar hoevelen gaan het lezen?


Javascript + css standaardregels
--------------------------------

TODO, input vragen.


Imports sorteren
----------------

TODO: discussie.

In ieder geval alfabetisch sorteren. Maar willen we dan de driedeling (uit
pep8) in python/library/ditproject houden? Plone doet nu makkelijk "alles
sorteren", da's ook wel overzichtelijk.

Voor greppen wil ik wel elke import op een regel (en wel volledig) hebben. Dus
geen gedoe met haakjes, want dan faalt grep daarop.

=> beetje eens worden en dan een ``isort.cfg`` in elk project en de "isort"
tool installeren.


Tools
-----

Editorconfig is een TODO puntje. Dat is een goede om alles explicit te maken
en er is ook bij veel editors support voor. Vooral ook handig voor js/css. De
python default is vaak wel goed in editors.

pep8/pyflakes: tegenwoordig wordt eigenlijk standaard de combinatie-tool
"flake8" gebruikt. Dat zouden we ook moeten gaan doen.

isort is goed om de imports OK en netjes geordend te krijgen.

TODO: kijken naar https://pypi.python.org/pypi/plone.recipe.codeanalysis
