<template>
    <section>
        <div class="characters">
            <div class="characters__item" v-for="characters in character" :key="character.id">
                <h2>{{ character.name }}</h2>
            </div>
        </div>
    </section>
</template>
<script>
import { computed, onMounted } from 'vue';
import { useStore } from 'vuex';
export default{
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

</style>