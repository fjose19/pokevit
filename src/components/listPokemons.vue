
<script setup>
   const pokemon = defineProps(["name","baseUrlsvg"])
</script>
<template>
     <div class="col-sm-6 col-md-4">
        <div class="card p-2 mb-3 cardListPokemon">
            <p class="text-center">{{pokemon.name}}</p>
            <img 
               :src="baseUrlsvg" 
               alt="..."
              
               
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
        height: 25vh;
       
        
    }

    .cardListPokemon img:hover{
        padding: 0.2rem;
    }

   
    .cardListPokemon img{
        height: 15vh;
    }

   
    @media (min-width: 360px) {
      
        .cardListPokemon img{
           height: 15vh;
        }

        .cardListPokemon p{
            font-size: medium;
        }
    }


    
    @media (min-width: 740px) {
      
        .cardListPokemon img{
        height: 10vh;
         }

         .cardListPokemon p{
            font-size: small;
        }

       
    }


   

   

</style>