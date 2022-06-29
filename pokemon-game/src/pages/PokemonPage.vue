<template>
  <h1>¿Quien es este Pokemon?</h1>


<h3>Turnos : {{turnos}}</h3>
  <h3>Acertados : {{counter}}</h3>
  
  <h3>Intentos Fallidos : {{failed}}</h3>

  <div v-if="pokemon">
    <PokemonPicture :pokemonId="pokemon.id" :showPokemon="pokemonShow" />

    <PokemonOptions :pokemons="pokemonArr" @selection="checkAnswer" />
  </div>
  <div v-else>loading ...</div>

  <div v-if="showAnswer">
    {{ message }}
    <br />
    <button class="button" @click="newGame()">New game</button>
  </div>
</template>

<script>
import PokemonOptions from "../components/PokemonOptions.vue";
import PokemonPicture from "../components/PokemonPicture.vue";
import getPokemonOptions from "@/helpers/getPokemonOptions";

console.log(getPokemonOptions());
export default {
  components: {
    PokemonOptions,
    PokemonPicture,
  },
  data() {
    return {
      pokemonArr: [],
      pokemon: null,
      pokemonShow: false,
      message: "",
      showAnswer: false,
      counter: 0,
      failed: 0,
      turnos: 5,
    };
  },
   
  mounted() {
    this.mixPokemonArray();
    this.newGame();
    this.againGame();
  },

  watch:{
    failed(value,oldValue){
      if(value == 5){
        this.showAnswer = true;
        this.message = "Perdiste";
      }
    },
    counter(value,oldValue){
      if(value == 5){
        this.showAnswer = true;
        this.message = "Ganaste";
      }
    }

  },
   
 
  
  methods: {
    async mixPokemonArray() {
      this.pokemonArr = await getPokemonOptions();

      const rndInt = Math.floor(Math.random() * 4);
      console.log(rndInt);

      this.pokemon = this.pokemonArr[rndInt];
      // console.log( this.pokemonArr)
    },

    newGame() {
      this.pokemonShow = false;
      this.showAnswer = false;
      this.pokemonArr =  [];
      this.mixPokemonArray();
      
    },

     

    



    checkAnswer(pokemonId) {
      this.turnos--;
        this.pokemonShow = true;
        this.showAnswer = true;
      if (pokemonId === this.pokemon.id) {
        this.message = `Correcto tu pokemon es  ${this.pokemon.name}`;
        this.counter++;
        this.pokemonArr =  [];
      } else {
        this.message = `!Ops..! tu pokemon era ${this.pokemon.name}`;
         this.failed++;
         
      }
    },
  },
};
</script>

<style>
.message {
  color: red;
  font-size: 1.5em;
  text-align: center;
}
.button {
  background-color: #1f2937;
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  border-radius: 50px;
}
</style>