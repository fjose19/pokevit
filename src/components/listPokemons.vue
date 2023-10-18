
<script setup>
   const pokemon = defineProps(["name","baseUrlsvg"])
</script>
<template>
     <div class="col-4">
        <div class="card p-2 mb-3 cardListPokemon">
            <p class="text-center">{{pokemon.name}}</p>
            <img 
               :src="baseUrlsvg" 
               class="card-img-top" 
               alt="..."
               height="80"
            >
        </div>
     </div>
</template>


<style scope>

/* https://cssgradient.io/ */

    .cardListPokemon{
        background: rgb(72,63,251);
        background: radial-gradient(circle, rgba(72, 63, 244, 0.5) 0%, rgba(70,252,244,0.3)100%);
        cursor: pointer;
        
    }

    .cardListPokemon img:hover{
        padding: 0.2rem;
    }
</style>