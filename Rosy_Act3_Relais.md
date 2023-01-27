# Rosy, Activité 3 : Communication Radio : Relais

## Présentation 1 @showdialog

Le but de l'activité est de se familiariser avec la communication radio. 
Cette activité se fait en équipe de deux, cependant il y a la possibilité de le faire à plus mais il faudrait adapter un peu l'activité. 
Le fonctionnement général de l'activité est de créer un canal radio qui permettra aux utilisateurs de s'échanger des messages qui pourront être affichés sur le Micro:bit.


## Étape 1

> ***Astuce*** : Si les instructions prennent trop de place à l'écran, simplement cliquer sur le bouton "Moins..." en gris au centre entre la fenêtre d'instruction et l'espace de programmation.

La première chose à faire est d'initialiser la radio.

1. Aller dans la section ``||radio:radio||`` pour trouver le bloc ``||radio:définir groupe||``, puis le mettre dans le bloc ``||basic:au démarrage||``.
2. Attribuer la valeur de votre numéro de groupe au bloc ``||radio:définir groupe||``. Si une autre équipe a la même valeur de groupe, vos messages seront mélangés, ce qui va nuire à votre mission.

>**À noter! Il arrive que les images de la bulle d'aide soient différentes de ce que l'on retrouve dans l'espace de programmation : couleurs différentes, noms en anglais, noms de variables différents des instructions, etc. Pas de problème, il s'agit simplement d'un caprice d'affichage de la plateforme MakeCode que vous pouvez ignorer.**

<img alt="Activité 3 Relais Étape 1" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Relais_01.gif" width="80%">

```blocks
radio.setGroup(3)
```

## Étape 2

Lorsqu'une donnée est reçue, nous voulons la voir affichée.

1. Toujours dans la section ``||radio:radio||``, trouver le bloc ``||radio:quand une donnée est reçue par radio||`` et le glisser dans la page de programmation.
2. Ensuite, aller dans ``||basic:base||`` pour trouver le bloc ``||basic:Afficher texte||``, et le mettre dans le bloc ``||radio:radio||`` que l'on vient d'ajouter.
3. Puis, glisser-déposer receivedString dans ``||basic:afficher texte||``.

refaire le gif
<img alt="Activité 3 Relais Étape 2" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Relais_02.gif" width="80%">

```blocks
radio.onReceivedValue(function (receivedString) {
    basic.showString(receivedString)
})
```

## Étape 3

Nous allons maintenant programmer les messages à envoyer

1. Dans la section ``||input:entrée||``, selectionner ``||input:Lorsque le bouton A est pressé||`` et glisser le dans la page de programmation.
2. Dupliquer le bloc et changer ``||input:A||`` par ``||input:B||``.
3. Dans la section ``||radio:radio||``, glisser-déposer ``||radio:envoyer la chaine "" par radio||`` dans le crochet ``||input:losrque le bouton A est pressé||``
4. Reperter cette action pour le deuxième crochet ``||input:losrque le bouton B est pressé||``


<img alt="Activité 3 Relais Étape 3" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Relais_03.gif" width="80%">

```blocks
input.onButtonPressed(Button.A, function () {
    radio.sendString("")
})
input.onButtonPressed(Button.B, function () {
    radio.sendString("")
})

```

## Étape 4

À vous de choisir quels messages envoyer à vos amis

1. Inscrir le message que vous désirez envoyer par radio
2. Faites un premier test en téléversant le code une premiere fois sur le microbit.

Si ça fonctionne, alors nous allons pouvoir passer à l'étape suivante

Si vous avez besoin de vous rafraîchir la mémoire au sujet du téléversement du code, [voyez ici la vidéo aide-mémoire](https://youtu.be/H8utNPE3sJo) par GénieLab, et [voici la procédure détaillée](https://makecode.microbit.org/device/usb) dans la documentation de MakeCode (en anglais seulement).

<img alt="Activité 3 Relais Étape 4" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Relais_04.gif" width="80%">

```blocks
input.onButtonPressed(Button.A, function () {
    radio.sendString("Message 1")
})
input.onButtonPressed(Button.B, function () {
    radio.sendString("Message 2")
})
```

## Étape 5

Dans cette deuxième partie nous allons Utiliser le panneau solaire  pour envoyer un message à un autre microbit s'il fait soleil
1. Dans la section ``||variable:variables||`` cliquer sur créer une variable, créer les variables ``||variable:Solaire||`` et ``||variable:Volt||``.
2. Glisser-deposer ``||variable:définir 'Solaire' à '0'||`` dans le crochet ``basic:toujours||``.

**Note: si le crochet ``||basic:toujours||`` ne se trouve pas dans la bage de programmation, vous pouvez le trouver dans la section ``||basic:Base||``.**
1. Dans ``||input:entrée||``, prendre le bloc ``||input:lorsque le bouton A est pressé||``.
2. Y insérer le bloc ``||radio:envoyer la valeur "" = 0 par radio||``.
3. Inscrire "terre" à gauche du "=", et laisser le chiffre à 0.

<img alt="Activité 3 Relais Étape 5" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Relais_05.gif" width="80%">

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

<img alt="Activité 3 Relais Étape 6" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Relais_06.gif" width="80%">

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

<img alt="Activité 3 Relais Étape 7" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Relais_07.gif" width="80%">

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

<img alt="Activité 3 Relais Étape 8" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Relais_08.gif" width="80%">

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