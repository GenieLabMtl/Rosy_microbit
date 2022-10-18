# Rosy, Activité 3 : Communication Radio : Relais V2

## Présentation 1 @showdialog

> -> Ce tutoriel s'adresse à la ou aux personnes qui feront la partie ***Satellite-relais*** de l'activité. Les parties ***Terre*** et ***Télescope spatial*** doivent également être faites pour que l'activité puisse avoir lieu.

![Rosy transmet un message](https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Relais.png)

Le télescope spatial veut transmettre une série de données qu'il a reçue en provenance d'une étoile lointaine au centre de commandement sur Terre pour qu'ils puissent être interprétés par une équipe de scientifiques.

Le problème est que le télescope a terminé sa mission il y a maintenant quelques années, et que plus personne n'écoute dans sa direction.


## Présentation 2 @showdialog

Votre rôle dans cette mission est de recevoir des messages provenant du télescope spatial et les transmettre au centre de commandement sur Terre. C'est une tâche en apparence simple, mais absolument critique à la réussite de la mission.

Pour réussir votre mission, vous devrez :

1. ***Choisir en équipe un numéro de groupe entre 0 et 255*** qui sera unique à votre équipe. Assurez-vous que les autres équipes de la classe ne prennent pas le même numéro.
2. ***Concevoir en équipe un [protocole de communication](https://fr.wikipedia.org/wiki/Protocole_de_communication)*** qui utilise seulement les chiffre 0, 1 et -1. Ce sera cette méthode de communication qui va permettre à la Terre de trouver l'emplacement de l'étoile sur un plan. Pour ce faire, vous devrez discuter de vos codes micro:bit respectifs afin de voir ce que chacun·e peut recevoir, envoyer et voir.
3. ***Recevoir les messages du satellite-télescope***, qui peuvent être 0, 1 ou -1.
4. ***Retransmettre ces données vers la Terre*** sans faire d'erreurs. Si le message n'est pas bien reçu par la Terre, les coordonnées de l'étoile d'où provient le signal extraterrestre ne seront pas connues et cette découverte n'aura jamais lieu! Les détails du défi se trouvent à la dernière étape de cette activité.

Les détails du défi se trouvent à la dernière étape de cette activité.

Bonne chance!

## Étape 1

> ***Astuce*** : Si les instructions prennent trop de place à l'écran, simplement cliquer sur le bouton "Moins..." en gris au centre entre la fenêtre d'instruction et l'espace de programmation.

La première chose à faire est d'initialiser la radio.

1. Aller dans la section ``||radio:radio||`` pour trouver le bloc ``||radio:définir groupe||``, puis le mettre dans le bloc ``||basic:au démarrage||``.
2. Attribuer la valeur de votre numéro de groupe au bloc ``||radio:définir groupe||``. Si une autre équipe a la même valeur de groupe, vos messages seront mélangés, ce qui va nuire à votre mission.

>**À noter! Il arrive que les images de la bulle d'aide soient différentes de ce que l'on retrouve dans l'espace de programmation : couleurs différentes, noms en anglais, noms de variables différents des instructions, etc. Pas de problème, il s'agit simplement d'un caprice d'affichage de la plateforme MakeCode que vous pouvez ignorer.**

<img alt="Activité 3 Relais Étape 1" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Relais_01.gif" width="300px">

```blocks
radio.setGroup(0)
```

## Étape 2

Lorsqu'une donnée est reçue du satellite-télescope, nous voulons la voir affichée.

1. Toujours dans la section ``||radio:radio||``, trouver le bloc ``||radio:quand une donnée est reçue par radio name value||`` et le glisser dans la page de programmation.
2. Ensuite, aller dans ``||logic:logique||`` pour trouver le bloc ``||logic:si <vrai> alors||``, et le mettre dans le bloc radio que l'on vient de prendre.

<img alt="Activité 3 Relais Étape 2" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Relais_02.gif" width="300px">

```blocks
radio.onReceivedValue(function (name, value) {
    if (True) {
    }
})
```

## Étape 3

Nous voulons seulement voir les données qui nous sont adressées. Nous devons donc vérifier que la [chaîne de caractères](https://fr.wikipedia.org/wiki/Cha%C3%AEne_de_caract%C3%A8res) que nous recevons est bien "relais".

1. Aller dans la section ``||logic:logique||``, y trouver ``||logic:" " = " "||``, et le glisser à la place de ``||logic:<vrai>||``.
2. Dans le cercle de gauche, glisser la variable ``||variables:name||`` qui se trouve dans ``||radio:quand une donnée est reçue par radio||``.
3. Dans le cercle de droite, inscrire "relais".

<img alt="Activité 3 Relais Étape 3" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Relais_03.gif" width="300px">

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "relais") {
    }
})
```

## Étape 4

Maintenant, affichons ces données et un point en haut de l'écran du micro:bit pour indiquer que nous n'avons pas encore agi après les avoir reçus.

1. Dans la section ``||basic:base||``, trouver ``||basic:montrer nombre||``, le mettre dans le bloc ``||logic:si <vrai> alors||``.
2. Glisser la variable ``||variables:value||`` de ``||radio:quand une donnée est reçue par radio||`` et la mettre dans le cercle de cet objet.
3. Aller dans la section ``||led:LED||``, prendre ``||led:allumer x y||`` et le mettre sous ``||basic:montrer nombre||``.
4. Y inscrire le chiffre 4 dans le cercle à côté de "x".

<img alt="Activité 3 Relais Étape 4" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Relais_04.gif" width="300px">

```blocks
radio.onReceivedValue(function (name, value) {
    if (name == "relais") {
        basic.showNumber(value)
        led.plot(4, 0)
    }
})
```

## Étape 5

Une fois que les données sont reçues, il faut les retransmettre à la Terre. Puisque nous pouvons recevoir et envoyer 3 types de caractères (0,1 et -1), il faudra faire 3 groupes de blocs similaires.

1. Dans ``||input:entrée||``, prendre le bloc ``||input:lorsque le bouton A est pressé||``.
2. Y insérer le bloc ``||radio:envoyer la valeur "" = 0 par radio||``.
3. Inscrire "terre" à gauche du "=", et laisser le chiffre à 0.

<img alt="Activité 3 Relais Étape 5" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Relais_05.gif" width="300px">

```blocks
input.onButtonPressed(Button.A, function () {
    radio.sendValue("terre", 0)
})
```

## Étape 6

Quand nous envoyons une donnée, elle est affichée à l'écran, puis l'écran est nettoyé. Commençons par "0".

Dans la section ``||basic:base||`` :
1. Trouver le bloc ``||basic:effacer l'écran||`` et le mettre sous ``||radio:envoyer la valeur||``.
2. Trouver le bloc ``||basic:montrer nombre 0||`` et le mettre à la suite.
3. Trouver le bloc ``||basic:pause (ms)||``, le mettre à la suite, et y inscrire le nombre 100.
4. Trouver le bloc ``||basic:effacer l'écran||`` et le mettre à la suite.

<img alt="Activité 3 Relais Étape 6" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Relais_06.gif" width="300px">

```blocks
input.onButtonPressed(Button.A, function () {
    radio.sendValue("terre", 0)
    basic.clearScreen()
    basic.showNumber(0)
    basic.pause(100)
    basic.clearScreen()
})
```

## Étape 7

Refaire la même chose que pour l'étape précédente, mais cette fois pour le "1". La fonction *Dupliquer* va nous aider.

1. Sur le bloc ``||input:lorsque le bouton A est pressé||`` que nous avons créé, faire clic droit, puis Dupliquer.
2. Changer le ``||input:bouton A||`` pour le ``||input:bouton B||``.
3. Changer le 0 pour 1 aux deux endroits où il apparait.

<img alt="Activité 3 Relais Étape 7" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Relais_07.gif" width="300px">

```blocks
input.onButtonPressed(Button.B, function () {
    radio.sendValue("terre", 1)
    basic.clearScreen()
    basic.showNumber(1)
    basic.pause(100)
    basic.clearScreen()
})
```

## Étape 8 @showhint

Refaire la même chose que pour l'étape précédente, mais cette fois pour le "-1".

1. Sur le bloc ``||input:lorsque le bouton A est pressé||``, faire clic droit, puis Dupliquer.
2. Changer le ``||input:bouton A||`` pour le ``||input:bouton A+B||``.
3. Changer le 0 pour -1 aux deux endroits où il apparait.

<img alt="Activité 3 Relais Étape 8" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Relais_08.gif" width="300px">

```blocks
input.onButtonPressed(Button.AB, function () {
    radio.sendValue("terre", -1)
    basic.clearScreen()
    basic.showNumber(-1)
    basic.pause(100)
    basic.clearScreen()
})
```

## Étape 9 @showhint

Voilà, le code est maintenant prêt! Le voici au complet. N'oubliez pas de faire dérouler l'image d'aide vers le bas pour le voir au complet.

```blocks
input.onButtonPressed(Button.A, function () {
    radio.sendValue("terre", 0)
    basic.clearScreen()
    basic.showNumber(0)
    basic.pause(100)
    basic.clearScreen()
})
input.onButtonPressed(Button.AB, function () {
    radio.sendValue("terre", -1)
    basic.clearScreen()
    basic.showNumber(-1)
    basic.pause(100)
    basic.clearScreen()
})
input.onButtonPressed(Button.B, function () {
    radio.sendValue("terre", 1)
    basic.clearScreen()
    basic.showNumber(1)
    basic.pause(100)
    basic.clearScreen()
})
radio.onReceivedValue(function (name, value) {
    if (name == "relais") {
        basic.showNumber(value)
        led.plot(4, 0)
    }
})
radio.setGroup(0)
```

## Étape 10

Il ne reste qu'à téléverser le code sur le micro:bit, et vous êtes prêt·e.

Si vous avez besoin de vous rafraîchir la mémoire au sujet du téléversement du code, [voyez ici la vidéo aide-mémoire](https://youtu.be/H8utNPE3sJo) par GénieLab, et [voici la procédure détaillée](https://makecode.microbit.org/device/usb) dans la documentation de MakeCode (en anglais seulement).


## Étape 11 @showdialog

Lorsque vos coéquipiers et coéquipières seront prêtes, vous pourrez commencer à retransmettre les données critiques à la mission.
En attendant, vous pouvez :

1. Vous pratiquer pour maitriser les boutons.
2. Élaborer un protocole de communication pour l'équipe. En effet, comment transmettre des messages comme "oui", "non", etc. avec seulement les caractères 0, 1 et -1?
3. Pouvez-vous trouver une façon d'améliorer l'affichage à l'écran du micro:bit?

Lorsque tout le monde est prêt, aller à la prochaine étape.

## Étape 12 @showdialog

Votre défi : guider l'équipe sur Terre pour qu'elle trouve la bonne étoile d'où provient le message, à l'aide de la carte suivante.

Voici le protocole de communication :

A) -1 veut dire une case vers la gauche
B) 1 veut dire une case vers la droite
C) Quand 0 est envoyé, ça veut dire que le déplacement horizontal est terminé, et qu'on commence le déplacement vertical
D) -1 veut alors dire une case vers le bas
E) 1 veut alors dire une case vers le haut
F) Pour vous assurer que les informations sont bien reçues, la Terre envoie un message de confirmation à chaque fois qu'elle reçoit un message : N pour vers le haut, S pour vers le bas, O pour vers la gauche, et E pour vers la droite.

1. La personne qui joue le rôle du satellite-relais (vous) doit retransmettre à la Terre les informations que vous recevez du télescope spatial... sans faire d'erreurs!
2. En partant du centre de l'image, la Terre devra correctement identifier l'étoile, que seul le télescope spatial connait.

Bonne chance!

![Charte des étoiles](https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/ciel_etoiles_v3.jpg)