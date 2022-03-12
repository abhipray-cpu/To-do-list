<template>
    <div id="container">
    <div class="scroll">
        <the-row :title="Row1.title" :Items="Row1.items"></the-row>
    </div>
         
  
     <the-row :title="Row2.title" :Items="Row2.items"></the-row>
     <the-row :title="Row3.title" :Items="Row3.items"></the-row>
     <the-row :title="Row4.title" :Items="Row4.items"></the-row>
     <the-row :title="Row5.title" :Items="Row5.items"></the-row>
     <the-row :title="Row6.title" :Items="Row6.items"></the-row>
     <the-row :title="Row7.title" :Items="Row7.items"></the-row>
     <the-row :title="Row8.title" :Items="Row8.items"></the-row>
     <the-row :title="Row9.title" :Items="Row9.items"></the-row>
     </div>
</template>
<script>
import TheRow from './TheRow.vue'

export default {
    inject:['Row1','Row2','Row3','Row4','Row5','Row6','Row7','Row8','Row9'],
     components:{TheRow, 
    },
    

   
}
</script>

<style scoped>
#container{
     margin-left:5px;
     display: grid;
     grid-template-rows: 10fr 10fr 10fr 10fr 10fr 10fr 10fr 10fr 10fr;
     padding:1px;
}
.scroll{
    overflow-x:auto
}
.scroll::-webkit-scrollbar{
display: none;
}


</style>