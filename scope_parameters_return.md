# Scope parameters en returnwaarden
## Scope
Scope geeft simpelgezegd antwoord op de vraag: "Waar heb ik toegang tot deze variabele?"

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

We kunnen overal de leeftijd lezen, gebruiken en veranderen.

## parameters


## returnwaarden
