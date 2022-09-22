# Rosy, Activité 2a : Panneau solaire V2

### Étape 1 @showdialog

Dans cette activité, nous allons **apprendre à mesurer** la [tension électrique](https://fr.wikipedia.org/wiki/Tension_%C3%A9lectrique) produite par le **panneau solaire**.

//changer le gif

<img alt="Résultat attendu de l'activité : le micro:bit affiche le niveau de tension électrique généré par le panneau solaire." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/gifactivite2_a.gif" width="60%">


### Étape 3 

Commencer par **connecter** le panneau solaire au micro:bit :

1. Insérer le micro:bit dans la carte de développement.
2. À l'aide des fils femelle-femelle :
    - Connecter le fil rouge (positif) du panneau solaire avec la broche 1 du micro:bit.
    - Connecter le fil noir (négatif) du panneau solaire avec la broche GND du micro:bit.

//changer l'image

<img alt="Les fils femelle-femelle font le lien entre le connecteur du panneau solaire et la carte de développement." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/RA2P2.jpg" width="80%">


### Étape 4

> ***Astuce*** : Si les instructions prennent trop de place à l'écran, simplement cliquer sur le bouton "Moins..." en gris au centre entre la fenêtre d'instruction et l'espace de programmation.

Il faut maintenant **programmer** le micro:bit. Commencer par aller dans la section ``||Variables||`` et **créer deux variables** :

1. solaire
2. volts

<img alt="Animation de la création des variables de l'étape 4." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/Rosy_Act2_01.gif" width="80%">


### Étape 5

1. Glisser le bloc ``||variables: définir||`` de la section ``||Variables||`` et le mettre dans ``||basic:toujours||``.
2. Lui attribuer la variable ``||variables:solaire||`` si ce n'est pas déjà fait.

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 5." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/Rosy_Act2_02.gif" width="80%">


```blocks
let solaire = 0
basic.forever(function () {
    solaire = 0
}
```

### Étape 6

Nous allons **lire la tension électrique** avec la broche 1 du micro:bit.

1. Assigner à la variable ``||variables:solaire||`` la lecture de la broche avec ``||pins:lire la broche analogique 1||`` qui se trouve dans la section ``||Broches||`` du menu "Avancé".
2. Assigner la broche *P1* dans ``||pins:lire la broche analogique 0||``.

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 6." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/Rosy_Act2_03.gif" width="80%">

```blocks
let solaire = 0
basic.forever(function () {
    solaire = pins.analogReadPin(AnalogPin.P1)
}
```


### Étape 7a

**Transformer** des valeurs numériques **en volts** :

Les **broches analogiques** du micro:bit peuvent lire des valeurs allant jusqu'à 3.3 volts et les représentent avec **des valeurs allant de 0 à 1023**.
Puisque le panneau solaire génère jusqu'à 3 volts d'électricité, il faut **diviser par 1023** la valeur lue, puis la **multiplier par 3**.


### Étape 7b

1. Glisser un autre bloc ``||variables:définir||`` à partir de ``||variables:Variables||`` dans ``||basic:toujours||``.
2. Y attribuer la variable "volts".
3. Prendre un bloc de ``||math:division||`` dans la section ``||math:Maths||``.
4. Diviser "solaire" par 1023.
5. Puis prendre un bloc ``||math:multiplication||`` et multiplier le bloc division que nous venons de créer par 3.
Mettre le tout dans la case à droite dans le bloc de définition de "volts".

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 7." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/Rosy_Act2_04.gif" width="80%">

```blocks
let solaire = 0
let volts = 0
basic.forever(function () {
    solaire = pins.analogReadPin(AnalogPin.P1)
    volts = solaire / 1023 * 3
    )
```

### Étape 8

Finalement, il ne reste qu'à **afficher** la valeur :
1. Glisser ``||led:tracer le graphe de||`` de la section ``||led:LED||``.
2. Y assigner la variable "volts" comme minimum.
3. Assigner la valeur 3.3 comme maximum.

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 8." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/Rosy_Act2_05.gif" width="80%">

```blocks
let solaire = 0
let volts = 0
basic.forever(function () {
    solaire = pins.analogReadPin(AnalogPin.P1)
    volts = solaire / 1023 * 3
    led.plotBarGraph(
    volts,
    3.3
    )
    )
```

### Étape 9

Il ne reste qu'à **téléverser** le code sur le micro:bit. **Les instructions** de notre simulateur de télescope **sont à la prochaine étape**.

Si vous avez besoin de vous rafraîchir la mémoire au sujet du téléversement du code, [voyez ici la vidéo aide-mémoire](https://youtu.be/H8utNPE3sJo) par GénieLab, et [voici la procédure détaillée](https://makecode.microbit.org/device/usb) dans la documentation de MakeCode (en anglais seulement).


### Étape 10

Voilà! Vous pouvez maintenant **visualiser l'énergie générée par le panneau solaire** directement sur le micro:bit!

Essayez de varier l'intensité lumineuse qui atteint le panneau solaire : l'écran du micro:bit allumera peu de DEL si le panneau solaire est peu éclairé, et toutes les DEL seront illuminées si beaucoup de lumière est fournie.