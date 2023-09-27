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
            arrayCards: null
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
    },
}
</script>

<template>
    <div class="block p-5">
        <div class="container bg-white p-5">
            <div class="row">
                <div class="col">
                    <div class="card_container d-flex flex-wrap">
                        <yugiCard v-for="card in arrayCards" :card="card" />
                    </div>

                </div>
            </div>
        </div>

    </div>
</template>

<style></style>