# Dictionaries

Strings en lists zijn geordende data structuren, wat inhoudt dat je precies op een plek kunt vinden wat daar staat (`woord[1]` geeft het tweede karakter uit `woord`, `kleuren[5]` geeft de 6e kleur in de lijst met kleuren). Maar niet alle dataverzamelingen hebben een natuurlijke manier van numeriek geordend zijn, en deze kunnen dus niet (gemakkelijk) geïndiceerd worden.
Python biedt “dictionaries” als een manier om ongeordende data te structureren.

## Dictionary basis

Een “dictionary” (letterlijk: “woordenboek,” maar die vergelijking loopt spaak in Python) is een ongeordende data structuur die een verzameling elementen bevat. Om een element te vinden, moet je de “key” (“sleutel”) van het element kennen.

In de grond is een dictionary een verzameling van “keys” met geassocieerde waardes. Dit heet ook wel key-value pairs.
Ieder onveranderbaar data type mag gebruikt worden als key. Een veelgebruikt data type dat als key wordt ingezet is de `string`. Om een `string` te wijzigen in Python moet je altijd een nieuwe string maken.

Dictionaries creëer middels accolades `{}`, vergelijkbaar met hoe je lists creëert met vierkante haken (`[]`). Een lege dictionary maak je door een assignment (toekenning) aan een variabele te doen met `{}`. Je kunt een dictionary met inhoud creëren door ieder element dat je erin wilt hebben tussen de accolades te zetten, met als syntax `<key>:<value>`, en komma’s tussen de elementen.

Hieronder bouw ik een dictionary fruitmand, met drie elementen, namelijk de key "appel" met waarde 3, de key "banaan" met waarde 5, en de key "kers" met waarde 50.

<iframe src="https://trinket.io/embed/python/08a7182023" width="100%" height="100" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>

~~~python
fruitmand =
~~~
