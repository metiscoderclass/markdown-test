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

Je wilt in een textbased programma vaak dat je regel een vast aantal karakters lang is, bijvoorbeeld 50. En soms wil je een kader om je hele programma hebben. Een regel kan er dus als volgt uit zien:

~~~
| Woord: vlieger                                 |
~~~

Of zo:

~~~
| Woord: vlieger           Vertaling: kite       |
~~~
