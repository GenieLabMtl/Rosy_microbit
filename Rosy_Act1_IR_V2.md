# Rosy, Activité 1 : télescope infrarouge v2

## Objectif 

Dans ce premier défi, nous allons créer un **modèle réduit de télescope à infrarouge**.

Nous serons en mesure de **détecter la présence d'une source de chaleur** dans l'axe du télescope, et de représenter visuellement la température observée afin de **détecter la présence d'exoplanètes**.

<img alt="Résultat attendu de l'activité : le micro:bit affiche la valeur lue par le capteur infrarouge." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_01/gifactivite1_v3.gif" width="300px">


## Matériel 

Voici le matériel dont nous aurons besoin :
    - Un micro:bit
    - Un câble USB
    - Le circuit imprimé
    - Le capteur infrarouge MLX90614
<img alt="microcontrôleur micro:bit, câble USB, circuit imprimé, capteur infrarouge MLX90614" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_01/Act1PictMatos.jpg" width="300px">


## Étape 1


Le capteur infrarouge [MLX90614](https://www.melexis.com/en/product/mlx90614/digital-plug-play-infrared-thermometer-to-can) permet de **lire la température** ambiante et la température d'un objet en face du capteur. La version que nous utilisons a **une portée utile d'environ 30 cm**.

Insérer les 4 pattes du capteur infrarouge MLX90614 dans 4 rangées numérotées différentes de la platine de prototypage.

<img alt="Le micro:bit s'insère dans la carte de développement de façon à ce que les boutons A et B du micro:bit soient du même côté que les connecteurs de la carte." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_01/Act1pict3IR_v2_600px.jpg" width="300px">


## Étape 2 

Insérer le micro:bit dans la carte de développement.

<img alt="Les pattes du capteur s'insèrent dans la platine de prototypage de sorte à ce que le capteur soit du côté extérieure de la platine, dégageant ainsi les autres trous des 4 rangées où il est connecté." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_01/Act1Pict2IR_v3.jpg" width="300px">


## Étape 5 

Voilà! Le circuit est aussi simple que ça! **Maintenant, allons programmer** le micro:bit pour qu'il puisse communiquer avec le capteur.

<img alt="Les connexions entre le capteur infrarouge et la carte de développement complète ce circuit simple." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_01/Act1Pict5IR_v2.jpg" width="300px">


## Étape 6

Commençons par **définir une variable** pour stocker la température de l'objet dans le champ de vision du capteur.

> ***Rappel*** : En cliquant avec le bouton de droite sur un bloc et en choisissant "Aide", vous pouvez voir une rubrique d'aide qui explique son fonctionnement (en anglais seulement).

> ***Rappel 2*** : Si les instructions prennent trop de place à l'écran, simplement cliquer sur le bouton "Moins..." en gris au centre entre la fenêtre d'instruction et l'espace de programmation.

> ***Rappel 3*** : En cliquant sur l'ampoule dans le cercle bleu à droite de ce texte, vous pouvez voir le résultat de l'étape en cours.

Aller dans la section ``||variables:Variables||`` et créer la variable "source".
Ensuite, glisser le bloc ``||variables:définir||`` dans le crochet ``||basic:Toujours||``

<img alt="Animation de la création d'une variable et de l'assemblage des blocs de programmation de l'étape 6." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_01/Rosy_Act1_01.gif" width="80%">

```blocks
let source = 0
basic.forever(function(){
    source = 0
})
```

## Étape 7

Ensuite, nous allons **lire le capteur** au moyen d'une [librairie sur mesure](https://github.com/GenieLabMtl/pxt-mlx90614-microbit) que nous avons déjà importée pour vous dans l'éditeur.

1. Trouver le bloc ``||Control:mesure temperature||`` dans la section ``||Control:MLX90614||`` et le glisser n'importe où dans la surface de programmation.
2. Refaire la même étape pour avoir 2 fois ce bloc de disponible.

> ***Astuce*** *: Au fil des étapes, vous pouvez cliquer sur l'ampoule bleue à droite de cette case pour voir le résultat de l'étape en cours, ainsi qu'une animation de ce qu'il faut faire.*

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 7." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_01/Rosy_Act1_02.gif" width="80%">


## Étape 8

Afin de représenter de façon significative la lecture de température sur l'écran du micro:bit, nous allons **établir la portée de la lecture** en fonction de l'affichage.
La valeur minimale de lecture est la température ambiante de la salle où vous vous trouvez.

1. Trouver le bloc ``||Math:projeter||`` dans la section ``||Math:Maths||`` et le glisser sur la surface de programmation.
2. Glisser ``||Control:mesure temperature||`` dans le premier cercle de ``||Math:projeter||`` et lui attribuer "Object" avec le menu déroulant.
3. Glisser l'autre ``||Control:mesure temperature||`` dans le second cercle de ``||Math:projeter||`` et lui attribuer "Ambient" avec le menu déroulant.

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 8." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_01/Rosy_Act1_03.gif" width="80%">


## Étape 9

Puisque le capteur retourne les températures en degrés Celsius, établissons la valeur maximale de captation à 35, ce qui est environ **la température de la paume d'une main**.
Pour illuminer l'écran du micro:bit, les valeurs de **0 à 50 nous donneront une bonne résolution**.

1. Dans le troisième cercle, inscrire le nombre 35.
2. Dans le quatrième cercle, inscrire le nombre 0.
3. Dans le dernier cercle, inscrire le nombre 50.

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 9." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_01/Rosy_Act1_04.gif" width="80%">


## Étape 10

Nous pouvons maintenant mettre ``||Math:projeter||`` dans le bloc ``||variables:définir||``.

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 10." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_01/Rosy_Act1_05.gif" width="80%">

```blocks
let source = 0
basic.forever(function () {
    source = Math.map(MLX90614.temperature(Environment.Object), MLX90614.temperature(Environment.Ambient), 35, 0, 50)
```


## Étape 11

Nous voulons que notre télescope **détecte une source de chaleur dans son axe**, puis qu'il affiche la lecture fine lorsque nous **appuyons sur le bouton "A"**.

Nous avons donc besoin d'un bloc conditionnel pour détecter **si le bouton est pressé ou non**.

1. Trouver le bloc ``||logic:si <vrai>...sinon||`` dans la section ``||logic:Logique||``.
2. Le glisser sous le bloc ``||variables:définir||``.
3. Trouver le bloc hexagonal ``||input:bouton A est pressé||`` dans la section ``||input:Entrée||``.
4. Le glisser à la place de ``||logic:<vrai>||`` de ``||logic:si <vrai>...sinon||``.

> ***Astuce*** *: Si vous manquez de place pour avoir une bonne vue d'ensemble de votre code, vous pouvez appuyer sur le bouton "-" en bas à droite de l'écran pour dézoomer.*

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 11." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_01/Rosy_Act1_06.gif" width="80%">

```blocks
let source = 0
basic.forever(function () {
    source = Math.map(MLX90614.temperature(Environment.Object), MLX90614.temperature(Environment.Ambient), 35, 0, 50)
    if (input.buttonIsPressed(Button.A)) {
        
    } else {
        
    }
})
```


## Étape 12

**Lorsque le bouton A est pressé**, affichons la visualisation de température.

1. Trouver le bloc ``||led:tracer le graphe||`` dans la section ``||led:LED||``.
2. Le glisser dans le crochet "si" de ``||logic:si <vrai>...sinon||``.
3. Trouver la variable ``||variables:Source||`` dans la section ``||variables:variable||``.
4. La mettre dans le premier cercle du bloc ``||led:tracer le graphe||``.
5. Inscrire le nombre 50 dans l'autre cercle.

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 12." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_01/Rosy_Act1_07.gif" width="80%">

```blocks
let source = 0
basic.forever(function () {
    source = Math.map(MLX90614.temperature(Environment.Object), MLX90614.temperature(Environment.Ambient), 35, 0, 50)
    if (input.buttonIsPressed(Button.A)) {
        led.plotBarGraph(
            source,
            50
        )
    } else {
        
    }
})
```


## Étape 13

Nous voulons **afficher** une image de planète **seulement quand une source de chaleur est détectée**.

1. Ajouter un autre bloc ``||logic:si <vrai>...sinon||`` à partir de la section ``||logic:Logique||`` et le glisser dans le crochet "sinon" du premier.
2. Glisser un bloc ``||logic:<||`` (plus petit que) à partir de la section ``||logic:Logique||`` et le placer à côté du nouveau "si".
3. À gauche du symbole "<", inscrire le nombre 1.
4. À droite du symbole, mettre la ``||variables:variable||`` "Source".

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 13." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_01/Rosy_Act1_08.gif" width="80%">

```blocks
let source = 0
basic.forever(function () {
    source = Math.map(MLX90614.temperature(Environment.Object), MLX90614.temperature(Environment.Ambient), 35, 0, 50)
    if (input.buttonIsPressed(Button.A)) {
        led.plotBarGraph(
            source,
        50
        )
    } else {
        if (1 < source) {

        } else {

        }
    }
})
```


## Étape 14

Affichons une image de planète **lorsque de la chaleur est détectée**.

1. Dans la section ``||basic:Base||``, trouver le bloc ``||basic:montrer LEDs||`` et le glisser dans le crochet "si".
2. Dessiner l'image qui vous convient dans la matrice.
3. Dans le crochet "sinon", insérer le bloc ``||basic:effacer l'écran||`` de la section ``||basic:Base||``.

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 14." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_01/Rosy_Act1_09.gif" width="80%">

```blocks
let source = 0
basic.forever(function () {
    source = Math.map(MLX90614.temperature(Environment.Object), MLX90614.temperature(Environment.Ambient), 35, 0, 50)
    if (input.buttonIsPressed(Button.A)) {
        led.plotBarGraph(
            source,
        50
        )
    } else {
        if (1 < source) {
            basic.showLeds(`
                . . # . .
                . # # # .
                # # # # #
                . # # # .
                . . # . .
                `)
        } else {
            basic.clearScreen()
        }
    }
})
```


## Étape 15 

Et voilà! Il ne reste plus qu'à **téléverser** le code sur le micro:bit. **Les instructions** de notre simulateur de télescope **sont à la prochaine étape**.

1. **Connecter le micro:bit** à votre ordinateur avec le câble USB fourni dans la trousse.
2. **Télécharger votre code** avec le bouton Télécharger en bas à gauche de l'écran.
3. Dans le gestionnaire de fichiers de votre ordinateur, **glisser le fichier téléchargé** vers le micro:bit.
4. Durant le transfert, la DEL orange au dos du micro:bit va clignoter rapidement. Une fois que c'est terminé, **votre code est sur l'appareil**.

[Voyez ici la vidéo aide-mémoire](https://youtu.be/H8utNPE3sJo) par GénieLab, et [voici la procédure détaillée](https://makecode.microbit.org/device/usb) dans la documentation de MakeCode (en anglais seulement).


## Étape 16 @showdialog

Vous pouvez maintenant **simuler** comment les télescopes à infrarouge peuvent **détecter des exoplanètes** en orbite autour d'étoiles lointaines :

1. Avec votre **main ouverte**, placez-la au-dessus du capteur de façon à ce que le micro:bit indique qu'il détecte de la chaleur.
2. Vous pouvez alors **tenir enfoncé le bouton "A"** pour lire le niveau de chaleur détecté.
3. À l'aide d'un.e ami.e, **faites passer un objet** entre votre main (l'étoile) et le capteur (télescope). Voyez comme la température détectée diminue. C'est de cette façon que les astronomes peuvent **détecter la présence de planètes** en orbite autour d'astres très lointains.
