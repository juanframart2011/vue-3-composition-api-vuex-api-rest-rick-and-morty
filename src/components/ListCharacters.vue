<template>
    <section>
        <div class="characters">
            <div class="characters__item" v-for="characters in character" :key="character.id">
                <CardCharacters :character="character" />
            </div>
        </div>
    </section>
</template>
<script>
import { computed, onMounted } from 'vue';
import { useStore } from 'vuex';

import CardCharacters from './CardCharacters.vue';
export default{
    components:{
        CardCharacters
    },
    setup(){
        const store = useStore();
        const characters = computed(()=>{
            debugger;
            return store.state.charactersFilter;
        });
        onMounted(()=>{
            store.dispatch('getCharacters')
        })
        return {
            characters
        }
    }
}
</script>
<style scoped>
.characters{
    display: grid;
    grid-template-columns: repeat (3,1fr);
    gap: 3rem;
    margin: 3rem 0;
}
</style>