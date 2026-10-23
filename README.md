# Le Pétrin, site de boulangerie

Site vitrine d'une boulangerie artisanale fictive de Bourges, avec une page de réservation et un script de prise de commande en JavaScript.

Ce projet est un devoir pratique de la Formation o'clock. Il sert à mettre en pratique les bases du développement web : HTML, CSS, JavaScript et Git.

## Fonctionnalités

- Page d'accueil : présentation de la boulangerie, carte de 6 produits et tableau des horaires

- Page de commande : formulaire de réservation pour le lendemain

- Appli de commande en Svelte : carte filtrable, panier, calcul du total et des remises, produits chargés avec fetch

- Site responsive, du mobile à l'ordinateur

## Technologies utilisées

- HTML5 (balises sémantiques, formulaires)

- CSS3 (box model, Flexbox, Grid, position, media queries)

- Svelte 5 avec Vite (composants, runes, fetch)

- Git et GitHub

## Structure du projet
```
le-petrin/  
├── index.html        Page d'accueil
├── commande.html     Page de réservation
├── README.md
├── css/
│   └── style.css     Styles des deux pages   
├── images/           Photos des produits   
└── app-commande/     Appli de commande en Svelte (projet Vite)   
```

## Lancer le projet

1- Cloner le dépôt :   
   ```
    git clone https://github.com/Cocroache/le-petrin.git 
 ```   

2- Ouvrir index.html dans un navigateur.   

3- Pour lancer l'appli de commande :
  ``` 
  cd app-commande
   npm install
   npm run dev
   ```

puis ouvrir l'adresse affichée dans le terminal.

## Voir le site en ligne

Lien GitHub Pages : à ajouter une fois le site publié

## Auteur

Jorick Ancillon, en formation Concepteur Développeur d'Applications GitHub : [Cocroache](https://github.com/Cocroache)


