<script>
  import { onMount } from "svelte";
  import CarteProduit from "./lib/CarteProduit.svelte";

  
  let produits = $state([]);
  let chargement = $state(true);
  let erreur = $state(null);
  let categorie = $state("tout");
  let panier = $state([]);
  let mode = $state("sur place");
  let fidele = $state(false);

  
  let produitsAffiches = $derived.by(() => {
    if (categorie === "tout") {
      return produits;
    }
    const resultat = [];
    for (let produit of produits) {
      if (produit.categorie === categorie) {
        resultat.push(produit);
      }
    }
    return resultat;
  });

  let totalPanier = $derived.by(() => {
    let somme = 0;
    for (let produit of panier) {
      somme = somme + produit.prix;
    }
    return somme;
  });

  let prixFinal = $derived.by(() => {
    let final = totalPanier;
    if (mode === "emporter") {
      final = totalPanier * 0.95;
    }
    if (fidele === true && totalPanier > 10) {
      final = final - 1;
    }
    final = Math.round(final * 100) / 100;
    return final;
  });

 
  async function chargerProduits() {
    chargement = true;
    erreur = null;
    try {
      const reponse = await fetch("/produits.json");
      if (!reponse.ok) throw new Error("Erreur " + reponse.status);
      produits = await reponse.json();
    } catch (e) {
      erreur = e.message;
    } finally {
      chargement = false;
    }
  }

  function ajouter(produit) {
    panier.push(produit);
  }

  function retirer(index) {
    panier.splice(index, 1);
  }

  onMount(chargerProduits);
</script>

<header>
  <h1 class="title-page">Commander au Pétrin</h1>
</header>

<main>
  <section class="selection">
    <button onclick={() => categorie = "tout"} class:actif={categorie === "tout"}>Tout</button>
    <button onclick={() => categorie = "pain"} class:actif={categorie === "pain"}>Pains</button>
    <button onclick={() => categorie = "viennoiserie"} class:actif={categorie === "viennoiserie"}>Viennoiseries</button>
    <button onclick={() => categorie = "patisserie"} class:actif={categorie === "patisserie"}>Pâtisseries</button>
  </section>

  {#if chargement}
    <p>Chargement de la carte...</p>
  {:else if erreur}
    <p>Impossible de charger la carte. Réessayez dans un instant. ({erreur})</p>
  {:else}
    <div class="container">
      {#each produitsAffiches as produit (produit.id)}
        <CarteProduit nom={produit.nom} prix={produit.prix} nouveau={produit.nouveau} onAjout={() => ajouter(produit)} />
      {/each}
    </div>
  {/if}

  <section class="panier">
    <h2>Votre panier</h2>
    <p>{panier.length} article(s)</p>

    {#each panier as produit, index}
      <p>
        {produit.nom} : {produit.prix.toFixed(2)} €
        <button onclick={() => retirer(index)}>Retirer</button>
      </p>
    {:else}
      <p>Votre panier est vide</p>
    {/each}

    <select bind:value={mode}>
      <option value="sur place">Sur place</option>
      <option value="emporter">À emporter</option>
    </select>

    <label>
      <input type="checkbox" bind:checked={fidele} />
      J'ai la carte de fidélité
    </label>

    <p>Total : {totalPanier.toFixed(2)} €</p>
    <p>À payer : {prixFinal.toFixed(2)} €</p>
  </section>
</main>

<style>
  .selection {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    padding: 20px;
  }
  .actif {
    background-color: #D6BCFA;
    color: black;
  }
.container {
  display: grid;
  grid-template-columns: 1fr;
  gap: 20px;
}
  .panier {
    margin-top: 40px;
  }

@media (min-width: 600px) {
  .container {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 900px) {
  .container {
    grid-template-columns: repeat(3, 1fr);
  }
}


</style>