<template>
    <h1>This will contain the heading</h1>
    <!--a layout should also be added -->
    <the-dish></the-dish>
    <!--Here implement the infinite scrolling-->
</template>

<script>
//two things needs to be decided the number of dishes that should be loaded for a single page
//the loading effect while the data of nexr page is fetched
//dish component is adjusted to the screen ratios
import TheDish from './TheDish.vue'
export default {
    components:{TheDish}
    }
</script>

<style scoped>

</style>