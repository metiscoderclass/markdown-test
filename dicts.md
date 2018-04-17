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

~~~python
fruitmand = { "appel":3, "banaan":5, "kers":50 }
~~~

Om een waarde te vinden die hoort bij een specifieke sleutel, gebruik je dezelfde syntax als voor een list, behalve dat waar je bij een list de index schrijft, je bij een dictionary de gezochte key schrijft.

In het voorbeeld zoeken we het getal op dat hoort bij de sleutel "banaan".

<iframe src="https://trinket.io/embed/python3/d3e8024d76" width="100%" height="130" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>

~~~python
fruitmand = { "appel":3, "banaan":5, "kers":50 }
print( fruitmand["banaan"] )
~~~

Je kunt via een for loop een dictionary doorlopen. De variabele in de for loop krijgt de waardes van de keys. (Als je nog niet weet hoe `format()` werkt lees dan eerst dat hoofdstuk).

<iframe src="https://trinket.io/embed/python3/169223450f" width="100%" height="130" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>

~~~python
fruitmand = { "appel":3, "banaan":5, "kers":50 }
for key in fruitmand:
print( "{}:{}".format( key, fruitmand[key] ))
~~~

Als je een dictionary element probeert te benaderen met een key die niet voorkomt in de dictionary, krijg je een runtime error (een foutmelding). Maar als je een nieuw element wilt toevoegen, kun je dat eenvoudigweg doen door een waarde toe te kennen aan een dictionary element met de nieuwe key. Bijvoorbeeld, om een "mango" toe te voegen aan de fruitmand, doe je het volgende:

<iframe frameborder="0" width="100%" height="200px" src="https://repl.it/student_embed/assignment/917042/2eadc6ce904170122f5b0259bdeab762"></iframe>

~~~python
fruitmand = { "appel":3, "banaan":5, "kers":50 }
print( fruitmand )
fruitmand["mango"] = 1
print( fruitmand )
~~~

Op dezelfde wijze kun je een bestaand dictionary element overschrijven.

Om een element te verwijderen uit een dictionary, gebruik je het gereserveerde woord `del`, net zoals je het gebruikt met lists.
~~~python
fruitmand = { "appel":3, "banaan":5, "kers":50 }
print( fruitmand )
del fruitmand["banaan"]
print( fruitmand )
~~~

Snap je overigens in welke volgorde de dictionary de elementen aanbiedt als je de inhoud van de dictionary print? Denk er even over na.

Het antwoord is: de volgorde is willekeurig. Ik zei dat bij het begin van het hoofdstuk: dictionaries zijn ongeordend. Ik kan je niet eens zeggen wat voor volgorde je op je scherm ziet als een de code hierboven uitvoert, want de volgorde kan verschillen tussen computers, besturingssystemen, en versies van Python. Er is een zekere structuur in de ordening, maar niet een die je zou kunnen (of willen) voorspellen. Door voldoende nieuwe elementen toe te voegen, kan de volgorde zelfs plotseling drastisch wijzigen.

Omdat dictionaries ongeordend (dus zonder vaste volgorde) zijn, zijn vele concepten die gelden voor lists, niet van toepassing op dictionaries. Bijvoorbeeld, je kunt geen “subdictionary” maken door een key-bereik te definiëren, je kunt kunt een dictionary niet “sorteren” of “inverteren.” Dictionaries zijn daarom wat beperkt, maar ze kunnen nuttig zijn.

## Dictionaries zijn veranderbaar (mutable)

Een dictionary is veranderbaar (mutable). Het werkt dus net even anders dan je gewend bent als met bijvoorbeeld getallen. Bekijk het volgende stukje code.

~~~python
getal1 = 5
getal2 = getal1
getal1 = 7
print(getal1)
print(getal2)
~~~

Je ziet dat `getal2` nog steeds gelijk is aan `5`. Dat terwijl je `getal1` hebt gewijzigd. Dit komt omdat `getal2` een kopie van de waarde van `getal1` krijgt. Dus als het ware een "nieuwe" waarde 5.

Bij dictionaries werkt dat niet zo. Als je daar de dictionary toekent aan een nieuwe variabele, dan verwijst die variabele naar ~dezelfde~ dictionary.

~~~python
kleuren_auto = {"rood": 6, "blauw": 4}
kleuren_auto2 = kleuren_auto
kleuren_auto["rood"] = 3
print("{}: {}".format("rood", kleuren_auto["rood"]))
print("{}: {}".format("rood", kleuren_auto2["rood"]))
~~~

Je ziet dat zowel `kleuren_auto` als `kleuren_auto2` dezelfde waarde hebben voor de kleur `"rood"`. Je hebt een alias (een andere naam) voor hetzelfde ding.

Als je echt een kopie wilt gebruiken heb je een functie nodig. In het volgende stuk worden deze uitgelegd.

Als je dit nog niet eerder hebt gezien, met lijsten werkt het hetzelfde:

~~~python
kleuren = ["rood", "geel"]
kleuren2 = kleuren
kleuren2.append("groen")
print(kleuren)
print(kleuren2)
~~~

## Dictionary methodes

Hieronder staan de dictionary methodes die het meest gebruikt worden.

### `copy()`

Net als met lists, kun je een variabele die een dictionary bevat via de assignment operator aan een andere variabele koppelen, en daarmee maak je dan een alias voor de dictionary. Dictionaries hebben een methode `copy()` die een kopie van de dictionary
maakt en retourneert.

~~~python
fruitmand = { "appel":3, "banaan":5, "kers":50 }
fruitmandalias = fruitmand
fruitmandcopy = fruitmand.copy()
fruitmand["appel"] = 2
print(fruitmand["appel"]))
print(fruitmandalias["appel"]))
print(fruitmandcopy["appel"]))
~~~

Let wel op dat dit een ondiepe kopie is (shallow copy). Dat betekent dat het goed gaat als je dict dingen als strings, integers en floats bevat. Maar als je bijvoorbeeld lijsten erin gaat zetten moet je een diepe kopie maken. Dat valt buiten de scope van dit boek.

### `keys()`, `values()`, `items()`

Je wilt natuurlijk ook met een for-loop elementen uit je dictionary kunnen bekijken. Dit kan! Als je `keys()` gebruikt zal je for-loop door alle sleutels lopen, met `values()` door alle waarden en met `items()` kun je door sleutel en waarden tegelijk lopen. Je krijgt dan steeds een koppel van sleutel en waarde. Dit heet ook wel een 2-tuple.

~~~python
fruitmand = { "appel":3, "banaan":5, "kers":50 }

print("sleutels")
for fruit in fruitmand.keys():
  print(fruit)

print("waarden")
for aantal in fruitmand.values():
  print(aantal)

print("2-tuples")
for fruit, aantal in fruitmant.items():
  print("{}: {}".format(fruit, aantal))
~~~

## `get()`

De `get()` methode kun je gebruiken om een waarde uit de dictionary te halen zelfs als je niet weet of de key die je zoekt wel in de dictionary zit. Je roept de `get()` methode aan met de key die je zoekt als argument, en het geeft de corresponderende waarde terug als de key bestaat, of de speciale waarde `None` als de key niet bestaat in de dictionary. Als je in plaats van `None` een andere waarde terug wilt krijgen als de key niet bestaat, dan kun je die waarde meegeven als het tweede, optionele argument (je mag het tweede argument dus ook weglaten).

~~~python
fruitmand = {"appel":3,"banaan":5,"kers":50,"druif":0,"mango":2}
appel = fruitmand.get( "appel" )
if appel:
  print( "appel is in de mand" )
else:
  print( "geen appels in de mand")

aardbei = fruitmand.get( "aardbei" )
if aardbei:
  print( "aardbei is in de mand" )
else:
  print( "geen aardbei in de mand")

banaan = fruitmand.get( "banaan", 0 )
print( "aantal bananen in de mand:", banaan )

aardbei = fruitmand.get( "aardbei", 0 )
print( "aantal aarbeien in de mand:", aardbei )
~~~

Voer de code hierboven uit en bestudeer de uitkomst, omdat wat de code demonstreert over de `get()` methode erg nuttig is. Stel je voor dat een collectie van items hebt met corresponderende hoeveelheden, bijvoorbeeld, de inhoud van een fruitmand waarbij de keys de namen van fruit zijn, en de waardes de hoeveelheden. Als je in de fruitmand dictionary zoekt met de `get()` methode en als tweede argument een nul, kun je naar een willekeurig stuk fruit zoeken in de mand zonder dat je eerst moet controleren of het bestaat in de mand, want als je naar een fruitnaam vraagt die er niet als key in voorkomt, krijg je nul terug, en dat is precies wat je wilt zien.


## Oefening
~~~python
~~~

## Keys
Zoals ik aangaf kan ieder onveranderbaar data type een dictionary key zijn. Dat betekent dat je strings, integers, en floats kunt gebruiken als keys. Je herinnert je wellicht dat tuples ook onveranderbaar zijn, wat betekent dat ook tuples als keys gebruikt kunnen worden.
Dat is soms nuttig.

Je kunt dus bijvoorbeeld een dictionary maken als volgt:
~~~python
punten_tellen = {(1, 2): 4, (3, 4):3}
~~~
Dus bij het tuple `(1, 2)` hoort dus de waarde `4`.

Een eenvoudig voorbeeld van het nut van tuples als keys is een dictionary waarbij je informatie wilt opslaan die geassocieerd is met punten in een 2-dimensionale ruimte. Er is geen goede manier waarmee je een 2-dimensionaal punt kunt opslaan als een enkel getal of string. Het is niet onmogelijk (je kunt bijvoorbeeld het
getallenpaar omzetten naar hun string-representatie en ze met een komma ertussen tot één string maken) maar het wordt al snel verwarrend (bijvoorbeeld, de strings "2,3", "2, 3", "+2,+3", en "02,03" zouden alle dezelfde tuple voorstellen, terwijl het verschillende keys zijn).

## Opslaan van complexe waardes

Tot op dit moment heb ik alleen gesproken over het opslaan bij een key in een dictionary van een enkele waarde van een enkel data type. Het is echter ook mogelijk om complexe waardes op te slaan in een dictionary. De waardes kunnen willekeurige Python objecten zijn. Bijvoorbeeld, je kunt bij iedere key een list opslaan. Hieronder staat een dictionary waarbij ik leerlingen opsla die badges behaalt hebben. De persoon cursus wordt geïdentificeerd door de naam. De badges worden geïdentificeerd door hun badgenummer.


~~~python
badges = {
  'Jochem' :[ '123456' , '383213' , '234178' ],
  'Iris' :[ '123456 ' , '223416' , '234178' ],
}

for persoon in badges:
  print(persoon)
  for badge in badges[persoon]:
    print(badge, end=" ")
  print()
~~~

## Snelheid

Lists en dictionaries zijn de twee meest-gebruikte data structuren in Python. Het is vaak duidelijk welk van de twee je moet gebruiken bij een probleem, maar het kan nuttig zijn om iets te weten over hoe Python deze data structuren verwerkt voor het geval je een keus hebt.

Stel je voor dat je een groot aantal getallen uit een bestand moet lezen. De getallen zijn allemaal verschillend en kunnen willekeurig groot zijn. Je moet later getallen van een andere lijst vergelijken met de getallen die je uit het bestand hebt gelezen.

Moet je een list of een dictionary gebruiken om de getallen die je inleest op te slaan? Omdat het alleen maar getallen zijn en geen extra data, lijkt een list de beste optie. Er is echter een probleem dat optreedt als je hier een list gebruikt. Bekijk de volgende code, die een list creëert met 10000 getallen, en daarna bekijkt of 10000 andere getallen in de list voorkomen (wat geldt voor geen van de getallen).

~~~python
from datetime import datetime

numlist = []
for i in range( 10000 ):
  numlist.append( i )

start = datetime.now()
teller = 0
for i in range( 10000 , 20000 ):
  if i in numlist:
    teller += 1
eind = datetime.now()

print( "{}.{} seconden om {} nummers te vinden".format(
(eind -start).seconds , (eind -start).microseconds , teller ) )
~~~

Hier is code die hetzelfde doet, maar de getallen inleest in een dictionary, waarbij simpelweg voor ieder ingelezen getal een waarde van 1 in de dictionary wordt opslagen.

~~~python
from datetime import datetime

numdict = {}
for i in range( 10000 ):
  numdict[i] = 1
s
tart = datetime.now()
teller = 0
for i in range( 10000 , 20000 ):
  if i in numdict:
    teller += 1
eind = datetime.now()

print( "{}.{} seconden om {} nummers te vinden".format(
(eind -start).seconds , (eind -start).microseconds , teller ) )
~~~

Als je deze code uitvoert, zul je zien dat voor de dictionary het antwoord vrijwel onmiddellijk volgt, maar dat het voor een list wat langer duurt. De reden is dat ik met behulp van de in operator controleer of een getal voorkomt in de list of de dictionary. Voor een list betekent dat dat Python de hele list sequentieel (van begin tot einde, één voor één) doorzoekt, totdat het het getal vindt of het einde van de list bereikt wordt. Dit houdt in dat Python 10000 keer 10000 getallen controleert (omdat het geen enkel getal kan vinden), ofwel 100 miljoen getallen.

Voor een dictionary is het zoeken van een key veel sneller. Python kan erg snel vaststellen of een key wel of niet in een dictionary zit. Meestal is het controleren van een handjevol getallen genoeg. Daarom is de dictionary code veel, veel sneller.

Python slaat de keys voor een dictionary op in een zogeheten “hash tabel.” Ik leg de details daarvan niet uit, maar weet dat dit het mogelijk maakt om keys heel snel op te zoeken, ten koste van wat geheugengebruik (dus dictionaties gebruiken wel meer geheugen dan lijsten).

Je denkt misschien dat een paar seconden zoektijd voor de list nog steeds erg weinig is, maar de zoektijd neemt kwadratisch toe met de hoeveelheid data. Afhankelijk van het soort en de omvang van het probleem, kan een dictionary zeer te prefereren zijn boven een list.

Lists nemen wel minder geheugen in beslag dan dictionaries, en als je een list direct kunt benaderen via een index, kunnen lists zeker sneller zijn dan dictionaries. Bijvoorbeeld, in bovenstaande probleem, als ik zou weten dat de list gesorteerd is dan kan ik getallen op een veel slimmere manier vinden dan via de in operator (ongeveer 14 getallen controleren volstaat) – in dat geval is het gebruik van een list misschien sneller dan het gebruik van
een dictionary.

Onthoud hiervan dat een list snel is als je de elementen via hun index kunt benaderen, terwijl een dictionary een betere keuze is als de enige manier om iets te zoeken is de elementen te scannen. De in operator lijkt gemakkelijk en is leesbaar, maar als je hem gebruikt om iets te zoeken in een lange list, dan ben je verkeerd bezig

## Samenvatting gebruik dictionary

~~~python
#  Nieuwe dict maken
fruitmand = {}  # Lege fruitmand
fruitmand = { "appel": 3, "peer": 5}

# Toevoegen / veranderen
fruitmand["appel"] = 4
fruitmand["banaan"] = 4

# Verwijderen
del fruitmand["appel"]

# Kopieëren (als de lijst eenvoudige datatypen bevat)
fruitmand_nw = fruitmand.copy()

# Door een dict loopen
fruitmand.keys() # Alle sleutels uit de dict
fruitmand.values() # Alle waarden uit de dict
fruitmand.items() # Alle 2-tuples uit de dict

# get()
fruitmand.get("appel", 0) # een waarde vinden of een alternatief



~~~
