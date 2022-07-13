# Rosy, Activité 3 : Communication Radio : télescope spatial

## Présentation 1 @showdialog

> -> Ce tutoriel s'adresse à la ou aux personnes qui feront la partie ***Télescope spatial*** de l'activité. Les parties ***Terre*** et ***Satellite-relais*** doivent également être faites pour que l'activité puisse avoir lieu.

![Rosy dans le télescope](https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Satellite.png)

Le télescope spatial veut transmettre une série de données pour indiquer l'emplacement d'une étoile lointaine au centre de commandement sur Terre.

Le problème est que le télescope a terminé sa mission il y a maintenant quelques années, et que plus personne n'écoute dans sa direction.


## Présentation 2 @showdialog

Votre rôle dans cette mission est de transmettre les données brutes au satellite relais. La Terre vous transmettra des informations pour confirmer ce qu'elle a reçu.

Pour réussir votre mission, vous devrez :

1. ***Choisir en équipe un numéro de groupe entre 0 et 255*** qui sera unique à votre équipe. Assurez-vous que les autres équipes de la classe ne prennent pas le même numéro.
2. ***Concevoir en équipe un [protocole de communication](https://fr.wikipedia.org/wiki/Protocole_de_communication)*** qui utilise seulement les chiffre 0, 1 et 2. Ce sera cette méthode de communication qui va permettre à la Terre de trouver l'emplacement de l'étoile sur un plan. Pour ce faire, vous devrez discuter de vos codes micro:bit respectifs afin de voir ce que chacun·e peut recevoir, envoyer et voir.
3. ***Envoyer des données*** au satellite-relais.
4. ***Visualiser les données de confirmation*** envoyées par le centre de commandement sur Terre quand ils reçoivent vos données pour s'assurer qu'ils ont reçu les bonnes informations.

Les détails du défi se trouvent à la dernière étape de cette activité.

Bonne chance!


## Étape 1

> ***Astuce*** : Si les instructions prennent trop de place à l'écran, simplement cliquer sur le bouton "Moins..." en gris au centre entre la fenêtre d'instruction et l'espace de programmation.

La première chose à faire est d'initialiser la radio.

1. Aller dans la section ``||radio:radio||`` pour trouver le bloc ``||radio:définir groupe||``, puis le mettre dans le bloc ``||basic:au démarrage||``.
2. Attribuer la valeur de votre numéro de groupe au bloc ``||radio:définir groupe||``. Si une autre équipe a la même valeur de groupe, vos messages seront mélangés, ce qui va nuire à votre mission.

>**À noter! Il arrive que les images de la bulle d'aide soient différentes de ce que l'on retrouve dans l'espace de programmation : couleurs différentes, noms en anglais, noms de variables différents des instructions, etc. Pas de problème, il s'agit simplement d'un caprice d'affichage de la plateforme MakeCode que vous pouvez ignorer.**

<img alt="Activité 3 Télescope Étape 1" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Telescope_01.gif" width="80%">

```blocks
radio.setGroup(0)
```

## Étape 2

Lorsqu'une donnée est reçue du centre de contrôle sur la Terre, nous voulons la voir affichée. 

1. Toujours dans la section ``||radio:radio||``, trouver le bloc ``||radio:quand une donnée est reçue par radio receivedString||`` et le glisser dans la page de programmation.
2. Ensuite, aller dans ``||logic:logique||`` pour trouver le bloc ``||logic:si <vrai> alors||`` et le mettre dans le bloc radio qu'on vient de prendre.
3. Cliquer sur le "+" pour ajouter 4 autres sections "sinon" dans ce bloc.

<img alt="Activité 3 Télescope Étape 2" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Telescope_02.gif" width="80%">

```blocks
radio.onReceivedString(function (receivedString) {
    if (True) {
    
    } else if (True) {
        
    } else if (True) {
        
    } else if (True) {
        
    } else {
        
    }
})
```

## Étape 3

Les données qui seront reçues peuvent être "n" pour Nord, "e" pour Est, "s" pour Sud, "o" pour Ouest, et "v" pour Valider. Lorsque nous recevrons ces lettres – qui sont appelées [chaînes de caractères](https://fr.wikipedia.org/wiki/Cha%C3%AEne_de_caract%C3%A8res) en programmation –, nous voudrons afficher sur le micro:bit une image qui lui correspond. Commençons par "n".

1. Aller dans la section ``||logic:logique||``, y trouver ``||logic:" " = " "||``, et le glisser à la place du premier ``||logic:<vrai>||``.
2. Dans le cercle de gauche, glisser la variable ``||variables:receivedString||`` qui se trouve dans ``||radio:quand une donnée est reçue par radio||``.
3. Dans le cercle de droite, inscrire "n".
4. Dans la section ``||basic:base||``, trouver le bloc ``||basic:montrer la flèche||`` et la mettre dans ce bloc.
5. Choisir "Nord" dans ce bloc.

<img alt="Activité 3 Télescope Étape 3" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Telescope_03.gif" width="80%">

```blocks
radio.onReceivedString(function (receivedString) {
    if (receivedString == "n") {
        basic.showArrow(ArrowNames.North)
    } else if (True) {

    } else if (True) {
 
    } else if (True) {
       
    } else {
        
    }
})
```

## Étape 4

Refaire la même chose pour les autres lettres "e" Est, "s" Sud, et "o" Ouest.

<img alt="Activité 3 Télescope Étape 4" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Telescope_04.gif" width="80%">

```blocks
radio.onReceivedString(function (receivedString) {
    if (receivedString == "n") {
        basic.showArrow(ArrowNames.North)
    } else if (receivedString == "e") {
        basic.showArrow(ArrowNames.East)
    } else if (receivedString == "s") {
        basic.showArrow(ArrowNames.South)
    } else if (receivedString == "o") {
        basic.showArrow(ArrowNames.West)
    } else {
        
    }
})
```


## Étape 5

Si ce que nous recevons n'est pas une de ces quatre lettres, faisons afficher un symbole de validation.

1. Dans la section ``||basic:base||``, trouver le bloc ``||basic:montrer l'icône||`` et la mettre dans la section ``||logic:sinon||`` du bloc.
2. Choisir l'image qui montre un crochet de validation.

<img alt="Activité 3 Télescope Étape 5" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Telescope_05.gif" width="80%">

```blocks
radio.onReceivedString(function (receivedString) {
    if (receivedString == "n") {
        basic.showArrow(ArrowNames.North)
    } else if (receivedString == "e") {
        basic.showArrow(ArrowNames.East)
    } else if (receivedString == "s") {
        basic.showArrow(ArrowNames.South)
    } else if (receivedString == "o") {
        basic.showArrow(ArrowNames.West)
    } else {
        basic.showIcon(IconNames.Yes)
    }
})
```

## Étape 6

Finalement, nous voulons nettoyer l'écran une fois l'information reçue.

1. Trouver le bloc ``||basic:pause (ms)||`` et le mettre après et en dehors du multibloc ``||logic:si <> alors||``, puis y inscrire le nombre 200.
2. Trouver le bloc ``||basic:effacer l'écran||`` et le mettre à la suite.

<img alt="Activité 3 Télescope Étape 6" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Telescope_06.gif" width="80%">

```blocks
radio.onReceivedString(function (receivedString) {
    if (receivedString == "n") {
        basic.showArrow(ArrowNames.North)
    } else if (receivedString == "e") {
        basic.showArrow(ArrowNames.East)
    } else if (receivedString == "s") {
        basic.showArrow(ArrowNames.South)
    } else if (receivedString == "o") {
        basic.showArrow(ArrowNames.West)
    } else {
        basic.showIcon(IconNames.Yes)
    }
    basic.pause(200)
    basic.clearScreen()
})
```

## Étape 7

Il faut maintenant pouvoir transmettre des données qui seront retransmises par le satellite-relais. Puisque nous pouvons envoyer trois types de caractères (0,1 et 2), il faudra faire trois groupes de blocs similaires. Voici comment faire le premier :

1. Dans ``||input:entrée||``, prendre le bloc ``||input:lorsque le bouton A est pressé||``.
2. Y insérer le bloc ``||radio:envoyer la valeur "" = 0 par radio||``.
3. Inscrire "relais" à gauche du "=", et laisser le chiffre à 0.

<img alt="Activité 3 Télescope Étape 7" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Telescope_07.gif" width="80%">

```blocks
input.onButtonPressed(Button.A, function () {
    radio.sendValue("relais", 0)
})
```

## Étape 8

Quand nous envoyons une donnée, elle s'affiche à l'écran, puis l'écran est nettoyé. Commençons par "0".

Dans la section ``||basic:base||`` :
1. Trouver le bloc ``||basic:montrer nombre 0||`` et le mettre sous ``||radio:envoyer la valeur||``.
2. Trouver le bloc ``||basic:pause (ms)||`` et le mettre à la suite, puis y inscrire le nombre 100.
3. Trouver le bloc ``||basic:effacer l'écran||`` et le mettre à la suite.

<img alt="Activité 3 Télescope Étape 8" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Telescope_08.gif" width="80%">

```blocks
input.onButtonPressed(Button.A, function () {
    radio.sendValue("relais", 0)
    basic.showNumber(0)
    basic.pause(100)
    basic.clearScreen()
})
```

## Étape 9

Refaire la même chose qu'à l'étape précédente, mais cette fois pour le "1". La fonction *Dupliquer* va nous aider.

1. Sur le bloc ``||input:lorsque le bouton A est pressé||`` que nous avons créé à l'étape précédente, faire clic droit, puis Dupliquer.
2. Changer le ``||input:bouton A||`` pour le ``||input:bouton B||``.
3. Changer le 0 pour 1 aux deux endroits où il apparait.

<!-- 1. Dans ``||input:entrée||``, prendre le bloc ``||input:lorsque le bouton A est pressé||`` et changer le "A" pour "B".
2. Y insérer le bloc ``||radio:envoyer la valeur "" = 0 par radio||``.
3. Inscrire "relais" à gauche du "=", et changer le chiffre à 1.
4. Trouver le bloc ``||basic:montrer nombre 0||`` et le mettre sous ``||radio:envoyer la valeur||``, puis attribuer le nombre 1.
5. Trouver le bloc ``||basic:pause (ms)||`` et le mettre à la suite, puis y inscrire le nombre 100.
6. Trouver le bloc ``||basic:effacer l'écran||`` et le mettre à la suite. -->

<img alt="Activité 3 Télescope Étape 9" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Telescope_09.gif" width="80%">

```blocks
input.onButtonPressed(Button.B, function () {
    radio.sendValue("relais", 1)
    basic.showNumber(1)
    basic.pause(100)
    basic.clearScreen()
})
```

## Étape 10

Refaire encore la même chose, mais cette fois pour le "2".

1. Sur le bloc ``||input:lorsque le bouton A est pressé||``, faire clic droit, puis Dupliquer.
2. Changer le ``||input:bouton A||`` pour le ``||input:bouton A+B||``.
3. Changer le 0 pour 2 aux deux endroits où il apparait.

<img alt="Activité 3 Télescope Étape 10" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Telescope_10.gif" width="80%">

```blocks
input.onButtonPressed(Button.AB, function () {
    radio.sendValue("relais", 2)
    basic.showNumber(2)
    basic.pause(100)
    basic.clearScreen()
})
```

## Étape 11 @showhint

Voilà, le code est maintenant prêt! Le voici au complet. N'oubliez pas de faire dérouler l'image d'aide vers le bas pour le voir au complet.


```blocks
input.onButtonPressed(Button.A, function () {
    radio.sendValue("relais", 0)
    basic.showNumber(0)
    basic.pause(100)
    basic.clearScreen()
})
input.onButtonPressed(Button.AB, function () {
    radio.sendValue("relais", 2)
    basic.showNumber(2)
    basic.pause(100)
    basic.clearScreen()
})
radio.onReceivedString(function (receivedString) {
    if (receivedString == "n") {
        basic.showArrow(ArrowNames.North)
    } else if (receivedString == "e") {
        basic.showArrow(ArrowNames.East)
    } else if (receivedString == "s") {
        basic.showArrow(ArrowNames.South)
    } else if (receivedString == "o") {
        basic.showArrow(ArrowNames.West)
    } else {
        basic.showIcon(IconNames.Yes)
    }
    basic.pause(200)
    basic.clearScreen()
})
input.onButtonPressed(Button.B, function () {
    radio.sendValue("relais", 1)
    basic.showNumber(1)
    basic.pause(100)
    basic.clearScreen()
})
radio.setGroup(0)
``` 

## Étape 12

Il ne reste qu'à téléverser le code sur le micro:bit, et vous êtes prêt·e.

Si vous avez besoin de vous rafraîchir la mémoire, [voyez ici la vidéo aide-mémoire](https://youtu.be/H8utNPE3sJo) par GénieLab, et [voici la procédure détaillée](https://makecode.microbit.org/device/usb) dans la documentation de MakeCode (en anglais seulement).


## Étape 13 @showdialog

Lorsque vous et vos coéquipiers et coéquipières serez prêtes, vous pourrez commencer la mission comme telle, qui se trouve à la prochaine étape.
En attendant, vous pouvez :

1. Vous pratiquer pour maitriser les boutons.
2. Pouvez-vous trouver une façon d'améliorer l'affichage à l'écran du micro:bit?

Lorsque tout le monde est prêt, aller à la prochaine étape.

## Étape 14 @showdialog

Voici votre défi : guider l'équipe sur Terre pour qu'elle trouve la bonne étoile d'où provient le message, à l'aide de la carte suivante.

Il est maintenant temps de revenir à votre protocole de communication. Maintenant que vous et vos deux coéquipiers et coéquipières êtes prêtes à commencer la communication, il faut vous entendre sur ce que veulent dire vos messages. Comment donner des directions précises avec des moyens de communication limités? Par exemple, vous pouvez vous inspirer du [code Morse](https://fr.wikipedia.org/wiki/Code_Morse_international), qui utilise seulement les deux symboles "." et "-" pour épeler toutes les lettres de l'alphabet, ou encore du [code binaire](https://fr.wikipedia.org/wiki/Code_binaire), qui n'utilise que des 1 et de 0.

1. Vous entendre sur un protocole de communication en équipe.
2. La personne qui joue le rôle du télescope spatial (vous) choisit secrètement une étoile sur la carte.
3. En utilisant le l'étoile Polaire (centre de l'image) comme point de départ, donner des instructions pour que la Terre puisse correctement identifier cette étoile.

Bonne chance!

![Charte des étoiles](https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/ciel_etoiles_v3.jpg)
