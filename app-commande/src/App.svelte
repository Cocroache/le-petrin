<script>
  import CarteProduit from "./lib/CarteProduit.svelte";


const produits = [
  { id: 1, nom: "Baguette tradition", prix: 1.30, categorie: "pain", nouveau: false },
  { id: 2, nom: "Pain de campagne", prix: 3.80, categorie: "pain", nouveau: false },
  { id: 3, nom: "Croissant", prix: 1.20, categorie: "viennoiserie", nouveau: false },
  { id: 4, nom: "Pain au chocolat", prix: 1.40, categorie: "viennoiserie", nouveau: false },
  { id: 5, nom: "Éclair au café", prix: 2.90, categorie: "patisserie", nouveau: true },
  { id: 6, nom: "Tarte aux pommes", prix: 3.50, categorie: "patisserie", nouveau: true }
];
let categorie = $state("tout")
let produitsAffiches = $derived.by(() => {
  if (categorie === "tout") { 
    return produits
  }
  const resultat = []

 
for (let produit of produits){
    if (produit.categorie === categorie) {resultat.push(produit)}
}
 return resultat
});

</script>
<header>
    <h1 class="title-page">Commander au Pétrin</h1>
</header>
<main>
<section class="Selection">
<button onclick={() => categorie= "tout"} class:actif={categorie === "tout"}>Tout</button>
<button onclick={() => categorie= "pain"} class:actif={categorie === "pain"}>Pains</button>
<button onclick={() => categorie= "viennoiserie"} class:actif={categorie === "viennoiserie"}>Viennoiseries</button>
<button onclick={() => categorie= "patisserie"} class:actif={categorie === "patisserie"}>Pâtisseries</button>
</section>



  <div class="container">
      {#each produitsAffiches as produit (produit.id) }
  <CarteProduit nom={produit.nom} prix={produit.prix} nouveau={produit.nouveau}/>
  {/each}
  
  
  </div>
</main>




<style>
.actif{
  background-color:#D6BCFA;
}
.container{
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}
.Selection{
  padding: 20px;
  gap: 20px;
}
body{
  background-color: #F8E2E2;
}
</style>