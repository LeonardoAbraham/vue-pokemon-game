<template>
    <h1>¿Quién es este pokémon?</h1>
    <PokemonPicture :pokemonId="25" :showPokemon="true"></PokemonPicture>
    <PokemonOptions :pokemons="pokemonArr" />

</template>
<script>

import PokemonOptions from '@/components/PokemonOptions'
import PokemonPicture from '@/components/PokemonPicture'
import getPokemonOptions from '@/helpers/getPokemonOptions'

export default {
    components:{
        PokemonPicture, 
        PokemonOptions
    },
    data() {
        return {
            pokemonArr: [],
        }
    },
    methods: {
        async mixPokemonArray(){
            this.pokemonArr = await getPokemonOptions()
        }
    },
    mounted() {
        this.mixPokemonArray();
    },

}
</script>
<style lang="">
    
</style>