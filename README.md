
# Prosit 5.03 - NODE.JS

## Mots clés
 * Node.js
 * React
 * Mode synchronisé
 * Framework
 * jsx
 * Chargement bloquant

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
![](https://res.cloudinary.com/smooth/image/upload/c_scale,w_800,q_auto,f_auto/v1504086120/ff8zien7jco4safoifpi)

Node.js est un **environnement open-source** qui permet de développer des applications multi-plateformes :
- Basé sur V8 de google (moteur JS)
- Ecriture côté client et serveur ⇒ Concurent PHP & Java

On retrouve :
- Possibilité de faire de **l'asynchrone**
- Même syntaxe pour front-end et bakc end (augmenter la productivité)
- Haute performances
- Configuration facile
- Très grande communauté (plus importante sous GitHub)
- De nombreux modules grâce au NPM (Node Package Manager)
- Supporte les websockets

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

- Basé sur Facebook (2013), Instagram, Netflix...
- Basé sous AngulasJS
- C'est une librairie et non un framework
- Utilisé pour de très grands volumes d'informations

**`Comment ça marche`**

- .jsx : HTML dans le Javascript (gérer du HTML via du Javascript)
- Permet de créer des composants <=> Interfaces
- Principe "d'embriquement de composants" (composant dans composants)
- Composants réutilisables
- Utilisation de l'algorithme de la réconciliation (VirtualDOM)
	-	=> Modifie l'état, modifiant le DOM virtuel, puis injecte DOM virtuel dans réel
	-	=> A chaque modification++ DOM => Compare modifications pour décider si il modifie le DOM réel
![](https://s3.amazonaws.com/media-p.slid.es/uploads/44933/images/1881608/reactjs-virtual-dom-real-dom.png)

- Permet de créer des applications mobiles.


**OPTIONNEL - Extention : "Flux"**
⇒ Facebook a crée "Flux" => Redux : 
- Gérer la partie "Etat" => Décrire + modifier 
- Peut interagir avec React JS

# 3- Les framework JS 

**`Avantages à utiliser un framework JS`**
- Efficace -> Gain de temps énorme
- Sécurité : Nouveaux tests réalisés
- Cout : Complètement gratuit, clés en main pour faciliter la vie des devs

Voici une liste exhaustive 
- **Angulas.js** (Google) : Framework open-source dédié au dev d'appli web monopage.
-** Vue.JS** : liaison bidirectionnelle, meilleurs choix pour le développement rapide de solutions multiplateforme.
- **Ember.js** : meilleur framework JS pour applis web.
- **Meteor.js** : Développement clé en main, applications mobiles pure JS, couvre toutes les phases du cycle de dév, full stack, pour applications web synchronisent avec le serveur
- **Express.js** : "micro-framewrok" open source, particulièrement flexible
- **React.js** (facebook) : Bibliothèque javaScript pour faciliter la création d'applications web monopage.



# 4- Principe de l'Asynchrone

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


