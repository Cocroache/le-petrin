# Le Pétrin, site de boulangerie

Site vitrine d'une boulangerie artisanale fictive de Bourges, avec une page de réservation et une appli de prise de commande en Svelte.  

Ce projet est un devoir pratique de la Formation o'clock. Il sert à mettre en pratique les bases du développement web : HTML, CSS, JavaScript avec Svelte, et Git.  

## Fonctionnalités

- Page d'accueil : présentation de la boulangerie, carte de 6 produits et tableau des horaires

- Page de commande : formulaire de réservation pour le lendemain

- Site responsive : 1, 2 ou 3 colonnes selon la taille de l'écran    

## Appli de commande (Svelte)
- Carte des produits chargée depuis un fichier JSON avec fetch, avec un message pendant le chargement et en cas d'erreur  

- Filtre par catégorie : tout, pains, viennoiseries, pâtisseries   

- Panier : ajout et retrait d'articles, nombre d'articles, message quand le panier est vide   

- Calcul automatique du total et du prix à payer :   
   - 5 % de remise pour une commande à emporter   
   - 1 € de remise avec la carte de fidélité, à partir de 10 € d'achat    

## Technologies utilisées

- HTML5 (balises sémantiques, tableaux, formulaires)

- CSS3 (box model, Flexbox, Grid, position, media queries)

- Svelte 5 avec Vite :   
   - composants et props ($props), avec une fonction transmise du parent à l'enfant   
   - données réactives ($state) et valeurs calculées ($derived)   
   - blocs {#if} et {#each}, liaisons bind:value et bind:checked   
   - chargement des données avec fetch, async/await et onMount   
- Git et GitHub

## Structure du projet
```
le-petrin/
├── index.html                  Page d'accueil
├── commande.html               Page de réservation
├── README.md
├── css/
│   └── style.css               Styles des deux pages
└── app-commande/               Appli de commande en Svelte (projet Vite)
    ├── index.html
    ├── public/
    │   └── produits.json       Données des produits
    └── src/
        ├── main.js             Point d'entrée de l'appli
        ├── app.css             Styles généraux de l'appli
        ├── App.svelte          Composant principal : filtre, panier, total
        └── lib/
            └── CarteProduit.svelte   Carte d'un produit
```

## Lancer le projet

1- Cloner le dépôt :   
   ```
    git clone https://github.com/Cocroache/le-petrin.git 
 ```   

2- Site vitrine : ouvrir index.html dans un navigateur.

3- Appli de commande : il faut Node.js installé.
  ``` 
  cd app-commande
   npm install
   npm run dev
   ```

puis ouvrir l'adresse affichée dans le terminal (en général http://localhost:5173).

## Voir le site en ligne

Lien GitHub Pages : à ajouter une fois le site publié

## Auteur

Jorick Ancillon, en formation Concepteur Développeur d'Applications GitHub : [Cocroache](https://github.com/Cocroache)


