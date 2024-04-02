# Eclipse - Données

## @showdialog

Programme le micro:bit pour qu'il recueille des données pendant l'éclipse solaire.

## Étape 1

Supprime les blocs ``||basic:toujours||`` et ``||basic:au démarrage||``.

## Étape 2


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

Remplace la valeur ``||math: 0||`` de droite par par ``||math: 5||``.

```blocks

loops.everyInterval(1000 * (60 * 5), function () {
    
})

```

## Étape 5


Ajoute le bloc ``||datalogger: log data||`` (trad. : enregistrer des données) dans le bloc ``||loops: chaque (ms)||``.

Appuie sur ``||datalogger: +||`` pour ajouter une 2e colonne.

```blocks

loops.everyInterval(1000 * (60 * 5), function () {
    datalogger.log(
    datalogger.createCV("", 0),
    datalogger.createCV("", 0)
    )
})

```
