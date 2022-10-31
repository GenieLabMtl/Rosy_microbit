# Rosy, Activité 3 : Communication - Activité à faire en solo 

## Présentation 1 @showdialog

Ce tutoriel est à faire seul·e.

Si vous êtes en groupe de 3 et que vous avez chacun.e un nano-ordinateur micro:bit, vous pouvez également faire l'*Activité 3 : Communication radio*, que vous trouverez sur la plateforme d'apprentissage en ligne.

![Rosy quelque part dans l'espace](https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Terre_Mars.png)

La communication entre les différents systèmes d'un satellite est essentielle à l'observation spatiale. Même si les meilleures images de tous les temps sont captées, si elles ne peuvent pas être envoyées sur Terre, personne ne pourra jamais les voir...

Les satellites d'observation spatiale sont des machines extrêmement complexes qui prennent plusieurs années à concevoir. Les systèmes qui s'y trouvent sont hautement automatisés puisque le temps de communication entre la Terre et le satellite fait en sorte que leur contrôle en temps réel est impossible.

## Présentation 2 @showdialog

Pour cette activité, nous allons programmer le micro:bit pour que ses coordonnées soient automatiquement envoyées au système de télécommunication lorsque nous trouvons les coordonnées d'une étoile inconnue et prometteuse.

Nous pourrons visualiser à l'écran de l'ordinateur les résultats de nos recherches en temps réel.

Pour réussir votre mission, il faut :

1. Générer des coordonnées X et Y aléatoirement pour représenter une étoile inconnue.
2. Utiliser le gyroscope intégré du micro:bit pour rechercher cette étoile en inclinant celui-ci de gauche à droite et de l'avant vers l'arrière.
3. Évaluer les coordonnées explorées en inclinant le micro:bit pour voir si elles sont celles de l'étoile inconnue.
4. Si nous avons trouvé ses coordonnées, envoyer un message les affichant à l'ordinateur.

Plusieurs concepts de programmation très utiles seront présentés lors de cette activité. À vous de voir comment vous pourrez modifier le code final pour l'utiliser comme point de départ pour d'autres projets.

>***IMPORTANT : Pour que cette activité fonctionne bien, vous allez avoir besoin d'utiliser le navigateur Google Chrome ou Microsoft Edge.***

Bonne chance!


## Étape 1

> ***Astuce*** : Si les instructions prennent trop de place à l'écran, simplement cliquer sur le bouton "Moins..." en gris au centre entre la fenêtre d'instruction et l'espace de programmation.

Pour commencer, nous allons créer une fonction. Les fonctions servent à encapsuler du code qui va être utilisé plusieurs fois dans notre programme.

1. **Ouvrir** le menu déroulant de la section ``||advanced:Avancé||`` au bas de la liste des catégories, puis aller dans la section ``||functions:Fonctions||``.
2. **Cliquer** sur le bouton "**Créer une fonction...**". Dans la fenêtre qui va s'ouvrir, **cliquer** sur le texte "**faireQuelqueChose**" dans le bloc ``||functions:fonction||``, et le **renommer** "TrouverUneEtoile".
3. Votre fonction devrait maintenant apparaitre dans la surface de programmation.

>**À noter! Il arrive que les images de la bulle d'aide soient différentes de ce que l'on retrouve dans l'espace de programmation : couleurs différentes, noms en anglais, noms de variables différents des instructions, etc. Pas de problème, il s'agit simplement d'un caprice d'affichage de la plateforme MakeCode que vous pouvez ignorer. 😄**

<img alt="Activité 3 Solo Étape 1" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Solo_01.gif" width="80%">

```blocks
function TrouverUneEtoile () {
	
}
```

## Étape 2

Nous allons maintenant avoir besoin de deux variables pour garder en mémoire les coordonnées de l'étoile inconnue.

1. Dans la section ``||variables:Variables||``, **cliquer** sur le bouton "**Créer une variable...**". Nommer-là "**coord_x**", pour *coordonnée X*.
2. **Cliquer** à nouveau sur le bouton "**Créer une variable...**", et cette fois la nommer "**coord_y**", pour *coordonnée Y*.
3. **Glisser 2 fois** le bloc ``||variables:définir [nom de la variable] à 0||`` dans le bloc de notre fonction.
4. Assurez-vous qu'un des bloc de ``||variables:variables||`` indique "**coord_x**", et l'autre "**coord_y**".

<img alt="Activité 3 Solo Étape 2" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Solo_02.gif" width="80%">

```blocks
function TrouverUneEtoile () {
    coord_x = 0
    coord_y = 0
}
```

## Étape 3

En attribuant une valeur aléatoire – c'est-à-dire au hasard – à nos coordonnées, une nouvelle étoile sera générée à chaque utilisation de notre programme.
Les valeurs à choisir devront se trouver entre les valeurs minimales et maximales de lecture du gyroscope du micro:bit : -1023 et 1023.

1. Dans la section ``||Math:Maths||``, **trouver** le bloc ``||Math:choisir au hasard de 0 à 10||``, et **l'ajouter** à la place du **0** dans les 2 blocs ``||variables:définir||``.
2. Inscrire "**-1023**" dans le cercle de gauche des blocs  ``||Math:choisir au hasard||``, et "**1023**" dans le cercle de droite.

<img alt="Activité 3 Solo Étape 3" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Solo_03.gif" width="80%">

```blocks
function TrouverUneEtoile () {
    coord_x = randint(-1023, 1023)
    coord_y = randint(-1023, 1023)
}
```

## Étape 4

Maintenant que notre fonction est prête, nous voulons que des coordonnées soient choisies chaque fois que le programme est lancé.

1. Dans la section ``||functions:Fonctions||`` – qui se trouve toujours sous **Avancé** –, **glisser** le bloc ``||functions:appel TrouverUneEtoile||`` dans le bloc ``||basic:au démarrage||``.

C'est tout! Les 2 variables auront des chiffres aléatoires attribués quand notre programme sera lancé.

<img alt="Activité 3 Solo Étape 4" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Solo_04.gif" width="80%">

```blocks
TrouverUneEtoile()
```

## Étape 5

Il est maintenant temps d'écrire le programme comme tel. Nous voulons d'abord envoyer un message indiquant qu'une nouvelle lecture du gyroscope a lieu.

1. Sous **Avancé**, aller dans la section ``||serial:Communication Série||``.
2. **Trouver** le bloc ``||serial:série écrire ligne ""||`` et **l'ajouter** dans le bloc ``||basic:toujours||``.
3. Dans le cercle où il est indiqué "", écrire "**Nouvelle lecture**".

<img alt="Activité 3 Solo Étape 5" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Solo_05.gif" width="80%">

```blocks
basic.forever(function () {
    serial.writeLine("Nouvelle lecture")
})
```

## Étape 6

Il peut être utile de voir quelle valeur est lue par le gyroscope avant de l'évaluer. Nous allons donc faire afficher cette valeur à notre écran d'ordinateur.

Commençons par l'axe des X (de gauche à droite).

1. Dans la section ``||serial:Communication Série||``, **glisser** le bloc ``||serial:série écrire valeur "x" = 0||`` dans notre code sous ``||serial:série écrire ligne||``.
2. Dans la section ``||input:Entrée||``, **glisser** le bloc ``||input:accélération (mg) x||`` à la place du **0**.

<img alt="Activité 3 Solo Étape 6" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Solo_06.gif" width="80%">

```blocks
basic.forever(function () {
    serial.writeLine("Nouvelle lecture")
    serial.writeValue("x", input.acceleration(Dimension.X))
})
```

## Étape 7

Il faut maintenant déterminer si notre valeur X est proche de celle de la coordonnée que nous recherchons. Puisqu'il est difficile et très long de tester toutes les 2047 valeurs allant de -1023 à 1023 et répéter ça 2047 fois pour chaque valeur de Y (pour un total de plus de 4.1 millions de possibilités!), vous allons utiliser une plage plus large.
En vérifiant si notre valeur X est à plus ou moins 200 de la valeur de la coordonnée mystère, on pourra la trouver beaucoup plus rapidement.

1. **Glisser** un bloc ``||logic:si <vrai> alors...sinon||`` de la section ``||logic:Logique||``, et **l'ajouter** à la suite de notre code.
2. **Glisser** le bloc logique ``||logic:<> et <>||`` et **l'ajouter** à la place du ``||logic:vrai||`` de notre bloc conditionnel.
3. **Glisser** 2 fois le bloc logique ``||logic:0 < 0||`` et **les ajouter** dans chacun des hexagones du bloc précédent.
4. Dans la section ``||Math:Maths||``, **glisser** 2 fois le bloc ``||math:0 - 0||`` et **l'ajouter** dans le cercle de droite de chacun des blocs ``||logic:0 < 0||``.

<img alt="Activité 3 Solo Étape 7" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Solo_07.gif" width="80%">

```blocks
basic.forever(function () {
    serial.writeLine("Nouvelle lecture")
    serial.writeValue("x", input.acceleration(Dimension.X))
    if (0 < 0 - 0 && 0 < 0 - 0) {
    	
    } else {
    	
    }
})
```

## Étape 8

Nous allons maintenant comparer la lecture du gyroscope en X avec la variable coord_x.

>**Attention! Lorsqu'il y a beaucoup de blocs l'un dans l'autre, il est facile de se tromper et de mettre un bloc au mauvais endroit. Il y a une fonction "revenir en arrière" fort utile, située en bas à droite de l'écran, que l'on peut utiliser en appuyant sur la flèche courbée vers la gauche.**

1. Faire un **clic droit** sur ``||input:accélération (mg) X||`` et sélectionner **Dupliquer**. (Si vous ne pouvez pas faire de clic droit, aller le retrouver dans le menu comme à l'étape précédente).
2. **Glisser** ce nouveau bloc dans le cercle de gauche du premier ``||logic:0 < 0||``.
3. **Répéter cette manoeuvre** pour mettre un autre bloc ``||input:accélération (mg) X||`` dans le cercle de gauche du second ``||logic:0 < 0||``.
4. Dans le cercle de gauche de chacun des blocs ``||math:0 - 0||``, **ajouter** la variable ``||variables:coord_x||``, que vous pouvez trouver dans la section ``||variables:Variables||``.
5. **Inscrire** "200" à la place des deux "0" restants.
6. Dans le bloc logique à la gauche du ``||logic:et||``, changer le symbole ``||logic:<||`` pour un ``||logic:>||``.
7. Dans le bloc logique à la droite du ``||logic:et||``, changer le symbole ``||logic:-||`` pour ``||logic:+||``.

<img alt="Activité 3 Solo Étape 8" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Solo_08.gif" width="80%">

```blocks
basic.forever(function () {
    serial.writeLine("Nouvelle lecture")
    serial.writeValue("x", input.acceleration(Dimension.X))
    if (input.acceleration(Dimension.X) > coord_x - 200 && input.acceleration(Dimension.X) < coord_x + 200) {
    	
    } else {
    	
    }
})
```

## Étape 9

Nous allons avoir besoin de nouvelles variables pour garder en mémoire le résultat de notre comparaison logique pour l'axe des X.

1. Dans la section ``||variables:Variables||``, **cliquer** sur le bouton "Créer une variable...". La nommer "**etoile_x**".
2. **Cliquer** à nouveau sur le bouton "Créer une variable...", et cette fois la nommer "**etoile_y**".
3. **Glisser** le bloc ``||variables:définir [nom de la variable] à 0||`` 2 fois, un dans chacune des sections du bloc ``||logic:si <> alors...sinon||``. Assurez-vous que la variable indiquée est bien "**etoile_x**".
4. À partir de ``||logic:Logique||``, **glisser** le bloc ``||logic:<vrai>||`` dans le ``||variables:définir etoile_x à 0||`` du haut.
5. **Glisser** le bloc ``||logic:<faux>||`` dans le ``||variables:définir etoile_x à 0||`` du bas.

<img alt="Activité 3 Solo Étape 9" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Solo_09.gif" width="80%">

```blocks
basic.forever(function () {
    serial.writeLine("Nouvelle lecture")
    serial.writeValue("x", input.acceleration(Dimension.X))
    if (input.acceleration(Dimension.X) > coord_x - 200 && input.acceleration(Dimension.X) < coord_x + 200) {
        étoile_x = true
    } else {
        étoile_x = false
    }
})
```

 
## Étape 10

Maintenant que nous pouvons vérifier si nous avons trouvé la valeur en X des coordonnées de l'étoile, nous devons maintenant refaire la même chose pour l'axe des Y.

> ***Astuce*** *: Si vous pouvez vous en servir, utiliser clic droit->Dupliquer sur les blocs dans l'espace de programmation va vous sauver beaucoup de temps. Sinon, refaire les 6 à 9 en remplaçant toutes les mentions de "X" par "Y".*

1. **Dupliquer** le bloc ``||serial:série écrire valeur "x"||`` et mettre le nouveau à la suite de notre bloc ``||logic:si...alors...sinon||``.
2. **Changer** dans ce bloc les 2 mentions de "**x**" pour "**y**".
3. **Dupliquer** le bloc ``||logic:si...alors...sinon||``. Si vous le faites à partir du bon bloc, tous les blocs inclus dedans devraient également être dupliqués. Le mettre à la suite du code.
4. Changer les 2 "**x**" pour "**y**", les 2 "**coord_x**" pour "**coord_y**", et les 2 "**etoile_x**" pour "**etoile_y**".

<img alt="Activité 3 Solo Étape 10" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Solo_10.gif" width="80%">

```blocks
basic.forever(function () {
    serial.writeLine("Nouvelle lecture")
    serial.writeValue("x", input.acceleration(Dimension.X))
    if (input.acceleration(Dimension.X) > coord_x - 200 && input.acceleration(Dimension.X) < coord_x + 200) {
        étoile_x = true
    } else {
        étoile_x = false
    }
    serial.writeValue("y", input.acceleration(Dimension.Y))
    if (input.acceleration(Dimension.Y) > coord_y - 200 && input.acceleration(Dimension.Y) < coord_y + 200) {
        étoile_y = true
    } else {
        étoile_y = false
    }
})
```


## Étape 11

Finalement, si les 2 conditions (X et Y) sont vraies, nous pourrons envoyer un message comme quoi l'étoile a été découverte.

1. **Prendre** un bloc ``||logic:si <vrai> alors||`` de la section ``||logic:Logique||`` et **le placer** à la suite du code.
2. **Prendre** le bloc logique ``||logic:<> et <>||`` et **l'ajouter** à la place du "**vrai**" de notre bloc conditionnel.
3. **Prendre** 2 fois le bloc logique ``||logic:0 = 0||`` et **les ajouter** dans chacun des hexagones du bloc précédent.
4. Dans chacun des cercles à gauche des symboles "=", **ajouter** les variables "**etoile_x**" et "**etoile_y**", que vous pouvez trouver dans la section ``||variables:Variables||``.
5. Dans les cercles de droite, **Ajouter** ``||logic:<vrai>||``, qui se trouve dans la section ``||logic:Logique||``.

<img alt="Activité 3 Solo Étape 11" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Solo_11.gif" width="80%">

```blocks
basic.forever(function () {
    serial.writeLine("Nouvelle lecture")
    serial.writeValue("x", input.acceleration(Dimension.X))
    if (input.acceleration(Dimension.X) > coord_x - 200 && input.acceleration(Dimension.X) < coord_x + 200) {
        étoile_x = true
    } else {
        étoile_x = false
    }
    serial.writeValue("y", input.acceleration(Dimension.Y))
    if (input.acceleration(Dimension.Y) > coord_y - 200 && input.acceleration(Dimension.Y) < coord_y + 200) {
        étoile_y = true
    } else {
        étoile_y = false
    }
    if (étoile_x == true && étoile_y == true) {

    }
})
```

## Étape 12

Si effectivement nous avons trouvé l'étoile, envoyons un message qui annonce la découverte et ses coordonnées.

1. Sous ``||advanced:Avancé||``, aller dans la section ``||serial:Communication Série||`` puis **glisser** ``||serial:série écrire ligne ""||`` dans le bloc ``||logic:si...alors||``.
2. Encore sous ``||advanced:Avancé||``, aller dans la section ``||text:Texte||`` et **trouver** ``||text:concaténation "Bonjour" "Monde"||``. **L'ajouter** dans le bloc ``||serial:série écrire ligne ""||``.
3. **Cliquer** 3 fois sur le symbole + de ce bloc pour avoir un total de 5 cercles.
4. Dans le premier, **inscrire** : "**Étoile trouvée!**"
5. Dans le 2e, **inscrire** : " X : "
6. Dans le 3e, **insérer** ``||input:accélération (mg) x||``.
7. Dans le 4e, **inscrire** : ", Y : "
8. Dans le dernier, **insérer** ``||input:accélération (mg) y||``.

> ***Astuce*** *: N'oubliez pas les espaces avant et après les lettres/signes de ponctuation tels qu'ils sont indiqués dans les instructions. Votre message sera ainsi plus facilement lisible.*

<img alt="Activité 3 Solo Étape 12" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Solo_12.gif" width="80%">

```blocks
basic.forever(function () {
    serial.writeLine("Nouvelle lecture")
    serial.writeValue("x", input.acceleration(Dimension.X))
    if (input.acceleration(Dimension.X) > coord_x - 200 && input.acceleration(Dimension.X) < coord_x + 200) {
        étoile_x = true
    } else {
        étoile_x = false
    }
    serial.writeValue("y", input.acceleration(Dimension.Y))
    if (input.acceleration(Dimension.Y) > coord_y - 200 && input.acceleration(Dimension.Y) < coord_y + 200) {
        étoile_y = true
    } else {
        étoile_y = false
    }
    if (étoile_x == true && étoile_y == true) {
        serial.writeLine("Étoile trouvée! " + "X : " + input.acceleration(Dimension.X) + ", Y : " + input.acceleration(Dimension.Y))
    }
})
```

## Étape 13

Finalement, après 5 secondes, assignons de nouvelles coordonnées aléatoires pour recommencer.

1. Dans ``||basic:Base||``, **prendre** ``||basic:pause (ms) 100||`` et **l'ajouter** à la suite de ``||serial:série écrire ligne ||``. **Changer** le nombre pour 5000 millisecondes, soit 5 secondes.
2. Dans ``||functions:Fonctions||``, **trouver** ``||functions:appel TrouverUneEtoile||`` et **l'ajouter** à la suite.
3. **Dupliquer** ``||basic:pause (ms) 5000||``, **l'ajouter** à la toute fin du code, sous le bloc ``||logic:si ... alors||``, et **inscrire** 100 millisecondes.

Ce dernier bloc sert à ralentir légèrement la vitesse d'affichage des données pour les rendre plus facilement lisibles.

<img alt="Activité 3 Solo Étape 13" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Act3_Solo_13.gif" width="80%">

```blocks
basic.forever(function () {
    serial.writeLine("Nouvelle lecture")
    serial.writeValue("x", input.acceleration(Dimension.X))
    if (input.acceleration(Dimension.X) > coord_x - 200 && input.acceleration(Dimension.X) < coord_x + 200) {
        étoile_x = true
    } else {
        étoile_x = false
    }
    serial.writeValue("y", input.acceleration(Dimension.Y))
    if (input.acceleration(Dimension.Y) > coord_y - 200 && input.acceleration(Dimension.Y) < coord_y + 200) {
        étoile_y = true
    } else {
        étoile_y = false
    }
    if (étoile_x == true && étoile_y == true) {
        serial.writeLine("Étoile trouvée! " + "X : " + input.acceleration(Dimension.X) + ", Y : " + input.acceleration(Dimension.Y))
        basic.pause(5000)
        TrouverUneEtoile()
    }
    basic.pause(100)
})
```

## Étape 14 @showhint

Voilà, le code est maintenant prêt! Le voici au complet.

```blocks
function TrouverUneEtoile () {
    coord_x = randint(-1023, 1023)
    coord_y = randint(-1023, 1023)
}
let coord_y = 0
let coord_x = 0
let étoile_y = false
let étoile_x = false
TrouverUneEtoile()
basic.forever(function () {
    serial.writeLine("Nouvelle lecture")
    serial.writeValue("x", input.acceleration(Dimension.X))
    if (input.acceleration(Dimension.X) > coord_x - 200 && input.acceleration(Dimension.X) < coord_x + 200) {
        étoile_x = true
    } else {
        étoile_x = false
    }
    serial.writeValue("y", input.acceleration(Dimension.Y))
    if (input.acceleration(Dimension.Y) > coord_y - 200 && input.acceleration(Dimension.Y) < coord_y + 200) {
        étoile_y = true
    } else {
        étoile_y = false
    }
    if (étoile_x == true && étoile_y == true) {
        serial.writeLine("Étoile trouvée! " + "X : " + input.acceleration(Dimension.X) + ", Y : " + input.acceleration(Dimension.Y))
        basic.pause(5000)
        TrouverUneEtoile()
    }
    basic.pause(100)
})

```


## Étape 15

Il ne reste qu'à téléverser le code sur le micro:bit, et vous êtes prêt·e.

Si vous avez besoin de vous rafraîchir la mémoire au sujet du téléversement du code, [voyez ici la vidéo aide-mémoire](https://youtu.be/H8utNPE3sJo) par GénieLab, et [voici la procédure détaillée](https://makecode.microbit.org/device/usb) dans la documentation de MakeCode (en anglais seulement).

> **Attention! Une fois le code installé, le micro:bit va redémarrer. Il faudra alors calibrer le gyroscope en faisant pivoter l'appareil dans tous les sens selon les instructions qui défileront à l'écran (en anglais). Lorsque toutes les DELs sont allumées, la calibration est terminée. Il faut la faire à chaque fois que le micro:bit redémarre quand le gyroscope est utilisé.**


## Étape 16

Deux boutons s'affichent maintenant sous le micro:bit virtuel : *Afficher la console Simulateur*, *Afficher la console Appareil*.

1. Cliquer sur *Afficher la console Appareil*. L'espace de programmation disparait pour faire place à un visualisateur de données provenant du micro:bit. 
2. Essayez maintenant de détecter des étoiles inconnues. Bonne chance!

![Activité 3 Solo Étape 13](https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_03/Rosy_Microbit_Console.png)


## Étape 17 @showdialog

Pour aller plus loin, voici quelques idées pour modifier le code :

1. Est-ce que vous pourriez utiliser d'autres capteurs au lieu du gyroscope?
2. Ajouter un indicateur sonore qui varie en fonction de la distance entre votre point d'observation et les coordonnées de l'étoile.
3. Quelles autres informations pourraient être envoyées pour être affichées à l'écran?
4. Est-ce qu'il y aurait d'autres façon d'écrire ce code pour arriver au même résultat?

Pour ceux et celles qui s'intéressent particulièrement à la programmation, allez explorer la version JavaScript de votre code. Simplement importer le fichier .hex de votre code dans une session régulière de MakeCode (pas le tutoriel), et vous pourrez basculer en JavaScript et même Python avec le bouton qui se trouve en haut de l'écran. Vous pourrez ainsi allez beaucoup plus loin beaucoup plus rapidement qu'avec l'interface de programmation visuelle.

Merci beaucoup pour votre participation !