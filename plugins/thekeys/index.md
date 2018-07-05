# The Keys

## Présentation

Ce plugin permet d'interconnecter Jeedom avec vos serrures The Key.

The Keys propose :

- serrures (le plugin les récupère de votre compte)

- boutons BLE (le plugin permet de gérer l'accès avec les serrures)

- gateway réseau (le plugin permet de l'utiliser pour les actions directes sur les serrures)

- digicode (le plugin permet de gérer le statut des accès avec les serrures)

- application mobile (le plugin permet de gérer le partage des serrures avec les téléphones)

## Configuration

### Configuration du plugin

Il faut saisir votre compte The Keys dans la page de configuration du plugin.

Votre nom d'utilisateur est le numéro de téléphone commençant par +33 sans le 0 et le mot de passe celui de l'app.

### Configuration des équipements

Il y a 5 types d'équipements disponible, tous ne fonctionnent pas pareil dans Jeedom

- serrure : les serrures sont créées automatiquement par la configuration générale du plugin
  les infos de statut et batterie sont disponible
  deux actions verrouillage et déverouillage sont créées pour chaque gateway ajouter

- gateway : la gateway est un équipement ajouté manuellement dans le plugin avec son IP et son ID du QRcode (se référer pour ce dernier au papier fourni avec et sous le QRcode il y a 3 chiffres + l'ID qu'il faut saisir)
  une information de présence online est disponible, ainsi qu'une action refresh qui rescanne les serrures alentour

- bouton : les boutons d'accès BLE doivent être ajoutés manuellement avec leur ID
  pour chaque serrure, le bouton aura une information de statut du partage permettant d'actionner la serrure, et les deux actions d'activation et désactivation du partage

- téléphone : le plugin permet d'ajouter un autre utilisateur à qui on souhaite partager des serrures, l'ajout est manuel avec le numéro de téléphone (commencant par +33)
  même fonctionnement que les boutons

- digicode : les équipements digicode sont créés automatiquement, un équipement est créé par partage de l'app (donc un meme digicode peut etre présent plusieurs fois sur une meme serrure s'il a des codes différents)
  ensuite le fonctionnement est identique aux boutons

Important : plugin fonctionnement pour les gateway, bouton, téléphone à condition qu'il n'y ait qu'un partage permanent avec chaque. Il faut laisser le plugin le gérer

Pour le digicode, il faut créer les partages permanents directement depuis l'app en choisissant le code dans ce cas particulier

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Oui sur la gateway locale (et le cloud pour scanner les équipements existants sur le compte).

## Changelog

[Voir la page dédiée](changelog.md).
