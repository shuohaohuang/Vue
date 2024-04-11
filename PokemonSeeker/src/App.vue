<template>
    <div>
    <componente @pokemonLoad="CatchPokemon"></componente>
    <section v-if="hasInfo">
        
    </section>
    </div>
</template>


<script>
import componente from '@/components/PokeSeacher.vue';
export default{
    components:{
        componente
    },
    data(){
        return{
            pokemon: null,
            presentValue:null,
        }
    },computed:{
        hasInfo(){
            return !this.pokemon==null;
        }
    },
    methods:{
        CatchPokemon(pokemon){
            this.pokemon=pokemon
        }
    }
}
</script>