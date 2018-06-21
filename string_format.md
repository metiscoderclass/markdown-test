# Strings weergeven met .format()

## De basis

In dit hoofdstuk kijken we naar andere manieren om een `string` naar het scherm te printen. Alles wat we hier doen kun je ook doen met behulp van loops en extra variabelen. Het lijkt in het begin misschien onzinnig om het op te lossen met `.format()` maar later kunnen we echt de voordelen laten zien. Probeer dat dus in het achterhoofd te houden als we daar mee bezig gaan!

Je kent wel bijvoorbeeld de volgende syntax:

~~~python
naam = input("Hoe heet je? ")
print("-"*27)
print("Naam: " + naam)
print("-"*27)
~~~

Maar wat nu als je de naam rechts wil laten uitlijnen? Dus als volgt:

~~~
---------------------------
Naam:        Henkie Willems
---------------------------
~~~

We kunnen dit doen door de lengte van de gegeven naam te gebruiken:

~~~python
naam = input("Hoe heet je? ")
lengte = len(naam)
print("-"*27)
print("Naam: " + " "*(27-lengte) + naam)
print("-"*27)
~~~

Maar Python `string` heeft ook de ingebouwde functie `format()` om dit mee te doen.

~~~python
naam = input("Hoe heet je? ")
print("-"*27)
print("Naam: {:>21}".format(naam))
print("-"*27)
~~~

Hierin wordt de `{}` vervangen door wat je meegeeft aan de functie (in dit geval `naam`). `>` betekent dat het rechts wordt uitgelijnd en `21` betekent dat het veld met de naam altijd 21 karakters breed is.

Dit gaat best snel dus daarom wil ik verwijzen naar een uitstekende online uitleg over `format()`. Ga die uitleg doornemen en zorg dat je in ieder geval de basisprincipes snapt.

Online uitleg: [https://www.digitalocean.com/community/tutorials/how-to-use-string-formatters-in-python-3]

## Uitlijnen

Je wilt in een textbased programma vaak dat je regel een vast aantal karakters lang is, bijvoorbeeld 60. En soms wil je een kader om je hele programma hebben zoals als volgt:
~~~
------------------------------------------------------------
|                       Menu                               |
|                                                          |          
|  o: start het overhoren                                  |
|  q: sluit het programma                                  |
------------------------------------------------------------
~~~

Een regel bij het overhoren kan er dan als volgt uit zien:

~~~
| Woord: vlieger                                           |
~~~

Of zo:

~~~
| Woord: vlieger        Vertaling: kite                    |
~~~

Het tweede voorbeeld kunnen we maken als volgt:

~~~python
woord = "vlieger"
vertaling = "kite"
print("| Woord: {:14} Vertaling: {:23} |".format(woord, vlieger))
~~~

Maar in een programma dat je schrijft heb je misschien wel 100 van dit soort printregels. Wat nou als je dan niet 50 maar 60 karakters breed wilt werken? En wat als je je woordlengte niet 14 maar 15 karakters breed wilt? Dan moet je het overal veranderen! Dan mis je er vast één of je maakt een rekenfout. We willen dit gaan oplossen met behulp van een constante waarde voor de breedte van het scherm en de maximale lengte van een woord.

We beginnen weer eenvoudiger met het voorbeeld:
~~~
| Woord: vlieger                                 |
~~~

We zeggen nu `SCHERMBREEDTE = 60` en gaan het aantal karakters voor het uitlijnen uitrekenen aan de hand van de schermbreedte en de maximale voordlengte. We kiezen ervoor dat woorden maximaal 14 karakters lang kunnen zijn.

~~~python
SCHERMBREEDTE = 60
MAX_WOORD_LENGTE = 14

woord = "vlieger"

print("| Woord: {:" + str(MAX_WOORD_LENGTE)+ "}".format(woord) + " "*(SCHERMBREEDTE - MAX_WOORD_LENGTE - 10) + "|")
~~~

Het stuk `"| Woord: {:" + str(MAX_WOORD_LENGTE)+ "}"` zal door Python veranderd worden in `"| Woord: {:14}"`.

Hierin is `10` het aantal karakters in de stukjes die vast liggen: `| Woord: ` en `|`. Dit zorgt ervoor dat `" "*SCHERMBREEDTE - MAX_WOORD_LENGTE - 10` precies het aantal spaties zal printen om het geheel mooi uit te lijnen.

Dit stuk code is nog wel te lezen. Maar het ziet er nou niet echt fraai uit.

Terug naar het tweede voorbeeld. Hoe gaan we het daar oplossen?

~~~
| Woord: vlieger        Vertaling: kite                    |
~~~

Nou, een eerste poging is:

~~~python
SCHERMBREEDTE = 50
MAX_WOORD_LENGTE = 14

woord = "vlieger"
vertaling = "kite"
print("| Woord: {:" + str(MAX_WOORD_LENGTE) + "} Vertaling: {:" + str(MAX_WOORD_LENGTE) + "}".format(woord, vlieger) + " "*str(SCHERMBREEDTE - 2*MAX_WOORD_LENGTE - 22) + "|")
~~~

De code ziet er onoverzichtelijker uit. Daar gaan we straks wat aan doen. Maar het probleem van variabele schermbreedte is nu opgelost. Het `|`-teken wordt altijd mooi rechts uitgelijnd. Maar als we `|` willen wijzigen in bijvoorbeeld `#` dan moeten we dat nog steeds op heel veel plekken in de code gaan doen!

Om dat te verbeteren en tegelijkertijd de code beter leesbaar te maken gaan we een functie maken om één regel netjes uit te lijnen.

~~~python
SCHERMBREEDTE = 50
MAX_WOORD_LENGTE = 14

woord = "vlieger"
vertaling = "kite"

def print_regel(regel):
  # Haal 4 karakters van schermbreedte af: '| ' en ' |'
  print("| {:" + str(SCHERMBREEDTE - 4)+ "} |".format(regel))

print_regel("Woord: {:^" + str(MAX_WOORD_LENGTE) "} Vertaling: {:^" + str(MAX_WOORD_LENGTE) + "}".format(woord, vertaling))
~~~

Dat ziet er al een stuk beter uit! En we hebben meteen de woorden `woord` en `vertaling` laten centreren.
