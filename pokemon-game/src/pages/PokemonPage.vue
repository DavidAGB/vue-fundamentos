<template>
  <h1>¿Quien es este Pokemon?</h1>
   <div v-if="pokemon">
    <PokemonPicture :pokemonId="pokemon.id" :showPokemon="pokemonShow"/>

    <PokemonOptions :pokemons="pokemonArr"/>
   </div>
   <div v-else>
      loading ...
   </div>
   
    
 
 
</template>

<script>
import PokemonOptions from '../components/PokemonOptions.vue'
import PokemonPicture from '../components/PokemonPicture.vue'
import getPokemonOptions from  '@/helpers/getPokemonOptions'

 console.log(getPokemonOptions())
export default {
    components:{
        PokemonOptions,
        PokemonPicture
    },
    data() {
        return {
            pokemonArr:[],
            pokemon:null,
            pokemonShow: false
        }
    },mounted() {
       
         this.mixPokemonArray()
         //console.log('r')
    },
     methods: {
    async   mixPokemonArray(){
      this.pokemonArr = await getPokemonOptions()

      const rndInt = Math.floor(Math.random() * 4) 
      console.log( rndInt)

       this.pokemon =  this.pokemonArr[rndInt]
     // console.log( this.pokemonArr)
    },
    
  }

}
</script>

<style>

</style>