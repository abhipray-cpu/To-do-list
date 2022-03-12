<template>
 <div id="row">
     <!---in the props pass a link value as well-->
     <h1 @click="redirect"><a href="#">{{ title }}</a></h1>
    <div id="row-content">
        <the-dish v-for="item in Items" 
        :key="item.name" 
        :Item="item.name" 
        :Image="item.image"></the-dish>
    </div>
    
 </div>
</template>

<script>
import TheDish from './TheDish.vue'
export default {
    inject:['rowRedirect'],
    props:['Items','title'],
    components:{TheDish},
    methods:{
        redirect(){
            this.rowRedirect(this.title);
        }
    },
   
   
}
</script>

<style scoped>
#row-content{
    display: inline-grid;
    grid-template-columns: 20fr 20fr 20fr 20fr 20fr 20fr;
  
    margin-top:5px;
    margin-bottom: 50px;
   
}

div h1{
    margin-bottom: 5px;
}
div h1 a{
    text-decoration: none;
    color:black
}

</style>

