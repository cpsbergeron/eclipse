# Eclipse - Données

## @showdialog

Programme le micro:bit pour qu'il recueille des données pendant l'éclipse solaire.

## Étape 1

Supprime les blocs ``||basic:toujours||`` et ``||basic:au démarrage||``.

## Étape 2

```package

datalogger=github:Microsoft/pxt-microbit

```

Glisse le bloc ``||loops: chaque 500 (ms)||`` dans la zone de programme.

Remplace la valeur ``||loops: 500||`` par le bloc ``||math: 0   x   0||``.

```blocks

loops.everyInterval(0 * 0, function () {
	})

```
