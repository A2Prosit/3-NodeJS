
# Prosit 5.03 - NODE.JS

## Mots clés
 * Node.js : /
 * React : /
 * Mode synchronisé : <=> Mode asynchrone
 * Framework : Boite à outils 
 * jsx : Extension pour reactJS, HTML dans le Javascript (gérer du HTML via du Javascript)
 * Chargement bloquant : /

## Analyse du besoin
### Quoi ?
Enpécher les serveurs de tomber à cause du trafic

### Comment ?
En les passant en asynchrone

### Pourquoi ?
Pour réduire la surchage et que les serveurs ne crashent pas

## Contraintes
Aucunes

## Problématique
 * Comment éviter les crash serveur en utilisant le framework Node.js et/ou React ?
 * Comment réduire la charge des serveurs en les passant en mode asynchrone (grâce aux framework node et react) ?

## Généralisation
 * *Prévention*
 * *Optimisation*
 * **MCO**
 * *Implementation*

## Hypothèse
 * Node.js permet l'exécution du JS coté serveur
 * Node.js permet l'assignation asynchrone
 * .jsx = extension des fichiers
 * Node.js fonctionne avec des modules
 * NPM est le gestionnaire de module de Node.js
 * React est un autre framework

## Plan d'Action
### Etudes
 * Etudier Node.js
 * Etudier React
 * Etudier serveurs synchrones / asynchrones

### Réalisation
 * Réaliser le workshop

# 1- NodeJS 

Node.js est un **environnement open-source** qui permet de développer des applications multi-plateformes :
- Basé sur V8 de google (moteur JS)
- Ecriture côté client et serveur (plus serveur) ⇒ Concurent PHP & Java

On retrouve :
- Possibilité de faire de **l'asynchrone**
- Même syntaxe pour front-end et bakc end (augmenter la productivité)
- Haute performances
- Configuration facile
- Très grande communauté (plus importante sous GitHub)
- De nombreux modules grâce au NPM (Node Package Manager)
- Supporte les **websockets**

**`Les websockets`**
Une action effectuée par un utilisateur se répercute directement sur les autres utilisateurs,  très utile pour le temps réel. (ex : blackfriday, chat facebook...)

**`Où l'utiliser`**

On l'utilise dans : 
- E-commerce
- Paiements
- Services en temps réel (chats / blackfriday...)
- Média Sociaux
- Jeux vidéo
- Sondage
- Notification
- Système de download

# 2 - React JS

- Développé par Facebook (2013), Instagram, Netflix...
- Basé sous AngulasJS
- C'est une librairie et non un framework
- Utilisé pour de très grands volumes d'informations
- Faciliter la création d'application web monopage

**`Comment ça marche`**
- Doit travailler avec d'autres framework, comme AngularJS.
- .jsx : HTML dans le Javascript (gérer du HTML via du Javascript)
- Permet de créer des composants  qui peuvent changer d'états <=> Interfaces (càd la vue)
- Principe "d'embriquement de composants" (composant dans composants)
- Composants réutilisables
- Permet de créer des applications mobiles.
- Utilisation de l'algorithme de la réconciliation (VirtualDOM)
	-	=> Modifie l'état, modifiant le DOM virtuel, puis injecte DOM virtuel dans réel
	-	=> A chaque modification++ DOM => Compare modifications pour décider si il modifie le DOM réel
![](https://s3.amazonaws.com/media-p.slid.es/uploads/44933/images/1881608/reactjs-virtual-dom-real-dom.png)


**NB :** Facebook a créer **"Flux"**, c'est un pattern proposé par Facebook qui est une alternative au MVC.
![](http://blog.soat.fr/wp-content/uploads/2016/04/flux-diagram-white-background-768x383.png)
Globalement : 

Lorsqu'un utilisateur fais une action **Action Creators**, les actions sont envoyés vers le **dispatcher**. On le **store** qui s'est enregistré auprès de lui, lui permettant de lancer des **callbacks** (des appels uniques).

En lançant un **callback**, on va mettre à jour les données du **store** en exécutant les règles associés au callback, c'est lui qui gère les états de l’application. On a également un évènement qui est lancé, pour avertir la vue du changement d'état, et qui va lui demander de mettre à jour l'affichage, exactement comme le pattern Observer / Observable.

# 3- Les framework JS 

**`Avantages à utiliser un framework JS`**
- Efficace -> Gain de temps énorme
- Sécurité : Nouveaux tests réalisés
- Cout : Complètement gratuit, clés en main pour faciliter la vie des devs

Voici une liste exhaustive 
- **Angulas.js** (Google) : Open source, permet principalement de développer des pages web.
- **vue.js**  : Open source, progressifs, pour construire des interfaces utilisateurs. Il peut aussi s'en servir pour faire des pages applicatives seules en web. Sa particularité est la liaison bidirectionnelle, c'est le meilleur choix pour le dév. rapide de solutions multiplateforme.
- **Ember.js** : Open-source, meilleur framework JS pour applis web, architecture MVC.
- **Meteor.js** : Open-source, basé sur Node.js, développement clé en main, applications mobiles pure JS, couvre toutes les phases du cycle de dév, full stack, architectures client-serveur avec possibilité de faire des requêtes en étant déconnecté du serveur.
- **Express.js** : Open source,  basé sur Node.js, particulièrement flexible, relativement minimaliste, permettant d'étendre ses fonctionnalités via des plugins.


# 4- Principe de l'Asynchrone
![](https://res.cloudinary.com/smooth/image/upload/c_scale,w_800,q_auto,f_auto/v1504086120/ff8zien7jco4safoifpi)

**`Avantage de l'asynchrone :`**

- Permet de traiter un gros volume de requêtes simultanément de manière efficaces
- Éviter les attentes
- Plusieurs requêtes en même temps
- A l'inverse du PHP qui traite par séquentielle
- Les streams : Traiter les fichiers alors même que son téléchargement n'est pas terminé
![](https://www.alioze.com/wp-content/uploads/2016/11/nodejs-non-bloquant.png)

**`Comment utiliser l'asynchrone:`**
- Callback : Très vite n'importe quoi, ne sont pas appelés avant la fin du parcours de la boucle.
- Promise (promesses) : Résolvent avec then() et catch() quand erreur. C'est un objet qui représente la complétion ou l'échec d'une opération asynchrone. On y attache des callback.
- Generators : Géré par le "yied"
- Async / Await : Disponible sous chrome, permet de rendre synchrone un flux asynchrone. Utilise des promise, et renvoient des promise. (La meilleure, utilisable grâce à babel.js)

**`Comment marche l'asynchrone :`**
![](https://www.developpez.net/forums/attachments/p216799d1/a/a/a)
**1 -** Pile d'exécution, ou "Call Stack" quui fait partie de l'API du navigateur, prise en compte de manière asynchrone.
**2 -** On crée un thread avec un délai, et dès qu'il est finis, il s'en va dans la Callback Queu
**3 -** Si pile exécution vide, on envois dans la pile d'exécution.
