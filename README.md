
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

Node.js est un environnement open-source qui permet de développer des applications multi-plateformes :
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

**`Avantage de l'asynchrone :`**

- Permet de traiter un gros volume de requêtes simultanément de manière efficaces
- Éviter les attentes
- Plusieurs requêtes en même temps
- A l'inverse du PHP qui traite par séquentielle
- Les streams : Traiter les fichiers alors même que son téléchargement n'est pas terminé
![](https://www.alioze.com/wp-content/uploads/2016/11/nodejs-non-bloquant.png)



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
- 
**`Comment l'utiliser :`**
- Utiliser des callback : Très vite n'importe quoi
- Utiliser des promise : Résolvent avec then() et catch() quand erreur
- Utiliser des Generators : Géré par le "yied"
- Utiliser Async / Await : Disponible sous chrome, permet de rendre synchrone un flux asynchrone. Utilise des promise, et renvoient des promise. (La meilleure, utilisable grâce à babel.js)


**`Framework`**
- Express.js : "micro-framewrok" open source, particulièrement flexible
- Meteo.js : full stack, pour applications web synchronisent avec le serveur
- React.js (facebook) : Bibliothèque javaScript pour faciliter la création d'applications web monopage.
- Angulas.js (Google) : Framework open-source dédié au dev d'appli web monopage.
 




# React JS (basé Facebook)
=> Basé sous AngulasJS
=> N'interagit pas sur ²le DOM, crée un virtual DOM
=> Code HTML géré par JavaScript
=> Modifie l'état, modifiant le DOM virtuel, puis injecte DOM virtuel dans réel
=> A chaque modification++ DOM => Compare modifications pour décider si il modifie le DOM réel

⇒ Facebook a crée "Flux" => Redux : 
- Gérer la partie "Etat" => Décrire + modifier 
- Peut interagir avec React JS
