# Tutoriel HCL ![Work in progress]

Si tu es sur cette page, c'est que tu rencontres quelques difficultés.

Voici un ensemble d'erreurs pouvant facilement être corrigées.

## Sommaire
 - [STATE est une chaine](#state-est-une-chaine)
 - [STATE manquant](#state-manquant)
 - [FAQ](#faq)

## STATE est une chaine

![STATE est une chaine](imgs/img1.png)

Cela indique que la configuration du sous-type de votre commande état n'est pas correctement configurée. 
Dans la majorité des cas, elle est configurée en _autre_ au lieu de _numérique_ ou _binaire_. Corriger la configuration du sous type et relancer le scan HCL.

## STATE manquant

![STATE manquant](imgs/img2.png)

Cela indique que la configuration _générique type_ est incorrecte sur la commande _etat_ de votre lampe.
ex :

![STATE manquant](imgs/img3.png)

Corriger la configuration _générique type_  et relancer le scan HCL.


## FAQ
