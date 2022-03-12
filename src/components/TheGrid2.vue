<template>
    <div id="container">
    <div class="scroll">
        <the-row :title="Row1Cocktail.title" :Items="Row1Cocktail.items"></the-row>
    </div>
         
  
     <the-row :title="Row2Cocktail.title" :Items="Row2Cocktail.items"></the-row>
     <the-row :title="Row3Cocktail.title" :Items="Row3Cocktail.items"></the-row>
     <the-row :title="Row4Cocktail.title" :Items="Row4Cocktail.items"></the-row>
     <the-row :title="Row5Cocktail.title" :Items="Row5Cocktail.items"></the-row>
     <the-row :title="Row6Cocktail.title" :Items="Row6Cocktail.items"></the-row>
     <the-row :title="Row7Cocktail.title" :Items="Row7Cocktail.items"></the-row>
     <the-row :title="Row8Cocktail.title" :Items="Row8Cocktail.items"></the-row>
     <the-row :title="Row9Cocktail.title" :Items="Row9Cocktail.items"></the-row>
     </div>
</template>
<script>
import TheRow from './TheRow.vue'

export default {
    inject:['Row1Cocktail','Row2Cocktail','Row3Cocktail','Row4Cocktail','Row5Cocktail','Row6Cocktail','Row7Cocktail','Row8Cocktail','Row9Cocktail'],
     components:{TheRow, 
    },
    

   
}
</script>

<style scoped>
#container{
     margin-left:5px;
     display: grid;
     grid-template-rows: 10fr 10fr 10fr 10fr 10fr 10fr 10fr;
     padding:1px;
}
.scroll{
    overflow-x:auto
}
.scroll::-webkit-scrollbar{
display: none;
}


</style>