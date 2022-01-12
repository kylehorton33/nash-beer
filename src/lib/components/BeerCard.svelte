<script>
    export let beer;
</script>



<div class="card shadow-2xl bg-neutral text-accent-content">
    <figure>
      <img src="https://picsum.photos/id/1005/400/250">
    </figure> 
    <div class="card-body">
      <h2 class="card-title">{beer.name}</h2> 
      <p class="line-clamp">{beer.description}</p> 
      <div class="block md:card-actions">
        <button class="btn btn-secondary mt-2">More info</button>
      </div>
    </div>
</div>

<style>
    .line-clamp {
        display: -webkit-box;
        -webkit-line-clamp: 3;
        -webkit-box-orient: vertical;  
        overflow: hidden;
    }
    @media (max-width: 500px) {
        .line-clamp {
            display: none;
        }
    }
</style>
