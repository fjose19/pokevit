<script setup>

    import {onMounted, reactive, ref, computed} from "vue";
    import listPokemons from "../components/listPokemons.vue"
    import cardPokemonSelected from "../components/cardPokemonSelected.vue"

    let baseUrlsvg = ref('https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/')
    let pokemons = reactive(ref());
    let searchPokemon = ref("");
    let selectedPokemon = reactive(ref());
    let loading = ref(true);

    onMounted( ()=>{
       fetch("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0")
       .then(res=>res.json())
       .then(res=> {
             pokemons.value = res.results
       });
    });

    const pokemonFiltered = computed(()=>{
        if(pokemons.value && searchPokemon.value){
          return pokemons.value.filter(pokemon=>
            pokemon.name.toLowerCase().includes(searchPokemon.value.toLowerCase())
          )
        }

        return pokemons.value
    });

    const selectPokemon = async (pokemon)=>{
         loading.value = true;
         await fetch(pokemon.url)
         .then(res=> res.json())
         .then(res=> selectedPokemon.value = res)
         .catch(err => alert(err))
         .finally(()=>{
            loading.value = false
         })

         
    }

</script>

<template>
  <main>
    <div class="container">

      <div class="container text-center">
        <div class="row mt-5">
          <div class="col-sm-12 col-md-6">
            
            <cardPokemonSelected 
            
               :name ="selectedPokemon?.name"
               :xp ="selectedPokemon?.base_experience"
               :height="selectedPokemon?.height"
               :img="selectedPokemon?.sprites.other.dream_world.front_default"
               :loading="loading"
            
            />
          </div>
          <div class="col-sm-12 col-md-6">
            <div class="card">

           
               <div class="card-body row card-List">

                  <div class="input-group mb-3">
                    <span class="input-group-text" id="inputGroup-sizing-default">Pesquisar</span>
                    <input type="text" class="form-control" id="searchPokemon" v-model="searchPokemon" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default">
                  </div>
              
                
                  <listPokemons 
                    
                    v-for="pokemon in pokemonFiltered"
                    :key="pokemon.name"
                    :name="pokemon.name"
                    :baseUrlsvg="baseUrlsvg + pokemon.url.split('/')[6]+ '.svg'"
                    @click="selectPokemon(pokemon)"
                  />


               </div>

              
            </div>
          </div>
          
        </div>
      </div>


    </div>
  </main>
</template>

<style scoped>

     
      .card-List {
         overflow-y: scroll;
         overflow-x: hidden;
         max-height: 75vh;
      }
</style>
