<template>
    <div class="test">
        <form v-on:submit.prevent="ToSearch">
            <input v-model="name" type="text">
            <input type="submit" value="Buscar">
        </form>
    </div>
</template>

<script>
export default {
    name: "SearchPokemon"
    , data() {
        return {
            name: null,
            info: null
        }
    },
    methods: {
        ToSearch() {
            this.bvalue = !this.bvalue;
           
           fetch("https://pokeapi.co/api/v2/pokemon/" + this.name)
           .then(res => {
               if(res.ok)
                   // respuesta ok, ahora queremos el json con los datos.
                   return res.json()
               })
           .then(function (json) {
               this.$emit('pokemonLoad',json);
               //Tratamos la información recibida
           });
        }
    }
}
</script>