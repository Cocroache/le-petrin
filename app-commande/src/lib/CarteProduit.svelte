<script>
let{nom,prix,nouveau=false,onAjout} = $props()
</script>




<article class="carte">
    <h2>{nom}</h2>
    <p>{prix.toFixed(2)} €</p>
    <button onclick={onAjout}>Ajouter</button>
    {#if nouveau === true }
    
    <span class="badge">Nouveau</span>
    
    
    {/if}
</article>

<style>
    .carte{
  border: solid black 1px;
  border-radius: 5px;
  position: relative;
  background-color: #F8E2E2;

}

.badge{
  position: absolute;
  top: -10px;
  right: -15px;
  border: solid black 1px;
  background-color: #D6BCFA;
  color: white;
}

</style>