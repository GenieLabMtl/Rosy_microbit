# Rosy, Activité préparatoire : Premiers pas avec le micro:bit – 1

## Objectif @showdialog

Découvrons ensemble comment programmer le micro:bit. Au cours de ce tutoriel, nous allons faire afficher différentes images à l'écran en fonction de l'orientation et des boutons pressés sur l'appareil.

Lorsque le micro:bit démarre, nous allons afficher un texte déroulant suivi d'une image. Ensuite, l'image affichée dépendra de nos actions.


## Étape 1

Lorsque le micro:bit démarre, **affichons un texte déroulant**.

> ***Astuce*** : En cliquant avec le bouton de droite sur un bloc et en choisissant "Aide", vous pouvez voir une rubrique d'aide qui explique son fonctionnement (en anglais seulement).

> ***Astuce 2*** : Si les instructions occupent trop de place à l'écran, simplement cliquer sur le bouton "Moins..." en gris au centre entre la fenêtre d'instruction et l'espace de programmation.

> ***Astuce 3*** : En cliquant sur l'ampoule dans le cercle bleu à droite de ce texte, vous pouvez voir le résultat de l'étape en cours.


1. **Trouver** le bloc ``||basic:afficher texte||`` dans la section ``||basic:Base||``.
2. Le **glisser** dans le crochet ``||basic:au démarrage||`` dans la surface de programmation.
3. Dans le cercle blanc du bloc ``||basic:afficher texte||``, **écrire** "Rosy!".

<!-- <img alt="Animation de l'assemblage des blocs de programmation de l'étape 12." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_01/Rosy_Act1_07.gif" width="80%"> -->

```blocks
basic.showString("Rosy!")
```


## Étape 2

Dans la boucle principale de notre programme, nous allons **mettre des conditions**.

1. **Trouver** le bloc ``||logic:si <vrai> alors||`` dans la section ``||logic:Logique||``.
2. Le **glisser** dans le crochet ``||basic:toujours||`` dans la surface de programmation.
3. **Cliquer 3 fois** sur le symbole ``||logic:+||`` au bas de ``||logic:si <vrai> alors||``.

```blocks
basic.forever(function () {
    if (true) {
        
    } else if (false) {
        
    } else if (false) {
        
    } else {
        
    }
})
```


## Étape 3

La première condition ve être déclenchée si le micro:bit est **secoué**.

1. **Trouver** le bloc ``||input:geste secouer est actif||`` dans la section ``||input:Entrée||``.
2. Le **glisser** à la place du premier ``||logic:vrai||``.

```blocks
basic.forever(function () {
    if (input.isGesture(Gesture.Shake)) {

    } else if (false) {
        
    } else if (false) {
        
    } else {
        
    }
})
```


## Étape 4

Affichons un visage surpris pour la condition que nous venons de créer.

1. **Trouver** le bloc ``||basic:montrer LEDs||``, dans la section ``||basic:Base||``.
2. Le **glisser** dans la condition que nous venons de créer.
3. **Y dessiner** un visage surpris.

```blocks
basic.forever(function () {
    if (input.isGesture(Gesture.Shake)) {
        basic.showLeds(`
            # . . . #
            . . . . .
            . . # . .
            . # . # .
            . . # . .
            `)
    } else if (false) {
        
    } else if (false) {
        
    } else {
        
    }
})
```


## Étape 5

La deuxième condition va être déclenchée si le micro:bit est **incliné vers la droite**.

1. Faire **clique droit** sur ``||input:geste secouer est actif||`` de la première condition et cliquer sur "**Dupliquer**".
2. **Glisser** le nouveau bloc ``||input:geste secouer est actif||`` dans la prochaine condition ``||logic:sinon si <> alors||``.
3. **Changer l'action** ``||input:secouer||`` pour ``||input:incliné à droite||``.

```blocks
basic.forever(function () {
    if (input.isGesture(Gesture.Shake)) {
        basic.showLeds(`
            # . . . #
            . . . . .
            . . # . .
            . # . # .
            . . # . .
            `)
    } else if (input.isGesture(Gesture.TiltRight)) {

    } else if (false) {
        
    } else {
        
    }
})
```


## Étape 6

Afficher une animation lorsque le micro:bit est **incliné vers la droite**.

1. **Ajouter** un bloc ``||basic:montrer LEDs||`` dans cette 2e condition, et **y dessiner** un visage surpris.
2. Dans la section ``||basic:Base||``, **trouver** le bloc ``||basic:pause (ms)||`` et le **glisser** à la suite.
3. **Attribuer** la valeur ``||basic:200||`` au bloc ``||basic:pause (ms)||``.
3. **Ajouter** un autre bloc ``||basic:montrer LEDs||`` sous ``||basic:pause (ms)||``, et **y dessiner** un visage regardant à droite.

```blocks
basic.forever(function () {
    if (input.isGesture(Gesture.Shake)) {
        basic.showLeds(`
            # . . . #
            . . . . .
            . . # . .
            . # . # .
            . . # . .
            `)
    } else if (input.isGesture(Gesture.TiltRight)) {
        basic.showLeds(`
            . . . . .
            . # . # .
            . . . . .
            # . . . #
            . # # # .
            `)
        basic.pause(200)
        basic.showLeds(`
            . . . . .
            . . # . #
            . . . . .
            # . . . #
            . # # # .
            `)
    } else if (false) {
        
    } else {
        
    }
})
```


## Étape 7

La troisième condition ve être déclenchée lorsque le **bouton A est pressé**.

1. **Trouver** le bloc ``||input:bouton A est pressé||`` dans la section ``||input:Entrée||``.
2. **Glisser** le bloc à la troisième condition.

```blocks
basic.forever(function () {
    if (input.isGesture(Gesture.Shake)) {
        basic.showLeds(`
            # . . . #
            . . . . .
            . . # . .
            . # . # .
            . . # . .
            `)
    } else if (input.isGesture(Gesture.TiltRight)) {
        basic.showLeds(`
            . . . . .
            . # . # .
            . . . . .
            # . . . #
            . # # # .
            `)
        basic.pause(200)
        basic.showLeds(`
            . . . . .
            . . # . #
            . . . . .
            # . . . #
            . # # # .
            `)
    } else if (input.buttonIsPressed(Button.A)) {

    } else {
        
    }
})
```


## Étape 8

Afficher une image prédéfinie quand le **bouton A est pressé**.

3. **Trouver** ``||basic:montrer l'icône||`` dans ``||basic:Base||`` et le mettre dans cette condition.
4. **Choisir** l'image du crochet.

```blocks
basic.forever(function () {
    if (input.isGesture(Gesture.Shake)) {
        basic.showLeds(`
            # . . . #
            . . . . .
            . . # . .
            . # . # .
            . . # . .
            `)
    } else if (input.isGesture(Gesture.TiltRight)) {
        basic.showLeds(`
            . . . . .
            . # . # .
            . . . . .
            # . . . #
            . # # # .
            `)
        basic.pause(200)
        basic.showLeds(`
            . . . . .
            . . # . #
            . . . . .
            # . . . #
            . # # # .
            `)
    } else if (input.buttonIsPressed(Button.A)) {
        basic.showIcon(IconNames.Yes)
    } else {
        
    }
})
```


## Étape 9

La dernière condition est toujours déclenchée lorsqu'**aucune des conditions précédentes** n'est remplie.

1. **Dupliquer** le bloc ``||basic:montrer l'icône||`` et le déplacer sous ``||logic:sinon||``.
2. **Choisir** l'image du du visage endormi.

```blocks
basic.forever(function () {
    if (input.isGesture(Gesture.Shake)) {
        basic.showLeds(`
            # . . . #
            . . . . .
            . . # . .
            . # . # .
            . . # . .
            `)
    } else if (input.isGesture(Gesture.TiltRight)) {
        basic.showLeds(`
            . . . . .
            . # . # .
            . . . . .
            # . . . #
            . # # # .
            `)
        basic.pause(200)
        basic.showLeds(`
            . . . . .
            . . # . #
            . . . . .
            # . . . #
            . # # # .
            `)
    } else if (input.buttonIsPressed(Button.A)) {
        basic.showIcon(IconNames.Yes)
    } else {
        basic.showIcon(IconNames.Asleep)
    }
})
```


## Étape 10 @showdialog

Et voilà! Il ne reste plus qu'à **téléverser** le code sur le micro:bit. **Les instructions pour la suite sont à la prochaine étape de l'activité**.

1. **Connecter le micro:bit** à votre ordinateur avec le câble USB fourni dans la trousse.
2. **Télécharger votre code** avec le bouton Télécharger en bas à gauche de l'écran.
3. Dans le gestionnaire de fichiers de votre ordinateur, **glisser le fichier téléchargé** vers le micro:bit.
4. Durant le transfert, la DEL orange au dos du micro:bit va clignoter rapidement. Une fois que c'est terminé, **votre code est sur l'appareil**.

[Voyez ici la vidéo aide-mémoire](https://youtu.be/H8utNPE3sJo) par GénieLab, et [voici la procédure détaillée](https://makecode.microbit.org/device/usb) dans la documentation de MakeCode (en anglais seulement).


## Étape 11 @showdialog

Vous pouvez maintenant **faire réagir Rosy** à l'aide du programme que nous avons mis sur le micro:bit. Pour continuer de vous familiariser avec cet environnement de programmation, vous pouvez :

1. Remplacer les conditions par d'autres types de manipulation.
2. Changer le type d'affichage.
3. Explorer les différents types de capteurs embarqués sur le micro:bit dans la section ``||input:Entrée||``.

Cliquez sur "Terminé à droite de cette barre pour avoir accès à tous les blocs de programmation.