# Rosy, Activité préparatoire : Premiers pas avec le micro:bit 2

## Objectif @showdialog

Continuons de découvrir les différentes fonctionnalités du micro:bit. Au cours de ce second tutoriel, nous allons faire afficher des DEL (aussi appelées LED en anglais) plus ou moins rapidement en fonction de la luminosité détectée.


## Étape 1

Commençons par **créer une fonction**, qui est un bloc de code que l'on peut facilement réutiliser.

1. **Cliquer** sur la section **Avancé**.
2. Dans la section ``||functions:Fonctions||``, **cliquer** sur "**Créer une fonction...**".
3. Dans le panneau qui apparait, **nommer** votre fonction "**animationDEL**".
4. **Cliquer** sur "**Nombres**".
5. **Cliquer** sur le bouton vert "**Terminé**".

<!-- <img alt="Animation de l'assemblage des blocs de programmation de l'étape 12." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_01/Rosy_Act1_07.gif" width="80%"> -->

```blocks
function animationDEL (num: number) {
    
}
```


## Étape 2

Créons une boucle pour faire afficher les DEL **les unes après les autres**.

1. Dans la section ``||loops:Boucles||``, **choisir** ``||loops:pour index variant de 0 à 4 faire||`` et le **glisser** dans la fonction.


```blocks
function animationDEL (num: number) {
    for (let index = 0; index <= 4; index++) {

    }
}
```


## Étape 3

Affichons une DEL pour un certain temps avant de l'effacer.

1. Dans la section ``||led:LED||``, **choisir** ``||led:allumer x 0 y 0||`` et le **glisser** dans la boucle.
2. Dans la section ``||basic:Base||``, **trouver** ``||basic:pause (ms)||`` et le **glisser** à la suite.
3. Toujours dans la section ``||basic:Base||``, **trouver** ``||basic:effacer l'écran||`` et le **glisser** sous ``||basic:pause (ms)||``.


```blocks
function animationDEL (num: number) {
    for (let index = 0; index <= 4; index++) {
        led.plot(0, 0)
        basic.pause(200)
        basic.clearScreen()
    }
}
```


## Étape 4

À chaque boucle, changer de DEL à illuminer. Aussi, faire en sorte qu'on peut controller le temps entre chaque cycle de la boucle. 

1. **glisser** la variable ``||variable:index||`` de la boucle et **l'ajouter** dans la case "x" du bloc ``||led:allumer x 0 y 0||``.
2. **glisser** la variable ``||variable:num||``  qui se trouve à droite dans le bloc fonction animationDEL et **l'ajouter** dans le bloc ``||basic:pause (ms)||``.


```blocks
function animationDEL (num: number) {
    for (let index = 0; index <= 4; index++) {
        led.plot(index, 0)
        basic.pause(num)
        basic.clearScreen()
    }
}
```


## Étape 5

La **vitesse de défilement** des DEL va varier en fonction de l'éclairage détecté par le micro:bit. Le niveau d'éclairage détecté est rapporté par le micro:bit comme un nombre entre 0 (noir complet) et 255 (très lumineux).

1. Dans la section ``||logic:Logique||``, **choisir** ``||logic:si <vrai> alors ... sinon||`` et le **glisser** dans ``||basic:toujours||``.
2. Toujours dans la section ``||logic:Logique||``, **choisir** ``||logic:<0> < <0>||`` (plus petit que) et le **glisser** à la place du ``||logic:vrai||``.
3. Dans ``||input:Entrée||``, **trouver** ``||input:niveau d'intensité lumineuse||`` et **l'ajouter** à la gauche sur symbole ``||logic:<||`` (plus petit que).
4. À la droite du symbole ``||logic:<||``, **inscrire 128**.


```blocks
basic.forever(function () {
    if (input.lightLevel() < 128) {
        
    } else {
        
    }
})
```


## Étape 6

Utilisons notre fonction ``||functions:animationDEL||`` pour faire **afficher les DEL en fonction de la luminosité**.

1. Dans la section ``||functions:Fonctions||``, **choisir** ``||functions:appel animationDEL 1||`` et le **glisser** dans la portion ``||logic:si||`` de notre condition.
2. **Remplacer** le "1" par "300" dans le cercle blanc de la ``||functions:fonction||``.
3. **Dupliquer** la ``||functions:fonction||``, et **l'ajouter** dans la portion ``|logic:sinon||``.
4. **Remplacer** le "300" par "50" dans le cercle blanc.


```blocks
basic.forever(function () {
    if (input.lightLevel() < 128) {
        animationDEL(300)
    } else {
        animationDEL(50)
    }
})
```


## Étape 7 @showdialog

Et voilà! Il ne reste plus qu'à **téléverser** le code sur le micro:bit. **Les instructions pour la suite sont à la prochaine étape de l'activité**.

1. **Connecter le micro:bit** à votre ordinateur avec le câble USB fourni dans la trousse.
2. **Télécharger votre code** avec le bouton Télécharger en bas à gauche de l'écran.
3. Dans le gestionnaire de fichiers de votre ordinateur, **glisser le fichier téléchargé** vers le micro:bit
4. Durant le transfert, la DEL orange au dos du micro:bit va clignoter rapidement. Une fois que c'est terminé, **votre code est sur l'appareil**.

[Voyez ici la vidéo aide-mémoire](https://youtu.be/H8utNPE3sJo) par GénieLab, et [voici la procédure détaillée](https://makecode.microbit.org/device/usb) dans la documentation de MakeCode (en anglais seulement).


## Étape 8 @showdialog

L'animation sur l'écran du micro:bit va changer de vitesse en fonction de la luminosité détectée. Il est important de savoir que les DEL servent à la fois à émettre de la lumière, et à détecter la lumière ambiante! Faites varier la lumière dirigée sur les DEL pour voir le résultat. Pour aller plus loin, vous pouvez :

1. Modifier les valeurs du seuil de luminosité et de vitesse d'affichage dans nos conditions.
2. Faire varier l'animation en modifiant où la ``||variable:variable index||`` de la boucle est placée.
3. Ajouter d'autres conditions au bloc ``||logic:si ... sinon||`` pour ajouter plus de variété.
4. Combiner les différents senseurs et boutons dans les conditions avec le bloc ``||logic:<> et <>||``.

Cliquez sur "Terminé à droite de cette barre pour avoir accès à tous les blocs de programmation.