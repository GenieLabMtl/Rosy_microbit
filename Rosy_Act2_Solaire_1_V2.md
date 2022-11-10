# Rosy, Activité 2a : Panneau solaire

### Étape 1 @showdialog

Dans cette activité, nous allons **apprendre à mesurer** la [tension électrique](https://fr.wikipedia.org/wiki/Tension_%C3%A9lectrique) produite par le **panneau solaire**.


<img alt="Résultat attendu de l'activité : le micro:bit affiche le niveau de tension électrique généré par le panneau solaire." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/Demo_Activite2.gif" width="300px">

### Matériels

Dans cette activité nous avons besoin de :
    - Le circuit imprimé.
    - un panneau solaire.
    - un micro:bit.
    - un cable usb.

<img alt="Le circuit imprimé, un panneua solaire, un microbit, un cable USB." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/Act2Pict3_v3.jpg" width="300px">


### Étape 3 

Commencer par **connecter** le panneau solaire au circuit imprimé :

1. **Insérer** le micro:bit dans le ciruit imprimé.
2. À l'aide des fils du panneau solaire :
    - Connecter le fil **rouge** (positif) du panneau solaire avec la broche **VCC**.
    - Connecter le fil **noir** (négatif) du panneau solaire avec la broche **GND** du circuit imprimé.

<img alt="Les fils femelle-femelle font le lien entre le connecteur du panneau solaire et le circuit imprimé." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/Cable_Solaire.jpg" width="300px">
<img alt="Les fils femelle-femelle font le lien entre le connecteur du panneau solaire et le circuit imprimé." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/ConnexionPCB.jpg" width="300px">


### Étape 4

> ***Astuce*** : Si les instructions prennent trop de place à l'écran, simplement cliquer sur le bouton "Moins..." en gris au centre entre la fenêtre d'instruction et l'espace de programmation.

Il faut maintenant **programmer** le micro:bit. Commencer par aller dans la section ``||variables:Variables||`` et **créer deux variables** :

1. ``||variables:solaire||``
2. ``||variables:volts||``

<img alt="Animation de la création des variables de l'étape 4." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/Rosy_Act2_01.gif" width="80%">


### Étape 5

1. **Ajouter** le bloc ``||variables: définir||`` de la section ``||Variables:Variables||`` et **l'ajouter** à ``||basic:toujours||``.
2. **Lui attribuer** la variable ``||variables:solaire||``.

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 5." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/Rosy_Act2_02.gif" width="80%">


```blocks
let solaire = 0
basic.forever(function () {
    solaire = 0
}
```

### Étape 6

Nous allons **lire la tension électrique** avec la broche **1** du micro:bit.

1. **Assigner à la variable** ``||variables:solaire||`` la lecture de la broche avec ``||pins:lire la broche analogique 1||`` qui se trouve dans la section ``||pins:Broches||`` du menu **Avancé**.
2. **Assigner** la broche ``||pins:P1||`` dans ``||pins:lire la broche analogique P0||``.

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 6." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/Rosy_Act2_03.gif" width="80%">

```blocks
let solaire = 0
basic.forever(function () {
    solaire = pins.analogReadPin(AnalogPin.P1)
}
```


### Étape 7

1. **Ajouter** un autre bloc ``||variables:définir||`` à partir de ``||variables:Variables||`` dans ``||basic:toujours||``.
2. **Lui attribuer** la variable ``||variables:volts||``.
3. **Prendre le bloc** ``||math:<0> ÷ <0>||`` dans la section ``||math:Maths||``.
4. **Diviser** ``||variables:solaire||`` par ``||math:303||``.
5. **Ajouter le tout** dans la case à droite dans le bloc ``||variables:définir volts à <0>||``.

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 7." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/gif1Act2aV2.gif" width="80%">

```blocks
let solaire = 0
let volts = 0
basic.forever(function () {
    solaire = pins.analogReadPin(AnalogPin.P1)  
    volts = solaire / 303
    )
```

### Étape 8

Finalement, il ne reste qu'à **afficher** la valeur :
1. **Ajouter** ``||led:tracer le graphe de 'MIN à 'MAX'||`` de la section ``||led:LED||``.
2. **Assigner** la variable ``||variables:volts||`` comme **minimum**.
3. **Assigner** la valeur 3.3 comme **maximum**.

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 8." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/gif2Act2aV2.gif" width="80%">

```blocks
let solaire = 0
let volts = 0
basic.forever(function () {
    solaire = pins.analogReadPin(AnalogPin.P1)
    volts = solaire / 303
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