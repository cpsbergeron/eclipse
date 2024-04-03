# Eclipse - Données

## @showdialog

Programme le micro:bit pour qu'il recueille des données pendant l'éclipse solaire.

## Étape 1

Supprime les blocs ``||basic:toujours||`` et ``||basic:au démarrage||``.

## Étape 2

```package

datalogger

```

Glisse le bloc ``||loops: chaque 500 (ms)||`` dans la zone de programme.

Remplace la valeur ``||loops: 500||`` par le bloc ``||math: 0   x   0||``.

```blocks

loops.everyInterval(0 * 0, function () {
    })

```

## Étape 3

Modifie le bloc ``||math: 0   x   0||``.

Remplace la valeur ``||math: 0||`` de gauche par ``||math: 1000||``.

Remplace la valeur ``||math: 0||`` de droite par le bloc ``||math: 0   x   0||``.

```blocks

loops.everyInterval(1000 * (0 * 0), function () {
    
})

```

## Étape 4

Modifie le nouveau bloc ``||math: 0   x   0||``.

Remplace la valeur ``||math: 0||`` du centre par ``||math: 60||``.

Remplace la valeur ``||math: 0||`` de droite par par ``||math: 2||``.

```blocks

loops.everyInterval(1000 * (60 * 5), function () {
    
})

```

## Étape 5

Ajoute le bloc ``||datalogger: log data||`` (trad. : enregistrer des données) dans le bloc ``||loops: chaque (ms)||``.

Appuie sur ``||datalogger: +||`` pour ajouter une 2e colonne.

```blocks

loops.everyInterval(1000 * (60 * 2), function () {
    datalogger.log(
    datalogger.createCV("", 0),
    datalogger.createCV("", 0)
    )
})

```

## Étape 6

Renomme les 2 colonnes du tableau par les valeurs ``||datalogger: T||`` (pour Celsius) et ``||datalogger: L||`` (pour luminosité).

```blocks

loops.everyInterval(1000 * (60 * 2), function () {
    datalogger.log(
    datalogger.createCV("T", 0),
    datalogger.createCV("L", 0)
    )
})

```

## Étape 7

Remplace la valeur ``||datalogger: 0||`` de la colonne ``||datalogger: T||`` par le bloc ``||input: température||``.

Remplace la valeur ``||datalogger: 0||`` de la colonne ``||datalogger: L||`` par le bloc ``||input: niveau d'intensité lumineuse||``.

```blocks

loops.everyInterval(1000 * (60 * 2), function () {
    datalogger.log(
    datalogger.createCV("T", input.temperature()),
    datalogger.createCV("L", input.lightLevel())
    )
})

```

## Étape 8

Glisse le bloc ``||input: lorsque le bouton A+B est pressé)||`` dans la zone de programme.

Ajoute le bloc ``||datalogger: delete log||`` (trad. : effacer le journal de données) dans le bloc ``||input: lorsque le bouton A+B est pressé)||``.

```blocks

input.onButtonPressed(Button.AB, function () {
    datalogger.deleteLog(datalogger.DeleteType.Fast)
})

```

## Étape 9

Modifie le bloc ``||datalogger: delete log||`` (trad. : effacer le journal de données).

Appuie sur le ``||datalogger: +||`` pour afficher plus d'options.

Remplace la valeur ``||datalogger: fast||`` (trad. : rapide) par la valeur ``||datalogger: plein||`` (trad. : au complet).

```blocks

input.onButtonPressed(Button.AB, function () {
    datalogger.deleteLog(datalogger.DeleteType.Full)
})

```

## Étape 10

Ajoute le bloc ``||basic: pause (ms)||`` sous le bloc  ``||datalogger: delete log||`` (trad. : effacer les données).

Remplace la valeur ``||basic: 100||`` par ``||basic: 1000||``.

```blocks

input.onButtonPressed(Button.AB, function () {
    datalogger.deleteLog(datalogger.DeleteType.Full)
    basic.pause(1000)
})

```

## Étape 11

Ajoute le bloc ``||control: remise à zero||`` sous le bloc  ``||basic: pause (ms)||``.

```blocks

input.onButtonPressed(Button.AB, function () {
    datalogger.deleteLog(datalogger.DeleteType.Full)
    basic.pause(1000)
    control.reset()
})

```

## Étape 12

Voici la programmation complète du tutoriel.

Regarde bien l'indice !

```blocks

input.onButtonPressed(Button.AB, function () {
    datalogger.deleteLog(datalogger.DeleteType.Full)
    basic.pause(1000)
    control.reset()
})
loops.everyInterval(1000 * (60 * 2), function () {
    datalogger.log(
    datalogger.createCV("T", input.temperature()),
    datalogger.createCV("L", input.lightLevel())
    )
})

```

## Étape 13

Télécharge et teste la la programmation avec le micro:bit.

