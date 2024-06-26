# Eclipse - Données

## @showdialog

Programme le micro:bit pour qu'il recueille des données pendant l'éclipse solaire.

## Étape 1

Supprime le bloc ``||basic:au démarrage||``.

## Étape 2

```package

datalogger

```

Ajoute le bloc ``||basic: effacer écran||`` dans le bloc ``||basic:toujours||``.

Ajoute le bloc ``||basic: pause (ms)||`` sous le bloc ``||basic: effacer écran||``.

```blocks

basic.forever(function () {
    basic.clearScreen()
    basic.pause(100)
})

```

## Étape 3

Remplace la valeur ``||basic: 100||`` du bloc ``||basic: pause (ms)||`` par le bloc ``||math: 0  x  0||``.

```blocks

basic.forever(function () {
    basic.clearScreen()
    basic.pause(0 * 0)
})

```

## Étape 4

Modifie le bloc ``||math: 0  x  0||``.

Remplace la valeur ``||math: 0||`` de gauche par ``||math: 1000||``.

Remplace la valeur ``||math: 0||`` de droite par le bloc ``||math: 5||``.

```blocks

basic.forever(function () {
    basic.clearScreen()
    basic.pause(1000 * 5)
})

```

## Étape 5

Ajoute le bloc ``||datalogger: log data||`` (trad. : enregistrer des données) sous le bloc ``||basic: pause (ms)||``.

Appuie sur ``||datalogger: +||`` pour ajouter une 2e colonne.

```blocks

basic.forever(function () {
    basic.clearScreen()
    basic.pause(1000 * 5)
    datalogger.log(
    datalogger.createCV("", 0),
    datalogger.createCV("", 0)
    )
})

```

## Étape 6

Renomme les 2 colonnes du tableau par les valeurs ``||datalogger: T||`` (pour Celsius) et ``||datalogger: L||`` (pour luminosité).

```blocks

basic.forever(function () {
    basic.clearScreen()
    basic.pause(1000 * 5)
    datalogger.log(
    datalogger.createCV("T", 0),
    datalogger.createCV("L", 0)
    )
})

```

## Étape 7

Remplace la valeur ``||datalogger: 0||`` de la colonne ``||datalogger: T||`` par le bloc ``||input: température||``.

Remplace la valeur ``||datalogger: 0||`` de la colonne ``||datalogger: L||`` par le bloc ``||math: 0  x  0||``.

```blocks

basic.forever(function () {
    basic.clearScreen()
    basic.pause(1000 * 5)
    datalogger.log(
    datalogger.createCV("T", input.temperature()),
    datalogger.createCV("L", 0 * 0)
    )
})

```

## Étape 8

Remplace la valeur ``||math: 0 ||`` de droite du bloc ``||math: 0  x  0||`` par le bloc ``||math: 0  /  0||``.

```blocks

basic.forever(function () {
    basic.clearScreen()
    basic.pause(1000 * 5)
    datalogger.log(
    datalogger.createCV("T", input.temperature()),
    datalogger.createCV("L", 0 * (0 / 0))
    )
})

```

## Étape 9

Modifie les valeurs.

Remplace la valeur ``||math: 0||`` de gauche par le bloc ``||input: niveau d'intensité lumineuse||``.

Remplace la valeur ``||math: 0||`` du centre par la valeur 100. 

Remplace la valeur ``||math: 0||`` de droite par la valeur 255.

```blocks

basic.forever(function () {
    basic.clearScreen()
    basic.pause(1000 * 5)
    datalogger.log(
    datalogger.createCV("T", input.temperature()),
    datalogger.createCV("L", input.lightLevel() * (100 / 255))
    )
})

```

## Étape 10

Ajoute le bloc ``||basic: montrer l'icône||`` sous le bloc ``||datalogger: log data||`` (trad. : enregistrer des données).

Sélectionne le ``||basic: le crochet||`` comme icône.

```blocks

basic.forever(function () {
    basic.clearScreen()
    basic.pause(1000 * 5)
    datalogger.log(
    datalogger.createCV("T", input.temperature()),
    datalogger.createCV("L", input.lightLevel() * (100 / 255))
    )
    basic.showIcon(IconNames.Yes)
})

```

## Étape 11

Glisse le bloc ``||input: lorsque le bouton A+B est pressé)||`` dans la zone de programme.

Ajoute le bloc ``||datalogger: delete log||`` (trad. : effacer le journal de données) dans le bloc ``||input: lorsque le bouton A+B est pressé)||``.

```blocks

input.onButtonPressed(Button.AB, function () {
    datalogger.deleteLog(datalogger.DeleteType.Fast)
})

```

## Étape 12

Modifie le bloc ``||datalogger: delete log||`` (trad. : effacer le journal de données).

Appuie sur le ``||datalogger: +||`` pour afficher plus d'options.

Remplace la valeur ``||datalogger: fast||`` (trad. : rapide) par la valeur ``||datalogger: plein||`` (trad. : au complet).

```blocks

input.onButtonPressed(Button.AB, function () {
    datalogger.deleteLog(datalogger.DeleteType.Full)
})

```

## Étape 13

Ajoute le bloc ``||basic: pause (ms)||`` sous le bloc  ``||datalogger: delete log||`` (trad. : effacer les données).

Remplace la valeur ``||basic: 100||`` par ``||basic: 1000||``.

```blocks

input.onButtonPressed(Button.AB, function () {
    datalogger.deleteLog(datalogger.DeleteType.Full)
    basic.pause(1000)
})

```

## Étape 14

Ajoute le bloc ``||control: remise à zero||`` sous le bloc  ``||basic: pause (ms)||``.

```blocks

input.onButtonPressed(Button.AB, function () {
    datalogger.deleteLog(datalogger.DeleteType.Full)
    basic.pause(1000)
    control.reset()
})

```

## Étape 15

Ajoute le bloc ``||basic: montrer nombre||`` dans le bloc ``||input: lorsque le bouton A est pressé||``.

Remplace la valeur ``||basic: 0||`` par le bloc ``||input: température||``.

```blocks

input.onButtonPressed(Button.A, function () {
    basic.showNumber(input.temperature())
})

```

## Étape 16

Ajoute le bloc ``||basic: montrer nombre||`` dans le bloc ``||input: lorsque le bouton B est pressé||``.

Remplace la valeur ``||basic: 0||`` par le bloc ``||math: 0  x  0||``.

```blocks

input.onButtonPressed(Button.B, function () {
    basic.showNumber(0 * 0)
})

```

## Étape 17

Remplace la valeur ``||math: 0||`` de droite du bloc ``||math: 0  x  0||`` par le bloc ``||math: 0  /  0||``.

```blocks

input.onButtonPressed(Button.B, function () {
    basic.showNumber(0 * (0 / 0))
})

```

## Étape 18

Modifie les valeurs dans le bloc ``||basic: montrer nombre||``.

Remplace la valeur ``||math: 0||`` de gauche par le bloc ``||input: niveau d'intensité lumineuse||``.

Remplace la valeur ``||math: 0||`` du centre par la valeur 100. 

Remplace la valeur ``||math: 0||`` de droite par la valeur 255.

```blocks

input.onButtonPressed(Button.B, function () {
    basic.showNumber(input.lightLevel() * (100 / 255))
})

```

## Étape 19

Voici la programmation complète du tutoriel.

Regarde bien l'indice !

```blocks

input.onButtonPressed(Button.A, function () {
    basic.showNumber(input.temperature())
})
input.onButtonPressed(Button.AB, function () {
    datalogger.deleteLog(datalogger.DeleteType.Full)
    basic.pause(1000)
    control.reset()
})
input.onButtonPressed(Button.B, function () {
    basic.showNumber(input.lightLevel() * (100 / 255))
})
basic.forever(function () {
    basic.clearScreen()
    basic.pause(1000 * 5)
    datalogger.log(
    datalogger.createCV("T", input.temperature()),
    datalogger.createCV("L", input.lightLevel() * (100 / 255))
    )
    basic.showIcon(IconNames.Yes)
})


```

## Étape 18

Télécharge et teste la la programmation avec le micro:bit.

