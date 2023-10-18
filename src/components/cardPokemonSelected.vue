<script setup>

   const pokemon = defineProps(["name", "xp", "height", "img", "loading"])

</script>

<template>
            <div class="card cardListPokemon" :class="loading ? '': 'animate__animated animate__flipInY'"> <!--animação animate.style-->
              <img v-if="pokemon.name" :src="pokemon.img" class="card-img-top" :alt="pokemon.name">
              <img v-else src="../assets/egg_pokemon.svg" class="card-img-top" alt="????">
              <div class="card-body">
                <h5 class="card-title text-center">{{ pokemon.name || '????' }}</h5>
                <hr>
                <div class="row texto">
                    <section class="col">
                        <strong>XP:</strong>
                        <span>{{ pokemon.xp }}</span>

                    </section>
                    <section class="col">
                        <strong>Altura:</strong>
                        <span>{{ pokemon.height }}</span>

                    </section>
                </div>
              </div>
            </div>

</template>


<style scoped>

    .cardListPokemon{
        background: rgb(72,63,251);
        background: radial-gradient(circle, rgba(244, 160, 63, 0.8) 0%, rgba(238, 28, 28, 0.8)100%);
        height: 75vh;
        overflow: none;
    }

    img{
      height: 50vh;
      padding: 5%;
    }

    @media (min-width: 360px) {
        .cardListPokemon {
         overflow-y: scroll;
         overflow-x: hidden;
         height: 45vh;
         }
         img{
            height: 30vh;
            padding: 5%;
          }
      }
    @media (min-width: 740px) {
        .cardListPokemon {
         overflow-y: scroll;
         overflow-x: hidden;
         height: 60vh;
         margin-top: -5%;
         }

         img{
            height: 45vh;
            padding: 5%;
          }
         .texto{
            margin-top: -4%;
         }

         .card-title{
           margin-top: -10%;
         } 
       
      }

</style>