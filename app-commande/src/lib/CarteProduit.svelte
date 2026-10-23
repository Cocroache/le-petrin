<script>

</script>

{#each produits as produit (produit.id) }
    <article class="carte">
        <h2>{produit.nom}</h2>
        <p>{produit.prix.toFixed(2)} €</p>
        
        
        
    </article>
    {/each}