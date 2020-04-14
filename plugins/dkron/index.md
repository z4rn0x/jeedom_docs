# Time Manager

## Présentation

Time Manager permet 3 types de fonctions principales :

- Créer des actions retardées

- Créer des actions récurrentes

- Créer des planifications dépendantes d'une commande information donnant un horaire

Le point principal est que le plugin permet de gérer le séquencement à la seconde.

## Configuration

Il n'y a pas de configuration générale.

### Configuration de l'équipement

On créer un équipement et on choisit son type (actions retardées, actions récurrentes, actions planifiées)

Puis on peut choisir un décalage en temps. Il s'exprime en format 00:00:00 pour heures, minutes, secondes. Si c'est juste des secondes, on saisit directement 00, par exemple 35 pour 35s. Si le décalage doit se faire en négatif, on saisit -00:00:00

### Configuration des actions

Pour chaque action créée, on peut y rattacher une ou plusieurs actions de Jeedom ainsi qu'un scénario facultatif.

#### Type d'action

Il faut bien paramétrer le type d'action. Il faut être cohérent avec les actions sélectionnées. Une action couleur permettra de définir une couleur à l'utilisation et de la passer à toutes les commandes sous-jacente. Les actions "autre" ne seront pas gênées.

Si vous choisissez "message", vous avez moyen de passer dans le champ titre les options pour toutes actions. Par exemple : color="ffffff";title="mon titre";select="choix1"

Il faut bien séparer par ; pour que tout soit passer vers les actions déclenchées

#### Condition

Il est possible d'utiliser le champ condition pour valider qu'une expression est vraie pour éxécuter les actions déclenchées

## Fonctionnement

Pour le type action retardée, il s'agit d'utiliser les actions normalement, simplement elles se feront avec le décalage prévu. Par exemple, je créer une action "Extinction Minutée" sur un équipement avec un décalage de 45s. Je sélectionne deux actions extinction de mes lampes. En utilisant "Extinction Minutée" dans un scénario ou sur le dashboard ... mes deux commandes seront éxécuter 45s plus tard.

Pour les actions récurrentes, le champ durée est alors la durée de récursivité. On peut par exemple saisir "45s", une planification sera mise en place et éxécutera toutes les actions créées à l'interval choisit.

Pour l'action planifiée, il faut renseigner la commande donnant une heure quotidienne. Une planification y sera appliquée avec le décalage saisi. Toutes les actions créées seront déclenchées par cette planification.

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Il s'appuie sur les API de dkron géré par le plugin. C'est donc sur le réseau local.

## Changelog

[Voir la page dédiée](changelog.md).
