# Rosy, Activité 3 : Communication Radio : Terre V2

## Présentation 1 @showdialog

> -> Ce tutoriel s'adresse à la ou aux personnes qui feront la partie ***Terre*** de l'activité. Les parties ***Satellite-relais*** et ***Télescope spatial*** doivent également être faites pour que l'activité puisse avoir lieu.

![Rosy quelque part dans l'espace](https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Terre_Mars.png)

Le télescope spatial veut transmettre les coordonnées d'une étoile lointaine au centre de commandement sur Terre pour qu'une équipe de scientifiques puisse analyser le signal qui en émane.

Le problème est que le télescope a terminé sa mission il y a maintenant quelques années, et que plus personne n'écoute dans sa direction.

## Présentation 2 @showdialog

Votre rôle dans cette mission est de recevoir des messages provenant du satellite-relais, puis de confirmer la réception de ces messages pour que le télescope ait la confirmation qu'ils ont bien été reçus.

Pour réussir votre mission, vous devrez :

1. ***Choisir en équipe un numéro de groupe entre 0 et 255*** qui sera unique à votre équipe. Assurez-vous que les autres équipes de la classe ne prennent pas le même numéro.

2. ***Concevoir en équipe un [protocole de communication](https://fr.wikipedia.org/wiki/Protocole_de_communication)*** qui utilise seulement les chiffre 0, 1 et -1. Ce sera cette méthode de communication qui va permettre à la Terre de trouver l'emplacement de l'étoile sur un plan. Pour ce faire, vous devrez discuter de vos codes micro:bit respectifs afin de voir ce que chacun·e peut recevoir, envoyer et voir.
3. ***Recevoir les données*** du satellite-relais, et ***envoyer des données de confirmation***.
4. ***Trouver l'étoile*** d'où provient le signal extra-terrestre. Les détails du défi se trouvent à la dernière étape de cette activité.

Les détails du défi se trouvent à la dernière étape de cette activité.

Bonne chance!


## Étape 1

> ***Astuce*** : Si les instructions prennent trop de place à l'écran, simplement cliquer sur le bouton "Moins..." en gris au centre entre la fenêtre d'instruction et l'espace de programmation.

La première chose à faire est d'initialiser la radio.

1. Aller dans la section ``||radio:radio||`` pour **trouver** le bloc ``||radio:définir groupe||``, puis **l'ajouter** dans le bloc ``||basic:au démarrage||``.
2. **Attribuer** la valeur de votre numéro de groupe au bloc ``||radio:définir groupe||``. Si une autre équipe a la même valeur de groupe, vos messages seront mélangés, se qui va nuire à votre mission.

>**À noter! Il arrive que les images de la bulle d'aide soient différentes de ce que l'on retrouve dans l'espace de programmation : couleurs différentes, noms en anglais, noms de variables différents des instructions, etc. Pas de problème! Il s'agit simplement d'un caprice d'affichage de la plateforme MakeCode que vous pouvez ignorer.**

<img alt="Activité 3 Terre Étape 1" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Terre_01.gif" width="80%">

```blocks
radio.setGroup(0)
```

## Étape 2

Lorsqu'une donnée est reçue du satellite-relais, nous voulons la voir affichée.

1. Toujours dans la section ``||radio:radio||``, **trouver** le bloc ``||radio:quand une donnée est reçue par radio name value||`` et **l'ajouter** à la page de programmation.
2. Aller dans ``||logic:logique||`` pour **trouver** le bloc ``||logic:si <vrai> alors||`` et **l'ajouter** dans le bloc radio que l'on vient de prendre.

<img alt="Activité 3 Terre Étape 2" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Terre_02.gif" width="80%">

```blocks
radio.onReceivedValue(function (name, value) {
    if (True) {
    }
})
```

## Étape 3

Il faut afficher la bonne image selon les données reçues, qui peuvent être 0, 1 ou -1. Commençons par recevoir les bons messages, qui sont sous forme de [chaînes de caractères](https://fr.wikipedia.org/wiki/Cha%C3%AEne_de_caract%C3%A8res).

1. Aller dans la section ``||logic:logique||``, **y trouver** ``||logic: " " = " "||``, et **l'ajouter** à la place de ``||logic:<vrai>||``.
2. Dans le cercle de gauche, **glisser** la variable ``||variables:name||`` qui se trouve dans ``||radio:quand une donnée est reçue par radio||``.
3. Dans le cercle de droite, **inscrire** "terre".

<img alt="Activité 3 Terre Étape 3" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Terre_03.gif" width="80%">

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "terre") {

    }
})
```

## Étape 4

Affichons maintenant les données reçues, puis nettoyons ensuite l'écran.

1. Dans la section ``||basic:base||``, **trouver** le bloc ``||basic:montrer nombre||`` et **l'ajouter** dans notre bloc ``||logic:si...alors||``.
2. **Glisser** la variable ``||variables:value||`` qui se trouve dans ``||radio:quand une donnée est reçue par radio||`` dans le cercle à droite dans ``||basic:montrer nombre||``.
3. Dans la section ``||basic:base||``, **trouver** le bloc ``||basic:pause (ms)||`` et **l'ajouter** à la suite.
4. **Trouver** le bloc ``||basic:effacer l'écran||`` et **l'ajouter** à la suite.

<img alt="Activité 3 Terre Étape 4" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Terre_04.gif" width="80%">

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "terre") {
        basic.showNumber(value)
        basic.pause(200)
        basic.clearScreen()
    }
})
```


## Étape 5

Nous voulons maintenant pouvoir envoyer des messages de confirmation. Ils peuvent être : *flèche à gauche* (ouest), *flèche à droite* (est), *flèche en haut* (nord), *flèche en bas* (sud), et *crochet de validation*.
Pour sélectionner le message à envoyer, nous allons utiliser l'[accéléromètre](https://fr.wikipedia.org/wiki/Acc%C3%A9l%C3%A9rom%C3%A8tre) du micro:bit.

1. Dans ``||input:entrée||``, **prendre** le bloc ``||input:lorsque le bouton A est pressé||``.
2. **Y insérer** le double bloc ``||logic:si <vrai> alors...sinon||`` de la section ``||logic:logique||``
3. **Aller** dans la section ``||logic:logique||``, y trouver l'hexagone ``||logic:plus petit que||``, et le **glisser** dans le premier ``||logic:si <vrai> alors||``.
4. Dans la section ``||input:entrée||``, **trouver** ``||input:accélération (mg)||`` et **l'ajouter** dans le cercle à gauche du ``||logic:plus petit que||``.

<img alt="Activité 3 Terre Étape 5" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Terre_05.gif" width="80%">

```blocks
input.onButtonPressed(Button.A, function () {
    if (input.acceleration(Dimension.X) < 0) {

    } else {

    }
})
```


## Étape 6

Lorsque le micro:bit penche vers la gauche et que l'on appuie sur le ``||input:bouton A||``, nous allons envoyer "o" pour Ouest. Ensuite, affichons ce que nous avons envoyé.

1. **Insérer** le bloc ``||radio:envoyer la chaîne "" par radio||`` de la section ``||radio:radio||`` sous le "si", et inscrire la lettre "o" dans ce bloc.
2. Dans la section ``||basic:base||``, **trouver** le bloc ``||basic:montrer la flèche||``, **l'ajouter** dans ce bloc et choisir "Ouest".
3. **Trouver** le bloc ``||basic:pause (ms)||`` et **l'ajouter** à la suite, puis **y inscrire** le nombre **100**.
4. **Trouver** le bloc ``||basic:effacer l'écran||`` et **l'ajouter** à la suite.

<img alt="Activité 3 Terre Étape 6" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Terre_06.gif" width="80%">

```blocks
input.onButtonPressed(Button.A, function () {
    if (input.acceleration(Dimension.X) < 0) {
        radio.sendString("o")
        basic.showArrow(ArrowNames.West)
        basic.pause(100)
        basic.clearScreen()
    } else {

    }
})
```

## Étape 7

Dans la section ``||logic:sinon||``, refaire la même chose, mais pour envoyer "e" pour Est.

1. Insérer le bloc ``||radio:envoyer la chaîne "" par radio||`` de la section ``||radio:radio||`` sous le ``||logic:sinon||``, et inscrire la lettre "e" dans ce bloc.
2. Dans la section ``||basic:base||``, trouver le bloc ``||basic:montrer la flèche||``, la mettre dans ce bloc et choisir "Est".
3. Trouver le bloc ``||basic:pause (ms)||`` et le mettre à la suite, puis y inscrire le nombre 100.
4. Trouver le bloc ``||basic:effacer l'écran||`` et le mettre à la suite.

<img alt="Activité 3 Terre Étape 7" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Terre_07.gif" width="80%">

```blocks
input.onButtonPressed(Button.A, function () {
    if (input.acceleration(Dimension.X) < 0) {
        radio.sendString("o")
        basic.showArrow(ArrowNames.West)
        basic.pause(100)
        basic.clearScreen()
    } else {
        radio.sendString("e")
        basic.showArrow(ArrowNames.East)
        basic.pause(100)
        basic.clearScreen()
    }
})
```

## Étape 8

Refaire la même chose qu'aux étapes 5 à 7, mais pour "Nord" et "Sud". La fonction *Dupliquer* va nous aider.

1. Sur le bloc ``||input:lorsque le bouton A est pressé||`` que nous avons créé à l'étape précédente, faire clic droit, puis Dupliquer.
2. Changer le ``||input:bouton A||`` pour le ``||input:bouton B||``.
3. Assigner "Y" à ``||input:accélération (mg)||``.
4. Changer "o" pour "n", et "Ouest" pour "Nord".
5. Changer "e" pour "s", et "Est" pour "Sud".

<img alt="Activité 3 Terre Étape 8" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Terre_08.gif" width="80%">

```blocks
input.onButtonPressed(Button.B, function () {
    if (input.acceleration(Dimension.Y) < 0) {
        radio.sendString("n")
        basic.showArrow(ArrowNames.North)
        basic.pause(100)
        basic.clearScreen()
    } else {
        radio.sendString("s")
        basic.showArrow(ArrowNames.South)
        basic.pause(100)
        basic.clearScreen()
    }
})
```

## Étape 9

Pour aider à la communication, il est pratique d'envoyer un message de validation pour signaler que le message a été bien reçu. Appuyez sur les ``||input:boutons A et B||`` en même temps nous permettra d'envoyer ce message.

Pour se faire, ajoutons un troisième bloc ``||input:lorsque le bouton A est pressé||``.

1. Créer un nouveau ``||input:lorsque le bouton A est pressé||`` et changer le ``||input:bouton A||`` pour ``||input:bouton A+B||``.
2. Y insérer le bloc ``||radio:envoyer la chaîne "" par radio||`` de la section ``||radio:radio||``, et y inscrire "ok".

<img alt="Activité 3 Terre Étape 9" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Terre_09.gif" width="80%">

```blocks
input.onButtonPressed(Button.AB, function () {
    radio.sendString("ok")
})
```

## Étape 10

Lorsque le message de confirmation est envoyé, affichons aussi une confirmation visuelle à notre écran.

1. Dans la section ``||basic:base||``, trouver le bloc ``||basic:montrer l'icône||`` et le mettre à la suite de ``||radio:envoyer la chaîne "ok" par radio||``.
2. Choisir l'image du crochet de validation dans le bloc ``||basic:montrer l'icône||``.
3. Trouver le bloc ``||basic:pause (ms)||``, le mettre à la suite et y inscrire le nombre 100.
4. Trouver le bloc ``||basic:effacer l'écran||`` et le mettre à la suite.

<img alt="Activité 3 Terre Étape 10" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Terre_10.gif" width="80%">

```blocks
input.onButtonPressed(Button.AB, function () {
    radio.sendString("ok")
    basic.showIcon(IconNames.Yes)
    basic.pause(100)
    basic.clearScreen()
})
```

## Étape 11 @showhint

Voilà, le code est maintenant prêt! Le voici au complet. N'oubliez pas de faire dérouler l'image d'aide vers le bas pour le voir au complet.

```blocks
input.onButtonPressed(Button.A, function () {
    if (input.acceleration(Dimension.X) < 0) {
        radio.sendString("o")
        basic.showArrow(ArrowNames.West)
        basic.pause(100)
        basic.clearScreen()
    } else {
        radio.sendString("e")
        basic.showArrow(ArrowNames.East)
        basic.pause(100)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.AB, function () {
    radio.sendString("ok")
    basic.showIcon(IconNames.Yes)
    basic.pause(100)
    basic.clearScreen()
})
input.onButtonPressed(Button.B, function () {
    if (input.acceleration(Dimension.Y) < 0) {
        radio.sendString("n")
        basic.showArrow(ArrowNames.North)
        basic.pause(100)
        basic.clearScreen()
    } else {
        radio.sendString("s")
        basic.showArrow(ArrowNames.South)
        basic.pause(100)
        basic.clearScreen()
    }
})
radio.onReceivedValue(function (name, value) {
    if (name == "terre") {
        basic.showNumber(value)
        basic.pause(200)
        basic.clearScreen()
    }
})
radio.setGroup(0)
```


## Étape 12

Il ne reste qu'à téléverser le code sur le micro:bit, et vous êtes prêt·e.

Si vous avez besoin de vous rafraîchir la mémoire au sujet du téléversement du code, [voyez ici la vidéo aide-mémoire](https://youtu.be/H8utNPE3sJo) par GénieLab, et [voici la procédure détaillée](https://makecode.microbit.org/device/usb) dans la documentation de MakeCode (en anglais seulement).


## Étape 13 @showdialog

Lorsque vos coéquipiers et coéquipières seront prêtes, vous pourrez commencer à recevoir et interpréter les données critiques à la mission, qui se trouvent à la prochaine étape.
En attendant, vous pouvez :

1. Vous pratiquer pour maitriser les boutons.
2. Pouvez-vous trouver une façon d'améliorer l'affichage à l'écran du micro:bit?

Lorsque tout le monde est prêt, aller à l'étape suivante.


## Étape 14 @showdialog

Votre défi : l'équipe du satellite-télescope va vous guider, en passant par le satellite-relais, pour trouver l'étoile d'où provient le message, à l'aide du plan suivant.

Voici le protocole de communication :

A) -1 veut dire une case vers la gauche
B) 1 veut dire une case vers la droite
C) Quand 0 est envoyé, ça veut dire que le déplacement horizontal est terminé, et qu'on commence le déplacement vertical
D) -1 veut alors dire une case vers le bas
E) 1 veut alors dire une case vers le haut
F) Pour vous assurer que les informations sont bien reçues, la Terre envoie un message de confirmation à chaque fois qu'elle reçoit un message : N pour vers le haut, S pour vers le bas, O pour vers la gauche, et E pour vers la droite.

1. Recevoir les informations de l'équipe satellite-relais et les interpréter selon le protocole établi.
2. En utilisant l'étoile Polaire (le centre de l'image) comme point de référence, suivre les indications reçues pour trouver la bonne étoile.

Une excellente communication entre toutes les équipes sera essentielle à la réussite de cette mission. Bonne chance!

![Charte des étoiles](https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/ciel_etoiles_v3.jpg)