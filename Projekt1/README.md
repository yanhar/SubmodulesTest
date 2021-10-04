# Filter bei GitHub hinzufügen

Funktioniert im Moment nicht korrekt, da bei jedem Wechsel des Branches die Filter auf allen Dateien angewendet werden.

## Edit gitconfig
1. gehe in die globale gitconfig:

```
C:\Benutzer\<Benutzername>\.gitconfig
```

2. Füge deinen Filter ein:

```
[filter "header"]
	smudge = perl X:/Pfad/zu/Repo_Sonstige_Skripte/Filter/header.smudge
	clean = perl X:/Pfad/zu/Repo_Sonstige_Skripte/Filter/header.clean
```

## Edit gitattributes
1. Erstelle oder bearbeite die `.gitattributes` Datei
2. Füge für jede Datei die mit einem Header versehen sein soll den Filter hinzu

```
*.py filter=header
*.pl filter=header
*.java filter=header

```

## Edit header.clean
1. Hier muss der Benutzername der Variable `$author` angepasst werden

```
my $author = "benutzername";
```

## Aufbau Header
Damit der Header in allen Dateien funktioniert sollte er folgende Form haben

```
#! /usr/bin/perl -w
# Dateiname
# Version x
#
# Erstellt am xx.xx.xxxx
# von benutzer
# geupdatet am $DATE$
# von $AUTHOR$
```
