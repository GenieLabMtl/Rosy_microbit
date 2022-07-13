# Rosy, Activité 2b : Gestion de l'énergie


## Étape 1 @showdialog

Dans cette activité, nous allons découvrir comment **diriger** l'électricité vers différents systèmes en fonction de l'énergie disponible.

Selon l'énergie générée par le panneau solaire, nous pourrons faire **allumer** différentes lumières qui seront alimentées directement par le panneau solaire.

<img alt="Résultat attendu de l'activité : le micro:bit affiche le niveau de tension électrique généré par le panneau solaire, et les DESs s'activent selon la tension." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/gifactivite2_b.gif" width="60%">


## Étape 2 @showdialog

Matériel dont vous allez avoir besoin :
- microcontrôleur micro:bit
- câble USB
- carte de développement micro:bit
- planchette de prototypage
- panneau solaire 3V
- DEL rouge
- DEL verte
- 1 résistance 10 000 ohms
- 2 résistances 220 ohms
- 2 transistors BC337
- 6 fils de raccordement mâle-femelle
- 1 fils de raccordement mâle-mâle

<img alt="microcontrôleur micro:bit, câble USB, carte de développement micro:bit, planchette de prototypage, panneau solaire 3V, DEL rouge, DEL verte, 1 résistance 10 000 ohms, 2 résistances 220 ohms, 2 transistors BC337, 6 fils de raccordement mâle-femelle, 1 fils de raccordement mâle-mâle" src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/RA2P3.jpg" width="80%">


## Étape 3a @showdialog

Les **résistances** sont probablement les composantes électroniques les plus répandues, on les trouve dans tous les circuits électroniques. Elles servent à **« limiter » le courant électrique** dans un circuit.

1. 10 000 ohms (aussi écrit 10k ohms): est utilisée comme [résistance de rappel](https://fr.wikipedia.org/wiki/R%C3%A9sistance_de_rappel) pour la lecture du panneau solaire, ce qui permettra de faire des lectures exactes du courant qui est fourni.
2. 220 ohms : Ces résistances servent à limiter le courant qui passe dans les DEL, afin d'éviter qu'elles ne brûlent si trop de courant leur est fourni.

<img alt="Les résistances sont codifiées avec des bandelettes de couleurs pour déterminer leur résistance et précision." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/code-couleur-resistance.png" width="80%">


## Étape 3b @showdialog

Sur la **planchette de développement**, placer les résistances comme suit :

> ***Astuce*** *: Il arrive que les numéros de rangées sur la planchette de prototypage soient difficiles à lire. Les numéros de rangées fournis dans les instructions sont seulement des indications pour vous aider, pas une obligation. Tant que les connexions sont faites correctement, n'importe quelles rangées peuvent être utilisées.*

1. 10k ohms : une patte dans la colonne bleue, et l'autre dans la rangée 25
2. 220 ohms : une patte dans la colonne rouge, et l'autre dans la rangée 15
3. 220 ohms : une patte dans la colonne rouge, et l'autre dans la rangée 5

<img alt="Diagramme : Les trois résistances sont placées sur la plaquette de prototypage avec beaucoup d'espace entre elles." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/Rosy_Act2_Breadboard_01_600px.png" width="80%">

<img alt="Photo des trois résistances sur la plaquette de prototypage." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/RA2P5.jpg" width="80%">



## Étape 4a @showdialog

Les **DEL**, ou diodes électroluminescentes, sont des **ampoules miniatures** qui ne demandent presque pas de puissance pour être allumées. 

Si **trop de courant** leur est fourni, elles peuvent brûler et ainsi **devenir inutilisables**. C'est pourquoi elles sont généralement utilisées avec une résistance placée en série.

Les DEL de différentes couleurs peuvent **utiliser plus ou moins de courant** selon leur fabrication.

<img alt="Les DELs ont une polarité, la patte la plus longue étant positive." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/DEL_graphique.png" width="80%">


## Étape 4b @showdialog

Sur la planchette de développement, **placer les DEL** (diodes électroluminescentes) comme suit :

1. DEL rouge : la patte la plus longue – l'anode – dans la rangée 15, et la patte la plus courte – la cathode – dans la rangée 14
2. DEL verte : la patte la plus longue dans la rangée 5, et la patte la plus courte dans la rangée 4

Les pattes longues sont donc dans les mêmes rangées que les résistances 220 ohms.

<img alt="Diagramme : La pattes les plus longues des DEL vont dans les mêmes rangées que les résistances, et les pattes courtes dans la rangée adjacente respective." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/Rosy_Act2_Breadboard_02_600px.png" width="80%">

<img alt="Photo des deux DEL ajoutées au circuit." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/RA2P6.jpg" width="80%">


## Étape 5a @showdialog

Les [transistors](https://fr.wikipedia.org/wiki/Transistor) ont de nombreuses applications, et ont rendu possible l'invention de **l'ordinateur moderne**.

Ceux que nous utilisons pour l'activité sont de type bipolaire NPN. Lorsque l'on regarde un transistor BC337 **de face**, c'est-à-dire que l'on fait face à son côté plat où est inscrit le numéro du modèle, la patte de **gauche est le collecteur**, où entre le courant, la patte du **centre est la base**, qui sert à contrôler si le transistor laisse passer le courant ou non, et la patte de **droite est l'émetteur**, où sort le courant.

Le courant sortant de l'émetteur est égal à la somme des courants au collecteur et à la base. Le courant émis par le micro:bit est très faible, et donc celui fourni par le panneau solaire semblera être le seul à avoir un impact visible sur les DEL.

>**Attention! Il ne faut jamais connecter directement la base du transistor avec les broches 3V du micro:bit. Trop de courant sera fourni, ce qui fera chauffer le transistor à une très haute température presque immédiatement!**

<img alt="Les transistors peuvent être représentés dans un diagramme sous forme de cercle avec 3 tiges en sortant." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/Émetteur_graphique.png" width="80%">


## Étape 5b @showdialog

**Écarter** légèrement les pattes des transistors, puis **placer** les transistors comme suit :

> ***Astuce*** *: il faut tenir le côté plat du transistor vers le haut et face à nous pour bien identifier les pattes.*

1er transistor : 
1. La patte de gauche – le collecteur – dans la rangée 14 avec la cathode de la DEL rouge.
2. La patte du centre – la base – seule dans la rangée 13.
3. La patte de droite – l'émetteur – dans la colonne bleue.

2e transistor : 
1. La patte de gauche dans la rangée 4.
2. La patte du centre dans la rangée 3.
3. La patte de droite dans la colonne bleue.

Les **collecteurs** sont donc dans les mêmes rangées que les **cathodes** des DEL.

>**Attention! Bien vous assurer que les pattes des différentes composantes ne se touchent pas pour éviter les courts-circuits.**

<img alt="Diagramme : Les deux transistors sont ajoutés au circuit." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/Rosy_Act2_Breadboard_03_600px.png" width="80%">

<img alt="Photo des deux transistors ajoutées au circuit." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/RA2P7.jpg" width="80%">


## Étape 6 @showdialog

**Insérer** le micro:bit dans la carte de développement.

>**Attention! La plaquette de prototypage de l'image diffère peut-être de celle que vous avez. L'important est de connecter les fils aux mêmes numéros de connecteurs.**

À l'aide des fils de raccordement mâle-femelle, faire les **connexions** suivantes :

carte de développement -> planchette de prototypage
1. G (ground) -> colonne bleue
2. 1 -> rangée 25 (même rangée que la résistance 10k ohm)
3. 2 -> rangée 13 (même rangée que la base du transistor)
4. 8 -> rangée 3 (même rangée que la base du transistor)

<img alt="Diagramme : Bien porter attention à l'endroit où l'on connecte les fils." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/Rosy_Act2_Breadboard_04_600px.png" width="80%">

<img alt="Photo des connexions sur la planchette de prototypage." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/RA2P8_1.jpg" width="80%">
<img alt="Photo des connexions sur la carte de développement." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/RA2P8_2.jpg" width="80%">


## Étape 7 @showdialog

Finalement, en utilisant 1 **fil de raccordement** mâle-mâle et 2 mâle-femelle :

>**Attention! Lorsque vous connectez les fils mâle-femelle au panneau solaire, le connecteur du panneau solaire doit être bien branché de sorte à ce que les tiges de métal à l'intérieur du connecteur soient bien insérer dans les connecteurs des fils. Une mauvaise connection donnera toujours une lecture à 0v et ne permettra pas à l'électricité de circuler.**

1. Connecter la rangée 25 (résistance 10k ohms et broche 1 du micro:bit) à la colonne rouge.
2. Connecter la colonne bleue au fil noir du panneau solaire.
3. Connecter la colonne rouge au fil rouge du panneau solaire.

<img alt="Diagramme : Connecter le panneau solaire à une extrémité de la planchette de prototypage, et ne pas oublier le fil mâle-mâle." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/Rosy_Act2_Breadboard_05_600px.png" width="80%">

<img alt="Photo des dernières connexions sur la planchette de prototypage." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/RA2P9.jpg" width="80%">


## Étape 8

Maintenant que le circuit est complet, il ne reste qu'à **programmer** le micro:bit.

Nous voulons faire **allumer** les DEL en fonction de la **lumière reçue** par le panneau solaire :

- Très peu de lumière : **aucune** lumière d'allumée
- Peu de lumière : lumière **rouge** allumée
- Beaucoup de lumière : lumière **verte** allumée


## Étape 9

Ajouter au code existant un bloc ``||logic:si <vrai>...sinon||`` de la section ``||logic:Logique||``.

> ***Astuce*** *: N'hésitez pas à déplacer les blocs sur la surface de programmation pour mieux voir votre code.*

> ***Astuce 2*** : Si les instructions prennent trop de place à l'écran, simplement cliquer sur le bouton "Moins..." en gris au centre entre la fenêtre d'instruction et l'espace de programmation.

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 9." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/Rosy_Act2_06.gif" width="80%">

```blocks
let solaire = 0
let volts = 0
basic.forever(function () {
    solaire = pins.analogReadPin(AnalogPin.P1)
    volts = solaire / 1023 * 3
    led.plotBarGraph(
    volts,
    3.3
    )
    if (true) {

    } else {

    }
})
```

## Étape 10

Nous voulons que le programme agisse différemment **selon la tension électrique** détectée.

1. Remplacer ``||logic:<vrai>||`` par un bloc ``||logic: > (plus grand que) ||``. 
2. Dans sa case de gauche, mettre la variable ``||variables:volts||``.
3. Dans la case de droite, écrire le nombre "2.1".

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 10." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/Rosy_Act2_07.gif" width="80%">

```blocks
let solaire = 0
let volts = 0
basic.forever(function () {
    solaire = pins.analogReadPin(AnalogPin.P1)
    volts = solaire / 1023 * 3
    led.plotBarGraph(
    volts,
    3.3
    )
    if (volts > 2.1) {

    } else {

    }
})
```

## Étape 11

Pour la plage **plus grand que 2.1 volts**, nous allons faire allumer la DEL verte et nous assurer que la DEL rouge est éteinte.

1. Dans le crochet directement sous ``||logic:si||``, mettre 2 fois ``||broches:écrire sur la broche||``.
2. Dans le premier, choisir la broche P8, et inscrire le nombre 1.
3. Dans le second, choisir la broche P2, et inscrire le nombre 0.

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 11." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/Rosy_Act2_08.gif" width="80%">

```blocks
let solaire = 0
let volts = 0
basic.forever(function () {
    solaire = pins.analogReadPin(AnalogPin.P1)
    volts = solaire / 1023 * 3
    led.plotBarGraph(
    volts,
    3.3
    )
    if (volts > 2.1) {
        pins.digitalWritePin(AnalogPin.P8, 1)
        pins.digitalWritePin(AnalogPin.P2, 0)
    } else {

    }
})
```

## Étape 12

Nous voulons maintenant **déterminer** ce qui va se passer si le courant est plus petit ou égale à 2.1v, mais plus grand que 1.2v.

> ***Astuce*** *: Faire clic droit sur un bloc et sélectionner Dupliquer permet de gagner beaucoup de temps!*

1. Cliquer sur le symbole ``||logic:+||`` en bas du bloc ``||logic:si < >...sinon||`` pour ajouter un ``||logic:sinon...si||``.
2. Y mettre un bloc ``||logic:<> et <>||``.
3. Dans sa case de gauche mettre un bloc de ``||logic:Logique||`` avec la variable "volts" à gauche, le symbole ``||logic:≤ (plus petit ou égal)||``, dans la case de droite, écrire le nombre "2.1".
4. Dans sa case de droite mettre un bloc de ``||logic:Logique||`` avec la variable "volts" à gauche, le symbole ``||logic:> (plus grand que)||``, dans la case de droite, écrire le nombre "1.2".

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 12." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/Rosy_Act2_09.gif" width="80%">

```blocks
let solaire = 0
let volts = 0
basic.forever(function () {
    solaire = pins.analogReadPin(AnalogPin.P1)
    volts = solaire / 1023 * 3
    led.plotBarGraph(
    volts,
    3.3
    )
    if (volts > 2.1) {
        pins.digitalWritePin(AnalogPin.P8, 1)
        pins.digitalWritePin(AnalogPin.P2, 0)
    } else if (volts <= 2.1 && volts > 1.2) {

    } else {

    }
})
```

## Étape 13

Si la tension électrique détectée est entre 2.1v et 1.2v, seule la DEL rouge s'allumera

1. Dans le crochet directement sous "si", mettre 2 fois ``||broches:écrire sur la broche||``.
2. Dans le premier, choisir la broche P8, et inscrire le nombre 0.
3. Dans le second, choisir la broche P2, et inscrire le nombre 1.

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 13." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/Rosy_Act2_10.gif" width="80%">

```blocks
let solaire = 0
let volts = 0
basic.forever(function () {
    solaire = pins.analogReadPin(AnalogPin.P1)
    volts = solaire / 1023 * 3
    led.plotBarGraph(
    volts,
    3.3
    )
    if (volts > 2.1) {
        pins.digitalWritePin(AnalogPin.P8, 1)
        pins.digitalWritePin(AnalogPin.P2, 0)
    } else if (volts <= 2.1 && volts > 1.2) {
        pins.digitalWritePin(AnalogPin.P2, 1)
        pins.digitalWritePin(AnalogPin.P8, 0)
    } else {

    }
})
```

## Étape 14

Finalement, dans le crochet ``||logic:sinon||``, mettre 2 fois ``||broches:écrire sur la broche||``.

1. Dans le premier, choisir la broche P8, et inscrire le nombre 0.
2. Dans le second, choisir la broche P2, et inscrire le nombre 0.

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 14." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_02/Rosy_Act2_11.gif" width="80%">

```blocks
let solaire = 0
let volts = 0
basic.forever(function () {
    solaire = pins.analogReadPin(AnalogPin.P1)
    volts = solaire / 1023 * 3
    led.plotBarGraph(
    volts,
    3.3
    )
    if (volts > 2.1) {
        pins.digitalWritePin(AnalogPin.P8, 1)
        pins.digitalWritePin(AnalogPin.P2, 0)
    } else if (volts <= 2.1 && volts > 1.2) {
        pins.digitalWritePin(AnalogPin.P2, 1)
        pins.digitalWritePin(AnalogPin.P8, 0)
    } else {
        pins.digitalWritePin(AnalogPin.P8, 0)
        pins.digitalWritePin(AnalogPin.P2, 0)
    }
})
```

## Étape 15

Il ne reste qu'à **téléverser** le code sur le micro:bit, et vous êtes prêt·e.

Si vous avez besoin de vous rafraîchir la mémoire, [voyez ici la vidéo aide-mémoire](https://youtu.be/H8utNPE3sJo) par GénieLab, et [voici la procédure détaillée](https://makecode.microbit.org/device/usb) dans la documentation de MakeCode (en anglais seulement).


## Étape 16

Voilà! Nous avons maintenant un système qui **réagit en fonction du courant disponible** fourni par le panneau solaire!

Pour aller plus loin, vous pouvez cliquer sur le bouton **Terminer** à droite de ce texte pour avoir accès à tous les blocs. Voici quelques idées :

- Changer les valeurs dans la section ``||logic:si < >...sinon||`` pour que le circuit réagisse mieux aux conditions dans lesquelles vous vous trouvez.
- Faire activer différentes animations à l'écran du micro:bit selon la tension électrique détectée.
- Utiliser les capteurs du micro:bit comme le thermomètre ou la boussole en combinaison avec la tension électrique générée par le panneau solaire.