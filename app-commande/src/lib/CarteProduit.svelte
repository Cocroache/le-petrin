<script>
let{nom,prix,nouveau=false} = $props()
</script>




<article class="carte">
    <h2>{nom}</h2>
    <p>{prix.toFixed(2)} €</p>
    {#if nouveau === true }
    
    <p><span class="badge">Nouveau</span></p>
    
    
    {/if}
</article>

<style>
    .carte{
  border: solid black 1px;
  border-radius: 5px;
}
article{
  position: relative;
}
.badge{
  position: absolute;
  top: -10px;
  right: -15px;
  border: solid black 1px;
  background-color: #3E2A3D;
  color: #9F7AEA;
}
.carte{
    background-color: #F8E2E2;
}
</style>