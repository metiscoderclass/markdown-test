# Bestanden lezen en schrijven

Bestanden lezen en schrijven kun je natuurlijk ook doen met Python!

We leggen hier uit:
* hoe je een bestand kunt inlezen in een lijst,
* hoe je een lijst kunt wegschrijven in een bestand,
* hoe je data achteraan het bestand kunt toevoegen

We doen dit door karakters in te lezen en weg te schrijven (strings). Je kunt ook per bit bestanden benaderen (binair) maar dat valt buiten de scope van dit hoofdstuk. Ook kun je willekeurige plekken in je bestand zoeken en daar stukjes lezen maar dat laten we ook buiten wegen.

## Wat is een file in Python?

Een file (bestand) is een object in Python net als het Turtle object. Je kunt functies aanroepen als `read()`, `readline()`, `write()` en nog meer. De leesfuncties geven je een stukje van het bestand terug als een string of als een lijst. Belangrijk is dat hier de line-endings ("enters" aan het einde van de regel) ook bij zitten. Dus die moeten we eruit halen.

In Python wordt het regeleindekarakter altijd weergegeven door `\n`. Op Windows en Linux zijn de 'echte' regeleindekarakter verschillend, maar Python zorgt ervoor dat je je daar geen zorgen over hoeft te maken. Als je binaire data gaat gebruiken moet je hier wel mee oppassen.

## Een bestand inlezen
Een bestand inlezen kan op een aantal manieren waar we er hier een paar van gaan bespreken. Er zijn nog meer manieren maar met deze twee kom je al een heel eind.

### Het hele bestand in één keer lezen en splitsen
Bekijk het volgende stuk code:

~~~python
with open('bestandsnaam') as f:
  bestandsdata = f.read()
~~~

In dat stuk code wordt het *hele* bestand ingelezen in één grote string `bestandsdata`. Dus als we de string uitprinten dan zie je het hele bestand op je scherm verschijnen (inclusief regeleinden).

~~~python
with open('bestandsnaam') as f:
  bestandsdata = f.read()

print(bestandsdata)
~~~

Wil je alle regels apart in een lijst hebben kun je de string opknippen met behulp van `split()`.

~~~python
# split() zonder argumenten maakt een lijst van alle 'woorden', zonder de spaties.
woorden = "Dit is een lange string.".split()
print(woorden)
~~~

Wil je dus op het regeleindekarakter (`\n`) splitsen dan gebruikt je:

~~~python
with open('bestandsnaam') as f:
  bestandsdata = f.read().split("\n")

print(bestandsdata)
~~~

Als je een bestand gaat inlezen moet je dus goed weten wat de structuur is die je er in aanbrengt. Een voorbeeld van een bestand kan als volgt zijn:

~~~
auto=car
couch=bank
fiets=bicycle
~~~

Hier wil je dus

* Eerst het bestand inlezen
* Splitsen op regeleinde
* Daarna splitsen op het karakter `=`

Code kan er dan uit zien als:
~~~python
with open('testbestand') as f:
  bestandsdata = f.read().split('\n')

for item in bestandsdata:
    if not item == '': # Sla lege regels over
        # Hieronder zie je hoe je de inhoud van een lijst met twee elementen aan twee variabelen kunt toekennen
        woord1, woord2 = item.split("=")
~~~

### Het bestand regel voor regel inlezen
Je kunt ook het bestand regel voor regel inlezen. Daarbij is het wel belangrijk dat je het bestand opent (met `open()`) maar ook goed afsluit (met `close()`). Je kunt voor het regel voor regel inlezen de `in`-operator voor gebruiken. Je kunt dat het einderegelkarakter eraf halen met de methode `strip('\n')` en daarna weer de string die je krijgt splitsen.

Ik ga weer uit van het volgende bestand:

~~~
auto=car
couch=bank
fiets=bicycle
~~~

~~~python
f = open('testbestand')

for line in f:
  woord1, woord2 = line.strip('\n').split('=')
  print("." + woord1 + "." + woord2 + ".")

f.close()
~~~

## Een bestand wegschrijven in python
Voor het wegschrijven van bestand in python moet je weten wat je wilt doen.

Als het bestand al bestaat kun je namelijk verschillende dingen doen. Je kunt namelijk:

* het hele bestand verwijderen en overschijven met nieuwe inhoud of
* inhoud achter het bestand bijvoegen (append)

Je kunt nog veel meer met bestanden maar voorlopig heb je aan deze twee manieren genoeg.

### Bestaande inhoud overschrijven
Om het bestand te openen en in zijn geheel te overschrijven gebruik je:

~~~python
f = open("leuk_bestand", 'w') #'w' zorgt ervoor dat het bestand overschreven wordt

f.write("Dit is de eerste regel in dit bestand\n")
f.write("Dit is het begin van de tweede regel ")
f.write("En dit is de tweede helft\n")

f.close()
~~~

Zoals je ziet moet je alle karakters die je in je bestand wilt hebben er naartoe schrijven, dus ook de regeleinde (`\n`).

Eigenlijk best simpel toch?

Je kunt natuurlijk ook `f.write()` gebruiken in een herhaling:

~~~python
f = open("bestandje", 'w')

for i in range(15):
  f.write("Dit is regel: " + str(i) + ".\n")

f.close()
~~~

### Achteraan Toevoegen
Wil je achter het bestand extra inhoud toevoegen dan gebruik je:

~~~python
f = open("bestandje", 'a') #'a' (append) zorgt ervoor dat inhoud achteraan toegevoegd wordt

f.write("Dit komt onderin het bestand\n")

f.close()
~~~
