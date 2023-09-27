<script>
export default {
    name: 'YuGiCard',
    props: ['card'],
    data() {
    },
}
</script>

<template>
    <div class="card p-3">
        <div>
            <img :src="this.card.card_images[0].image_url" alt="">
            <h4>{{ this.card.name }}</h4>
            <p>{{ this.card.archetype }}</p>
        </div>
    </div>
</template>

<style></style>