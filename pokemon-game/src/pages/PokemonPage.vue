<template>
  <h1>¿Quien es este Pokemon?</h1>

   
    <PokemonPicture :pokemonId="35" :showPokemon="true"/>

    <PokemonOptions :pokemons="pokemonArr"/>
{{pokemonArr}}
 
</template>

<script>
import PokemonOptions from '../components/PokemonOptions.vue'
import PokemonPicture from '../components/PokemonPicture.vue'
import getPokemonOptions from  '@/helpers/getPokemonOptions'

 
export default {
    components:{
        PokemonOptions,
        PokemonPicture
    },
    data() {
        return {
            pokemonArr:[],
        }
    },
    mounted() {
       
         this.mixPokemonArray()
         
    },
     methods: {
       mixPokemonArray(){
      this.pokemonArr =  getPokemonOptions()
      
    },
    
  }

}
</script>

<style>

</style>