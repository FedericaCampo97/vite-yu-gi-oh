<script>
export default {
    name: 'YuGiCard',
    props: ['card'],
    data() {
    },
}
</script>

<template>
    <div class="card">

        <img :src="this.card.card_images[0].image_url" alt="">
        <h2>{{ this.card.name }}</h2>
        <p>{{ this.card.archetype }}</p>
    </div>
</template>

<style></style>