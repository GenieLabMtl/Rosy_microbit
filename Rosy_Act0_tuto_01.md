# Rosy, Activité préparatoire : Premiers pas avec le micro:bit – 1

## Objectif @showdialog

Découvrons ensemble comment programmer le micro:bit. Au cours de ce tutoriel, nous allons faire afficher différentes images à l'écran en fonction de l'orientation et des boutons pressés sur l'appareil.

Lorsque le micro:bit démarre, nous allons afficher un texte déroulant suivi d'une image. Ensuite, l'image affichée dépendra de nos actions.


## Étape 1

Lorsque le micro:bit démarre, **affichons un texte déroulant**.

> ***Astuce*** : En cliquant avec le bouton de droite sur un bloc et en choisissant "Aide", vous pouvez voir une rubrique d'aide qui explique son fonctionnement (en anglais seulement).

> ***Astuce 2*** : Si les instructions occupent trop de place à l'écran, simplement cliquer sur le bouton "Moins..." en gris au centre entre la fenêtre d'instruction et l'espace de programmation.

> ***Astuce 3*** : En cliquant sur l'ampoule dans le cercle bleu à droite de ce texte, vous pouvez voir le résultat de l'étape en cours.


1. Trouver le bloc ``||basic:afficher texte||`` dans la section ``||basic:Base||``.
2. Le glisser dans le crochet ``||basic:au démarrage||`` dans la surface de programmation.
3. Dans le cercle blanc du bloc ``||basic:afficher texte||``, écrire "Rosy!".

<!-- <img alt="Animation de l'assemblage des blocs de programmation de l'étape 12." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_01/Rosy_Act1_07.gif" width="80%"> -->

```blocks
basic.showString("Rosy!")
```


## Étape 2

Ensuite, **affichons une image pendant 2 secondes** avant de continuer le programme.

1. Trouver le bloc ``||basic:montrer LEDs||`` dans la section ``||basic:Base||``.
2. Le glisser sous le bloc ``||basic:afficher texte||`` de l'étape précédente.
3. Y dessiner le visage de Rosy qui sourit en cliquant dans les cases de ``||basic:montrer LEDs||``.
4. Trouver ``||basic:pause (ms)||`` dans la section ``||basic:Base||``.
5. Le glisser à la suite du bloc ``||basic:montrer LEDs||``.
6. Cliquer sur le cercle blanc où il est inscrit "100", et choisir "2 secondes".

```blocks
basic.showString("Rosy!")
basic.showLeds(`
    . # . # .
    . # . # .
    . . . . .
    # . . . #
    . # # # .
    `)
basic.pause(2000)
```


## Étape 3

Dans la boucle principale de notre programme, nous allons **mettre des conditions**.

1. Trouver le bloc ``||logic:si <vrai> alors||`` dans la section ``||logic:Logique||``.
2. Le glisser dans le crochet ``||basic:toujours||`` dans la surface de programmation.
3. Cliquer 3 fois sur le symbole "+" au bas de ``||logic:si <vrai> alors||``.

```blocks
basic.forever(function () {
    if (true) {
        
    } else if (false) {
        
    } else if (false) {
        
    } else {
        
    }
})
```


## Étape 4

La première condition ve être déclenchée si le micro:bit est **secoué**.

1. Trouver le bloc ``||input:geste secouer est actif||`` dans la section ``||input:Entrée||``.
2. Le glisser à la place du premier ``||logic:vrai||``.
3. Dans cette première condition, ajouter un bloc ``||basic:montrer LEDs||``.
4. Y dessiner un visage surpris.

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

La deuxième condition ve être déclenchée si le micro:bit **incliné vers la droite**.

1. Faire clique droit sur ``||input:geste secouer est actif||`` de la première condition et cliquer sur "Dupliquer".
2. Glisser le bloc ``||input:geste secouer est actif||`` qui vient d'apparaitre à la prochaine condition ``||logic:sinon si <> alors||``.
3. Ajouter un bloc ``||basic:montrer LEDs||`` dans cette condition, et y dessiner un visage souriant.
4. Ajouter un bloc ``||basic:pause (ms)||`` à la suite, et lui attribuer la valeur "200".
5. Mettre un bloc ``||basic:montrer LEDs||`` sous ``||basic:pause (ms)||``, et y dessiner un visage regardant à droite.

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


## Étape 6

La troisième condition ve être déclenchée lorsque le **bouton A est pressé**.

1. Trouver le bloc ``||input:bouton A est pressé||`` dans la section ``||input:Entrée||``.
2. Le glisser à la troisième condition.
3. Trouver ``||basic:montrer l'icône||`` dans ``||basic:Base||`` et le mettre dans cette condition.
4. Choisir l'image du crochet.

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


## Étape 7

La dernière condition est toujours déclenchée lorsqu'**aucune des conditions précédentes** n'est remplie.

1. Dupliquer le bloc ``||basic:montrer l'icône||`` et le mettre sous ``||logic:sinon||``.
2. Choisir l'image du du visage endormi.

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


## Étape 8 @showdialog

Et voilà! Il ne reste plus qu'à **téléverser** le code sur le micro:bit. **Les instructions pour la suite sont à la prochaine étape de l'activité**.

1. **Connecter le micro:bit** à votre ordinateur avec le câble USB fourni dans la trousse.
2. **Télécharger votre code** avec le bouton Télécharger en bas à gauche de l'écran.
3. Dans le gestionnaire de fichiers de votre ordinateur, **glisser le fichier téléchargé** vers le micro:bit.
4. Durant le transfert, la DEL orange au dos du micro:bit va clignoter rapidement. Une fois que c'est terminé, **votre code est sur l'appareil**.

[Voyez ici la vidéo aide-mémoire](https://youtu.be/H8utNPE3sJo) par GénieLab, et [voici la procédure détaillée](https://makecode.microbit.org/device/usb) dans la documentation de MakeCode (en anglais seulement).


## Étape 9 @showdialog

Vous pouvez maintenant **faire réagir Rosy** à l'aide du programme que nous avons mis sur le micro:bit. Pour continuer de vous familiariser avec cet environnement de programmation, vous pouvez :

1. Remplacer les conditions par d'autres types de manipulation.
2. Changer le type d'affichage.
3. Explorer les différents types de capteurs embarqués sur le micro:bit dans la section ``||input:Entrée||``.

Cliquez sur "Terminé à droite de cette barre pour avoir accès à tous les blocs de programmation.

