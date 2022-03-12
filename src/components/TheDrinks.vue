<template>
    <div id="container">
        <drink-dish v-for="drink in drinks"
    :key="drink.name"
    :name="drink.name"
    :image="drink.image"
    ></drink-dish>
    </div>
</template>


<script>
import DrinkDish from './DrinkDish.vue'
export default {
    components: {
        DrinkDish
    },
   inject:['drinks'],
}
</script>

<style scoped>
#container{
    overflow-x: auto;
}
#container::webkit-scrollbar{
    display: none;
}
</style>