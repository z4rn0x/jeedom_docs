# Mir:ror by Violet

## Présentation

Ce plugin permet d'utiliser des lecteurs RFID Mir:ror de Violet.

## Configuration

Sur la page de configuration, il faut renseigner le port à utiliser (par défaut /dev/hidraw1)

L'équipement sera créer automatiquement avec en commandes :

  * une position du lecteur (binaire à 1 quand il est face visible, 0 quand retourné)

  * un indicateur de RFID pour chaque puce présentée (binaire à 1 si présent sur le lecteur, 0 quand enlevé)

## FAQ

>Puis-je utiliser d'autre lecteurs RFID que le Mir:ror ?

Non le plugin ne gère que ce lecteur

## Changelog

[Voir la page dédiée](changelog.md).
