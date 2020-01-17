# Human Centric Lighting

## Présentation

Permet de gérer vos lumières à travers Jeedom pour le quotidien. Le plugin créer un équipement par objet de Jeedom. Il scan tous les équipements avec les types génériques lumière disponible dans l'objet.

Le plugin permet :

- gérer des "ambiances" ou type d'éclairage (lecture, repas, soirée ...) qui correspondent à un éclairage donné (par exemple en lecture, seule la lampe de chevet de la pièce sera allumé à 70% en blanc froid)

- de lier un/des déclencheurs (comme les détecteurs de mouvement) pour activer en automatique un mode

- gérer un timer pour éteindre automatiquement les lumières

- ajouter une sonde de luminosité pour ne pas allumer la lumière quand ce n'est pas nécessaire (avec seuil configurable)

- basculer l'ambiance utilisée par défaut (pour gérer via la présence, les modes, l'heure, le sommeil ...). Exemple : passer en ambiance soirée au coucher du soleil pour l'éclairage automatique. Mais en pouvant toujours passer en ambiance lecture en appuyant sur un interrupteur

- utiliser des valeurs "Circadian Lighting" pour l'éclairage

## Configuration

Des paramètres sont utilisés par le plugin et sont ajustable à plusieurs niveaux (valeur par défaut, page de conf du plugin, page de l'équipement, modal de l'ambiance). La valeur utilisée est connue ainsi :

- valeur présente sur le modal de l'ambiance en premier

- sinon, si définie sur l'équipement, c'est cette valeur qui est précise

- sinon, si définie sur la page de configuration du plugin

- par défaut si rien d'autre n'est défini, c'est la valeur par défaut (visible sur la page de configuration)

Ainsi, si on défini une durée d'allumage de 2mn sur la page de configuration, et 20mn pour le salon, c'est bien 20 qui sera utilisé pour la lumière du salon.

Les paramètres disponibles :

- Timer d'extinction automatique

- Niveau de luminosité pour allumage sur détecteur

- Information du niveau de luminosité

- Paramètres "Circadian Lighting"

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Non.
> tu es un kevin la suite ici (kevin.md).

## Changelog

[Voir la page dédiée](changelog.md).
