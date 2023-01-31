# Rosy, Activité 3 : Communication Radio : Multiplayer

## Présentation 1 @showdialog

Le but de l'activité est de se familiariser avec la communication radio. 
Cette activité se fait en équipe de deux, cependant il y a la possibilité de le faire à plus mais il faudrait adapter un peu l'activité. 
Le fonctionnement général de l'activité est de créer un canal radio qui permettra aux utilisateurs de s'échanger des messages qui pourront être affichés sur le Micro:bit.


## Étape 1

> ***Astuce*** : Si les instructions prennent trop de place à l'écran, simplement cliquer sur le bouton "Moins..." en gris au centre entre la fenêtre d'instruction et l'espace de programmation.

La première chose à faire est d'initialiser la radio.

1. Aller dans la section ``||radio:radio||`` pour trouver le bloc ``||radio:radio définir groupe '1'||``, puis le mettre dans le crochet ``||basic:au démarrage||``.
2. Attribuer la valeur de votre numéro de groupe au bloc ``||radio:radio définir groupe '1'||``. Si une autre équipe a la même valeur de groupe, vos messages seront mélangés, ce qui va nuire à votre mission.

>**À noter! Il arrive que les images de la bulle d'aide soient différentes de ce que l'on retrouve dans l'espace de programmation : couleurs différentes, noms en anglais, noms de variables différents des instructions, etc. Pas de problème, il s'agit simplement d'un caprice d'affichage de la plateforme MakeCode que vous pouvez ignorer.**

<img alt="Activité 3 Relais Étape 1" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Relais_01.gif" width="80%">

```blocks
radio.setGroup(3)
```

## Étape 2

Lorsqu'une donnée est reçue, nous voulons la voir affichée.

1. Toujours dans la section ``||radio:radio||``, trouver le bloc ``||radio:quand une donnée est reçue par radio 'receivedString'||`` et le glisser dans la page de programmation.
2. Ensuite, aller dans ``||basic:base||`` pour trouver le bloc ``||basic:Afficher texte||``, et le mettre dans le crochet du bloc ``||radio:quand une donnée est reçue par radio 'receivedString'||`` que l'on vient d'ajouter.
3. Puis, glisser-déposer ``||radio:receivedString||`` dans ``||basic:afficher texte||``.

refaire le gif
<img alt="Activité 3 Relais Étape 2" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Relais_02.gif" width="80%">

```blocks
radio.onReceivedString(function (receivedString) {
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

1. Inscrire le message que vous désirez envoyer par radio
2. Faites un premier test en téléversant le code une premiere fois sur le microbit.

Si ça fonctionne, alors nous allons pouvoir passer à l'étape suivante

Si vous avez besoin de vous rafraîchir la mémoire au sujet du téléversement du code, [voyez ici la vidéo aide-mémoire](https://youtu.be/H8utNPE3sJo) par GénieLab, et [voici la procédure détaillée](https://makecode.microbit.org/device/usb) dans la documentation de MakeCode (en anglais seulement).

```blocks
input.onButtonPressed(Button.A, function () {
    radio.sendString("Message 1")
})
input.onButtonPressed(Button.B, function () {
    radio.sendString("Message 2")
})
```

## Étape 5

Dans cette deuxième partie nous allons Utiliser le panneau solaire  pour envoyer un message à un autre microbit s'il fait soleil.
1. Dans la section ``||variable:variables||`` cliquer sur créer une variable, créer les variables ``||variable:Volt||`` et ``||variable:Solaire||``.
2. Glisser-deposer ``||variable:définir 'Solaire' à '0'||`` dans le crochet ``||basic:toujours||``.
3. Faire la même chose pour la variable ``||variable:Volt||``.

*Note: si le crochet ``||basic:toujours||`` ne se trouve pas dans la bage de programmation, vous pouvez le trouver dans la section ``||basic:Base||``.*

<img alt="Activité 3 Relais Étape 5" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Relais_05.gif" width="80%">

```blocks
basic.forever(function () {
    Solaire = 0
    Volt = 0
})
```

## Étape 6
Nous récupérons les données du paneau solaire. 

1. Cliquer sur avancé, puis dans la section ``||pins:broches||``, glisser-déposer ``||pins:lire la broche analogique P0||`` dans ``||variable:définir 'Solaire' à '0'||`` à la place du 0.

2. Dans la section ``||Maths:Maths||``, glisser-déposer ``||Math:'0'/'0'||`` dans l'espace de programmation.
3. Nous allons diviser ``||variable:Solaire||`` par 303 et attribuer la valeur à ``||variable:Volt||``
4. Dans la section ``||variable:variables||`` glisser-déposer ``||variable:Solaire||`` à gauche du calcul ``||Math:'0'/'0'||``
3. Remplacer le ``||Math:'0'||`` de gauche par ``||Math:303||``
4. Glisser le calcul à la place du '0' dans ``||variable:définir Volt à '0'||``

<img alt="Activité 3 Relais Étape 6" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Relais_06.gif" width="80%">

```blocks
basic.forever(function () {
    Solaire = pins.analogReadPin(AnalogPin.P0)
    Volt = Solaire / 303
})
```

## Étape 7

Nous allons envoyer un message si il y a du soleil

1. Dans la section ``||logic:logique||`` selectionner ``||logic:si vrai alors||`` et le glisser sous la définition des deux ``||variable:variables||`` dans le crochet ``||basic:toujours||``
2. Dans le crochet ``||logic:si vrai alors||``, y glisser ``||radio:envoyer la chaine " " par radio||`` que vous trouverez sous la section ``||radio:radio||``
3. Inscrire "Soleil" dans ``||radio:envoyer la chaine "Soleil" par radio||``

<img alt="Activité 3 Relais Étape 7" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Relais_07.gif" width="80%">

```blocks
basic.forever(function () {
    Solaire = pins.analogReadPin(AnalogPin.P0)
    Volt = Solaire / 303
    if (true) {
        radio.sendString("Soleil")
    }
})
```

## Étape 8 

Nous allons maintenant ajouté la condition pour envoyer le message "soleil".

1. Dans la section ``||logic:logique||``, glisser-déposer ``||logic:"0"<"0"||`` à la place de ``||logic:vrai||``.
2. Dans la condition, remplacer le "0" de gauche par la variable ``||variable:Volt||`` que vous trouverez dans la section ``||variable:variables||``
3. Remplacer le "0" de droite par "2"
4. Changer le signe ``||logic:<||`` par ``||logic:>||``.

5. Ajouter une ``||basic:pause||`` de 100ms à la fin du crochet ``||basic:toujours||`` que vous trouverez dans la section ``||basic:base||``.

<img alt="Activité 3 Relais Étape 8" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Relais_08.gif" width="80%">

```blocks
basic.forever(function () {
    Solaire = pins.analogReadPin(AnalogPin.P0)
    Volt = Solaire / 303
    if (Volt > 2) {
        radio.sendString("Soleil")
    }
    basic.pause(100)
})
```
## Étape 9 

Nous allons rendre ça plus jolie en affichant un soleil plutôt que de faire defiler le mot au complet.

Je te laisse trouver la solution!!

*Ps: la réponse se trouve à la prochaine étape.*

## Étape 10

L'une des solutions possible est la suivante:

1. Dans la section ``||logic:logique||``, glisser-déposer ``||logic:si vrai alors sinon||`` dans le crochet ``||radio:quand une donnée est reçue par radio||`` 
2. Glisser-déposer ``||basic:afficher texte||`` dans le crochet ``||logic:sinon||``
3. Glisser-déposer ``||basic:montrer LEDs||`` dans le crochet ``||logic:si vrai alors||`` et y dessiner un soleil.
4. Dans la section ``||logic:logique||`` glisser-déposer ``||logic:"" = ""||`` à la place de ``||logic:vrai||`` dans la condition ``||logic:si vrai alors||``
5. Glisser-déposer ``||radio:receivedString||`` à gauche de ``||logic:"" = ""||`` et ecrire Soleil à droite de ``||logic:"" = ""||``

```blocks
radio.onReceivedString(function (receivedString) {
    if (receivedString == "Soleil") {
        basic.showLeds(`
            . . # . .
            . # # # .
            # # # # #
            . # # # .
            . . # . .
            `)
    } else {
        basic.showString(receivedString)
    }
})
```
## Étape 11 @showhint

Voilà, le code est maintenant prêt! Le voici au complet. N'oubliez pas de faire dérouler l'image d'aide vers le bas pour le voir au complet.

```blocks
radio.setGroup(1)

basic.forever(function () {
    Solaire = pins.analogReadPin(AnalogPin.P0)
    Volt = Solaire / 303
    if (Volt > 2) {
        radio.sendString("Soleil")
    }
    basic.pause(100)
})
input.onButtonPressed(Button.A, function () {
    radio.sendString("Message 1")
})
input.onButtonPressed(Button.B, function () {
    radio.sendString("Message 2")
})
radio.onReceivedString(function (receivedString) {
    if (receivedString == "Soleil") {
        basic.showLeds(`
            . . # . .
            . # # # .
            # # # # #
            . # # # .
            . . # . .
            `)
    } else {
        basic.showString(receivedString)
    }
})
```

## Étape 12

Il ne reste qu'à téléverser le code sur le micro:bit, et vous êtes prêt·e.

Si vous avez besoin de vous rafraîchir la mémoire au sujet du téléversement du code, [voyez ici la vidéo aide-mémoire](https://youtu.be/H8utNPE3sJo) par GénieLab, et [voici la procédure détaillée](https://makecode.microbit.org/device/usb) dans la documentation de MakeCode (en anglais seulement).

