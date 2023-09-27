<script>
import axios from 'axios';
import yugiCard from './YuGiCard.vue';

export default {
    name: 'AppMain',
    components: {
        yugiCard
    },
    data() {
        return {
            base_url: 'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0',
            arrayCards: null,
            archetype_url: 'https://db.ygoprodeck.com/api/v7/archetypes.php',
            arrayArchetype: null
        }
    },
    created() {
        axios
            .get(this.base_url)
            .then(resp => {
                this.arrayCards = resp.data.data;
                console.log(this.arrayCards);
            })
            .catch(error => {
                console.error(error)
            })
        axios
            .get(this.archetype_url)
            .then(response => {
                this.arrayArchetype = response.data;
                console.log(this.arrayArchetype)
            })
    },
}
</script>

<template>
    <div class="block p-5">
        <div class="container ">
            <select name="" id="">
                <option value="alien" v-for="element in arrayArchetype">
                    {{ element.archetype_name }}
                </option>
            </select>
            <div class="row bg-white p-4">

                <div class="col">
                    <p class="bg-black text-white px-3 py-2 m-0 mx-3">Found {{ arrayCards.length }} card</p>
                    <div class="card_container d-flex flex-wrap">
                        <yugiCard v-for="card in arrayCards" :card="card" />
                    </div>

                </div>
            </div>
        </div>

    </div>
</template>

<style></style>