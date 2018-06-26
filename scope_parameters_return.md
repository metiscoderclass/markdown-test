# Scope, parameters en returnwaarden
## Scope
Scope geeft simpelgezegd antwoord op de vraag: "Waar heb ik toegang tot deze variabele?"

### Globale variabelen
Tot nu toe ben je gewend om met veel variabelen te werken die je aan het begin van je programma definieert. Deze variabelen zijn dan overal in je programma te benaderen. Ook in iedere functie.

Dat soort variabelen noemen we: **globale variabelen**. Ze zijn namelijk globaal (overal) beschikbaar.

Kijk maar eens naar het programma hieronder:

~~~python
leeftijd = 15

print(leeftijd)

def print_boodschap():
  print("Je bent " + str(leeftijd) + " jaar oud.")

print_boodschap()
leeftijd = 20
print_boodschap()
~~~

We kunnen overal de leeftijd lezen, gebruiken en veranderen. Als je in python een globale variabele wilt veranderen in een functie, dan heb je het woord `global` nodig. We gaan hier verder niet op in omdat het beter is zo min mogelijk globale variabelen te gebruiken.

Het probleem met globale variabelen is dat je er overal toegang toe hebt. Als je een groter programma hebt heb je niet meer scherp voor ogen waar je allemaal die globale variabele gebruikt. Hierdoor heb je minder overzicht en is de kans op bugs groter. Zoals met elke regel zijn er uitzonderingen dus als het beter is toch globaal een variabele te gebruiken dan moet je het zeker doen.

### Lokale variabelen
Maar hoe doen we het dan als we geen globale variabelen gaan gebruiken? We maken dan gebruik van **lokale variabelen**. Dit zijn variabelen die alleen op een bepaalde plek te gebruiken zijn, bijvoorbeeld in een functie. Een voorbeeld:

~~~python
def print_boodschap():
  naam = input("Hoe heet je?")
  print("Hallo " + naam)

print_boodschap()
print(naam)
~~~

Dit programma geeft een foutmelding. De variabele `naam` bestaat namelijk *alleen* **lokaal** in de functie `print_boodschap`! Dus als je daarna naam probeert uit te printen dan kent Python die variabele niet.

Nog een voorbeeld:

~~~python
naam = "Henk"

def verander_naam():
  naam = "Arie"
  print(naam)

verander_naam()
print(naam)
~~~

Als we dit programma uitvoeren zien we:

~~~
Arie
Henk
~~~

Dus eerst zal `naam == "Arie"` zijn (tijdens het uitvoeren van de functie) maar daarna is het gewoon weer `"Henk"`. Wat er gebeurt is dat en in de functie `vraag_naam()` een *nieuwe* variabale `naam` wordt gemaakt met een andere inhoud. Als de functie klaar is verdwijnt deze variabele en hebben we alleen nog de 'oude' variabele `naam` over met inhoud `Henk`.

Maar wat nu als we wel met de nieuwe naam door willen gaan? Daarvoor gebruiken we parameters en returnwaarden.

## Parameters en returnwaarden
Je weet al wat parameters zijn en misschien ook wel wat returnwaarden zijn. Parameters zijn waarden die je meegeeft aan een functie. Zo kun je toch informatie aan een functie geven zonder globale variabelen te gebruiken. Returnwaarden zijn dingen die een functie terug kan geven als deze klaar is.

Je kent dit al maar bent je daar misschien niet van bewust. Voorbeelden van functies waarbij je dit gebruikt:

~~~python
# Parameter: string die geprint wordt
# Returnwaarde: string die de gebruiker ingeeft
naam = input("Hoi hoe heet je?")

# Parameters: waarden waar tussen een getal wordt gekozen
# Returnwaarde: het gekozen getal
import random
getal = random.randint(1, 100)
~~~

Je geeft dus iets mee aan een functie en je krijgt ook iets terug.

Een voorbeeld (dat ook zonder een functie zou kunnen):

~~~python
def vraag_getal(vraag):
  getal = int(input(vraag))
  return getal

som = 0

while True:
  getal = vraag_getal("Geef een getal: ")
  som += getal
  getal = vraag_getal("Geef nog een getal: ")
  som += getal

  if som > 100:
    print("Som groter dan 100! Som: " + som)
    break
~~~

Dus wat zien we hier? Een functie `vraag_getal()` die als parameter een `string` meekrijgt die als vraag gesteld gaat worden. Dan zien we ook de *lokale* variabele `getal` in die functie. Dit `getal` wordt vervolgens teruggegeven als de functie klaar is.

In de `while`-loop wordt deze functie gebruikt en krijg je twee keer een getal als returnwaarde die je opslaat in een andere variabele `getal`.

Nou kun je dit voorbeeld ook makkelijk maken zonder te gebruik maken van een functie maar je zult merken dat het erg overzichtelijk is om ze te werken als je een groter programma hebt.
