# Zoneminder, CCTV Open Source

## Présentation

Ce plugin permet l'interconnexion avec un Zoneminder.

Zoneminder est "le" logiciel de CCTV Open Source. Il est présent depuis des années et à peu près seul. Quelques produits sont arrivés avec le Pi par exemple mais se limitent souvent à gérer un fluxion de motion.

Zoneminder permet de connecter un très large panel de camera IP mais aussi d'autres connexions (USB, via CCTV ...)

Une fois les camera ajoutées, on peut configurer différents rôles (motion, monitor ...) et appliquer des zones de détection de mouvement mais aussi avec les travaux de plugins en cours de reconnaissance faciale ou plaques d'immatriculation

Le plugin permet de récupérer les cameras déclarées dans Zoneminder, les déclarer dans le plugin Camera de Jeedom et récupérer les events Zoneminder.

## Configuration

Le plugin nécessite de rentre les informations de connexion à Zoneminder

 * adresse Zoneminder (sous la forme http://ipzm, avec le http:// et sans / à la fin)

 * complément d'adresse (sous la /zm, avec le / au début et sans / à la fin, seulement si votre adresse complète zoneminder est par exemple http://ipzm/zm)

 * compte à utiliser

 * mot de passe

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Non, le plugin pilote Zoneminder directement

>Je n'arrive pas à synchroniser correctement ?

Il faut bien remplir l'adresse sous la forme http://ipzoneminder et remplir le champ complément si votre installation le nécessite (normalement /zm par défaut)

En cas d'installation derrière un reverse où bien que tout Zoneminder est dans /rm ou /zoneminder par exemple, il faut l'iniquer dans l'adresse et laisser le complément vide

## Changelog

[Voir la page dédiée](changelog.md).
