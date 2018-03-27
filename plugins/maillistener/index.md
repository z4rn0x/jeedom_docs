# Mail Listener, surveiller une boite mail et utiliser les propriétés des mails entrants dans Jeedom

Ce plugin permet d'avoir Jeedom qui se connecte à une boite mail et reste à l'écoute des mails entrants.

Sur un nouvel email, il indiquera les propriétés de celui-ci qui seront visible et utilisable dans Jeedom

# Configuration du plugin

Il n'y a pas de configuration du plugin

## Configuration d'un équipement

Il est nécessaire de fournir les informations d'accès à la boite mail :

  Compte : le compte à utiliser (suivant la boite, ca peut être par exemple le nom devant @ ou bien toute l'adresse)

  Mot de passe : le mot de passe quoi

  Serveur : l'adresse du serveur mail

  Port : le port du serveur imap

  Pièces jointes : indique si les pièces jointes doivent être traitées

La sauvegarde de l'équipement va automatiquement faire démarrer l'écoute de la boite mail


## Informations d'un équipement

Les informations suivantes sont disponibles :

  Expéditeur : l'expéditeur du mail

  Sujet : le Sujet

  Corps : le corps du mail en format textarea

  HTML : l'équivalent en HTML

  Pièce jointe : quand les pièces jointes sont traitées, donnent le chemin de sauvegarde de la pièce jointe (pour un traitement par datatransfert par exemple)

Les différentes informations sont de type évènementiel dès qu'un mail est recu l'information est enregistrée. On peut donc utiliser les différentes infos en déclencheur de scénario et en testant leur valeur.

# FAQ

Est-ce que je peux envoyer un mail avec ce plugin ?

> Non, le plugin n'a vocation qu'à rester à l'écoute d'une boite mail et d'indiquer ce qui y arrive.

Comment utiliser ce plugin en scénario ?

>Exemple, d'un côté via le plugin mail on envoit un mail du style :
Titre : Saisie Energie
Texte :
#Eau#=
#ECS#=

Ce mail est mis en envoi par un agenda (par semaine, mois ...)

Cette boite mail qui envoit est en surveillance par mail listener également
Un scénario avec en déclencheur le mail listener et un test sur le titre qui contienne "Saisie Energie" précédemment rentré et on peut récupérer les informations

En gros, un SI pour vérifier que le titre contient la Saisie Energie
Après on découpe le corps ligne par ligne et on regarde à quoi correspond chaque ligne et on assigne

# Troubleshoting

Je n'ai pas d'informations qui remontent

> Il faut bien vérifier les paramètres fournis et les logs

## Changelog

[Voir la page dédiée](changelog.md).
