# Mail Listener, surveiller une boîte mail et utiliser les propriétés des mails entrants dans Jeedom

Ce plugin permet d'avoir Jeedom qui se connecte à une boîte mail et reste à l'écoute des mails entrants.

Sur un nouvel email, il indiquera les propriétés de celui-ci qui seront visibles et utilisables dans Jeedom

# Configuration du plugin

Il n'y a pas de configuration du plugin

## Configuration d'un équipement

Il est nécessaire de fournir les informations d'accès à la boîte mail :

  Compte : le compte à utiliser (suivant la boîte, ça peut être par exemple le nom devant @ ou bien toute l'adresse)

  Mot de passe : le mot de passe quoi

  Serveur : l'adresse du serveur mail

  Port : le port du serveur imap

  Pièces jointes : indique si les pièces jointes doivent être traitées

La sauvegarde de l'équipement va automatiquement faire démarrer l'écoute de la boîte mail


## Informations d'un équipement

Les informations suivantes sont disponibles :

  Expéditeur : l'expéditeur du mail

  Sujet : le sujet

  Corps : le corps du mail en format textarea

  HTML : l'équivalent en HTML

  Pièce jointe : quand les pièces jointes sont traitées, donne le chemin de sauvegarde de la pièce jointe (pour un traitement par datatransfert par exemple)

Les différentes informations sont de type évènementiel dès qu'un mail est reçu, l'information est enregistrée. On peut donc utiliser les différentes infos en déclencheur de scénario et en testant leur valeur.

# FAQ

Est-ce que je peux envoyer un mail avec ce plugin ?

> Non, le plugin n'a vocation qu'à rester à l'écoute d'une boîte mail et d'indiquer ce qui y arrive.

Comment utiliser ce plugin en scénario ?

>Exemple, d'un côté via le plugin mail, on envoie un mail du style :
Titre : Saisie Energie
Texte :
#Eau#=
#ECS#=

Ce mail est mis en envoi par un agenda (par semaine, mois ...)

Cette boîte mail qui envoie est en surveillance par mail listener également
Un scénario avec en déclencheur le mail listener et un test sur le titre qui contient "Saisie Energie" précédemment rentré et on peut récupérer les informations

En gros, un SI pour vérifier que le titre contient la Saisie Energie
Après, on découpe le corps ligne par ligne et on regarde à quoi correspond chaque ligne et on assigne

# Troubleshoting

Je n'ai pas d'informations qui remontent

> Il faut bien vérifier les paramètres fournis et les logs

## Changelog

[Voir la page dédiée](changelog.md).
