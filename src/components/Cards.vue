<template>
   <div class="cards flex" v-if='cards.length'>
       <card v-for='card in cards' :card='card' :key='card.id'  />
    </div>
</template>

<script>
import Card from '../components/Card.vue'
export default {
    components: {Card},
    props: {
        cards: {
            type: Array,
            required: true
        }
    }
}
</script>

<style>
.cards{
        margin-top: 32px;
        gap: 30px;
        flex-wrap: wrap;
    }
    @media(max-width: 797px){
        .cards{
               justify-content: center;
        }
     
    }

</style>