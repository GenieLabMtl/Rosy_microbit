# Rosy, Activité 2a : Panneau solaire V2

### Étape 1 @showdialog 
bonjour


### etape 2

Le capteur infrarouge [MLX90614](https://www.melexis.com/en/product/mlx90614/digital-plug-play-infrared-thermometer-to-can) permet de **lire la température** ambiante et la température d'un objet en face du capteur. La version que nous utilisons a **une portée utile d'environ 30 cm**.

### etape 3

Nous pouvons maintenant mettre ``||Math:projeter||`` dans le bloc ``||variables:définir||``.

<img alt="Animation de l'assemblage des blocs de programmation de l'étape 10." src="https://raw.githubusercontent.com/GenieLabMtl/Rosy_microbit/master/static/images/Activity_01/Rosy_Act1_05.gif" width="80%">

```blocks
let source = 0
basic.forever(function () {
    source = Math.map(MLX90614.temperature(Environment.Object), MLX90614.temperature(Environment.Ambient), 35, 0, 50)
```
