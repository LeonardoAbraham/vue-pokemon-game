<template>
    <h1>¿Quién es este pokémon?</h1>
    <!-- Componente Imagen pokémon-->
    <PokemonPicture :pokemonId="25" :showPokemon="true"></PokemonPicture>
    <PokemonOptions/>

    <!-- Componente Opciones -->
</template>
<script>

import PokemonOptions from '@/components/PokemonOptions'
import PokemonPicture from '@/components/PokemonPicture'
export default {
    components:{
        PokemonPicture, 
        PokemonOptions
    },

}
</script>
<style lang="">
    
</style>