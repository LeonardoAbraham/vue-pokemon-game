<template>
    <h1 v-if="!pokemon">Espere por favor...</h1>
    <div v-else>
        <h1>¿Quién es este pokémon?</h1>
        <PokemonPicture 
            :pokemonId="pokemon.id" 
            :showPokemon="showPokemon"
        ></PokemonPicture>

        <PokemonOptions 
            :pokemons="pokemonArr" 
            @selection="checkAnswer" 
        />
        
        <template v-if="showAnswer">
            <h2 class="fade-in">{{message}}</h2>
            <boton-leo @click-boton="newGame" leyenda="Nuevo juego"></boton-leo>
        </template>
        
    </div>
</template>
<script>

import PokemonOptions from '@/components/PokemonOptions'
import PokemonPicture from '@/components/PokemonPicture'
import getPokemonOptions from '@/helpers/getPokemonOptions'
import BotonLeo from '@/components/BotonLeo.vue';

export default {
    components:{
        PokemonPicture, 
        PokemonOptions,
        "boton-leo":BotonLeo,
    },
    data() {
        return {
            pokemonArr: [],
            pokemon: null,
            showPokemon: false,
            showAnswer: false,
            message:''
        }
    },
    methods: {
        async mixPokemonArray(){
            this.pokemonArr = await getPokemonOptions()

            const rndInt = Math.floor( Math.random() * 4 )

            this.pokemon = this.pokemonArr[rndInt]
        },
        checkAnswer(selectedId){
            this.showPokemon = true;
            this.showAnswer = true;
            if(selectedId === this.pokemon.id){
                this.message = `Correcto, ${ this.pokemon.name }`
            }
            else{
                this.message = `Oops, era ${ this.pokemon.name }`
            }
        },
        newGame(){
            this.showPokemon    = false;
            this.showAnswer     = false;
            this.pokemonArr     = [];
            this.pokemon        = null;
            this.message        = '';
            this.mixPokemonArray();
        }
    },
    mounted() {
        this.mixPokemonArray();
    },

}
</script>
<style lang="">
    
</style>