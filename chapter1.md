# Dictionaries

Strings en lists zijn geordende data structuren, wat inhoudt dat je precies op een plek kunt vinden wat daar staat (`woord[1]` geeft het tweede karakter uit `woord`, `kleuren[5]` geeft de 6e kleur in de lijst met kleuren). Maar niet alle dataverzamelingen hebben een natuurlijke manier van numeriek geordend zijn, en deze kunnen dus niet (gemakkelijk) geïndiceerd worden.
Python biedt “dictionaries” als een manier om ongeordende data te structureren.

## Dictionary basis

Een “dictionary” (letterlijk: “woordenboek,” maar die vergelijking loopt spaak in Python) is een ongeordende data structuur die een verzameling elementen bevat. Om een element te vinden, moet je de “key” (“sleutel”) van het element kennen.

In de grond is een dictionary een verzameling van “keys” met geassocieerde waardes. Dit heet ook wel key-value pairs.
Ieder onveranderbaar data type mag gebruikt worden als key. Een veelgebruikt data type dat als key wordt ingezet is de `string`. Om een `string` te wijzigen in Python moet je altijd een nieuwe string maken.

Dictionaries creëer middels accolades `{}`, vergelijkbaar met hoe je lists creëert met vierkante haken (`[]`). Een lege dictionary maak je door een assignment (toekenning) aan een variabele te doen met `{}`. Je kunt een dictionary met inhoud creëren door ieder element dat je erin wilt hebben tussen de accolades te zetten, met als syntax `<key>:<value>`, en komma’s tussen de elementen.

Hieronder bouw ik een dictionary fruitmand, met drie elementen, namelijk de key "appel" met waarde 3, de key "banaan" met waarde 5, en de key "kers" met waarde 50.

<iframe src="https://trinket.io/embed/python/08a7182023" width="100%" height="130" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>

~~~python3  
fruitmand = { "appel":3, "banaan":5, "kers":50 }
~~~

Om een waarde te vinden die hoort bij een specifieke sleutel, gebruik je dezelfde syntax als voor een list, behalve dat waar je bij een list de index schrijft, je bij een dictionary de gezochte key schrijft.

In het voorbeeld zoeken we het getal op dat hoort bij de sleutel "banaan".

<iframe src="https://trinket.io/embed/python3/d3e8024d76" width="100%" height="130" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>

Je kunt via een for loop een dictionary doorlopen. De variabele in de for loop krijgt de waardes van de keys. (Als je nog niet weet hoe `format()` werkt lees dan eerst dat hoofdstuk).

<iframe src="https://trinket.io/embed/python3/169223450f" width="100%" height="130" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>

~~~python
fruitmand =
~~~
