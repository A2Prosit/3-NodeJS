# Prosit 5.03 - NODE.JS

## Mots clés
 * Node.js : framework web pour des des app monopage
 * React : biblio 
 * Mode synchronisé : on attend qu'action A soit finie avec de faire l'action B 
 * Framework
 * jsx : extension de react
 * Chargement bloquant: synchrone (on attends la fin avant de continuer)

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

#### **Etudier Node.js**

Basé sur le V8 de Google, avec Node l’écriture se fait en JavaScript non plus uniquement côté client, mais également côté serveur. Il vient ainsi concurrencer les autres langages serveurs comme PHP ou Java.

avantages et fonctionnalités:

* gestion I/O non-bloquante permettant la réalisation d'actions asynchrones
* même langage pour le front-end et le back-end: JS
* hautes perf
* config facile
* communauté active
* plein de modules dispo (apparement "centaines de milliers"), facile à installer avec Node Package Manager
* les stream: on peut traiter un fichier alors que le dl n'est pas fini

étant asynchrone on a pas besoin d'attendre qu'une action longue soit terminée pour en lancer une autre contrairement à PHP, nodejs peut donc exécuter plusieurs actions en même temps


cas d'utilisation de node.js:

* e-commerce
* traitement de paiements
* services en temps réel
* réseaux sociaux
* jeux video
* sondage
* notif
* dl


installation:

Après avoir installé Node.js, les développeurs ont le choix entre plusieurs frameworks pour les aider à développer des sites web rapides, scalables et en temps réel:

* express.js : un micro-framewor open-source sous licence MIT, très flexible
* meteor.js : framework full-stack conçue pour simplifier la créatin d'application web qui se synchro en temps réel avec le serv
* React.js (Fb) : biblio JS conçue pour faciliter la création d'app web monopage
* Angular.js (google) : un framework JS open-source dédié au dev d'app web monopage (comme react), il permet de faire de l'html dynamique

hello world:

		var http = require('http');

		//create a server object:
		http.createServer(function (req, res) {
		  res.write('Hello World!'); //write a response to the client
		  res.end(); //end the response
		}).listen(8080); //the server object listens on port 8080

#### **Etudier React**

lib qui se focus sur la partie vue. 
React fonctionne avec un système d'état. Si on mofiie l'état, le code html change. Il n'intergait pas avec le DOM mais avec un virtual DOM qu'il va injecter dans le DOM du navigateur. Lorsqu'on modifie l'état il regénère le VDOM et le compare au précédent puis modif le DOM, il est donc + perf <- algo de réconcilliation

installation:

	npm install -g create-react-app
	create-react-app my-app

	cd my-app
	npm start


ou en stand alone avec ce fichier html:

``` HTML
	<!DOCTYPE html>
	<html>
	  <head>
	    <meta charset="UTF-8" />
	    <title>Hello World</title>
			    <script src="https://unpkg.com/react@16/umd/react.development.js"></script>
		    <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
		    <script src="https://unpkg.com/babel-standalone@6.15.0/babel.min.js"></script>
	  </head>
	  <body>
	    <div id="root"></div>
	    <script type="text/babel">
	
	      ReactDOM.render(
	        <h1>Hello, world!</h1>,
	        document.getElementById('root')
	      );

	    </script>
	    <!--
		      Note: this page is a great way to try React but it's not suitable for production.
		      It slowly compiles JSX with Babel in the browser and uses a large development build of React.

		      To set up a production-ready React build environment, follow these instructions:
	      * https://reactjs.org/docs/add-react-to-a-new-app.html
	      * https://reactjs.org/docs/add-react-to-an-existing-app.html

		      You can also use React without JSX, in which case you can remove Babel:
	      * https://reactjs.org/docs/react-without-jsx.html
	      * https://reactjs.org/docs/cdn-links.html
	    -->
	  </body>
	</html>
```

code minimal (presque minimal):


``` javascript
	import React, { Component } from 'react';
	import logo from './logo.svg';
	import './App.css';
	
	class App extends Component {
	  render() {
	    return (
	      <div className="App">
	        <header className="App-header">
	          <img src={logo} className="App-logo" alt="logo" />
	          <h1 className="App-title">Welcome to React</h1>
	        </header>
	        <p className="App-intro">
	          To get started, edit <code>src/App.js</code> and save to reload.
	        </p>
	      </div>
	    );
	  }
	}
	export default App;
```
apparement on peut le faire avec ça:

``` Javascript

	ReactDOM.render(
	  <h1>Hello, world!</h1>,
	  document.getElementById('root')
	);
	
```
mais moi j'y arrive pas

solutions d'asynchrone avec nodejs:

1. Callbacks

Typiquement, une personne qui commence en Node.js va commencer en général avec les Callbacks. C’est simple au départ mais cela devient très vite n'importe quoi... c'est ce qu'on appelle les Callback Hell (on callback dans une fonction call back, etc)

 Il est courant en JavaScript que les callbacks soient des fonctions anonymes passées en paramètre et définies au moment même de l'appel de la fonction asynchrone.

Librairie de gestion de Callbacks : Async.js
``` Javascript

	async.series({  
	  one: function (callback) {
	   fs.readFile('file1.txt', 'utf8', (err,data) => callback(err, data))
	  },
	  two: function (callback){
	   fs.readFile('file2.txt', 'utf8', (err,data) => callback(err, data))
	  }
	}, (err, results) => {
	  // results = {one: "text file1", two: "text file2"}
	})

``` 


un callback est un fonction qui est exécutée lorsqu'une fonction asynchrone est terminée. ex:

```Javascript
	var get = function(url,success){
	
		var xhr = new window.XMLHttpRequest()

		xhr.onreadystatechange = function(){
			if(xhr.readyState == 4){
				success(xhr.responseText)
			}
		}
		xhr.open('GET',url,true)
		xhr.send()
	}

	var getPosts = function(){
		get('www.google.com',function(response){
			console.log(response)
		}
	}
```
ici la fonction getPost charge une 

2 . Promise

Beaucoup mieux que les callbacks, les promises nous permettent de gérer l'asynchrone plus intelligemment. Elles se résolvent avec .then() ou .catch() quand il y a une erreur.
Le concept des Promises n'est pas facile à comprendre donc souvent on se retrouve à les utiliser comme les callbacks et on crée ce qu'on appelle une Promise Pyramide of Doom.

	var promise1 = new Promise(function(resolve, reject) {
	  setTimeout(resolve, 100, 'foo');
	});

	console.log(promise1);

return resolve si elle se fini et reject en cas de problème.

Librairie de gestion de Promises : Bluebird

``` Javascript

	Promise.props({  
	  pictures: getPictures(),
	  comments: getComments(),
	  tweets: getTweets()
	}).then((results) => {
	  // results = {pictures: …, comments: …, tweets: ….}
	}).catch((err) => console.error(err))
```
3 . Generators

Les Generators sont arrivés en ES2015 et sont aujourd'hui un des concepts les plus complexes en JavaScript, mais sont très puissants quand ils sont bien utilisés. Gérer l'asynchrone avec les Generators c'est très simple, ça se rapproche beaucoup de Async / Await.

Librairie de gestion de Generators : Co

``` Javascript

	co(function* () {  
	 const user = yield db.Account.current()
	 const comments = yield db.Comments.find(user.id)
	 return {user, comments}
	}).then((results) => {
	 // results = {user: ..., comments: ...}
	}, (err) => {
	 console.error(err)
	})
```
4 . Async / Await

Fonctionnalité très attendue de cette année en JavaScript. Déjà accessible sur Chrome, elle permet de rendre synchrone un flux asynchrone

	async function myFunction() {
	  await aPromise;
	  // on n'arrivera à cette ligne que lorsque "aPromise" sera résolue
	}

Librairie de gestion Async / Await : Pas besoin de librairie

``` Javascript

	async function getTweets() {  
	 const user = await db.getCurrentUser()
	 const tweets = await db.getUserTweets(user.id)
	 return {userName: user.name, tweets}
	}

	getTweets()  
	 .then((results) => {
	  // results = {userName: ..., tweets: ...}
	 })
	 .catch((err) => console.log(err))
```

Reux (flux) : permet de gérer la partie état

 * Etudier serveurs synchrones / asynchrones
**synchrone** PHP est synchrone : l'action A doit être terminée avant de commencer l'action B
**asynchrone**
permet d'éviter d'attendre. on peut effectuer plusieurs requêtes en mm temps

\*diagramme serv js*

#### Autres frameworks:

Ember.js: en 2015, Ember a été nommé le meilleur framework javascript pour les applications web, laissant derrière lui React et AngularJS. Aujourd’hui, il bénéficie d’une immense communauté en ligne, de mises à jour régulières et d’un grand nombre de bonnes pratiques JavaScript pour garantir une expérience ultime dès le départ.

Meteor.js : Meteor est parmi les framework JavaScript les plus populaires, bien équipé avec des tonnes de features pour le développement back-end, le rendu front-end, la gestion de base de données

Vue.js : introduit en 2016 Ember, React et Angulaire, mettant tout cela dans un paquet pratique. Il est prouvé être plus rapide et plus fin, comparé à React et Angulaire 2.0.

### Réalisation
 * Réaliser le workshop

q1: on a le cintenu du fichier Json (une liste d'utilisateurs) qui s'affiche dans la console*

q2: rep est undifined
