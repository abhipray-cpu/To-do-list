<template>
 
    <div id="body">
        <!-- <div id="spinner" v-if="spin">
     The data is loading.....
 </div> -->
       
            <img :src="getImage" :alt="getTitle">
        <h1>{{ getTitle }}</h1>
        <!---this button will route back to home page-->
       <div id="home"><button @click="homeRedirect"><img src="./Assets/home-solid.svg" alt=""></button></div>
        <div id="Receipe">
            <h2>Receipe:</h2>
            <ul>
                <li v-for="instruction in getReceipe" 
                :key=instruction>
                 instruction
                </li>
            </ul>
        </div>
        <div id="Ingredients">
            <h2>Ingredients:</h2>
            <ul>
                <li v-for="ingredient in getIngredients" 
                :key="ingredient">
                ingredient
                </li>
            </ul>
        </div>
       </div>
    
</template>

<script>
export default {
    //the spinner needs to be globally managed here therfore defining it in the store
    inject:['homeRedirect'],
    computed:{
        getImage()
        {
        return this.$store.getters['getDishImage']
        },
        getTitle()
        {
             return this.$store.getters['getDishTitle']
        },
        getIngredients()
        {
             return this.$store.getters['getDishIngredients']
        },
        getReceipe(){
         return this.$store.getters['getDishReceipe']
        },
        spin(){
            return this.$store.getters['getSpin'];//this is globally managed app
        }
    },
    mounted(){
        console.log('This is the state of the spinner')
        console.log(this.spin);
    }
    
  
}

</script>

<style scoped>
#body{
    margin-left: 35%;
    border:2px solid black;
    border-radius: 10px;
    width:414px;
    height:800px;
    padding:2px;
    overflow-y: auto;
    background-color: white;
}
#body::-webkit-scrollbar{
    display:none;
}
#body img{
     height:350px;
     width:100%;
     border-radius: 10px;
     padding: 0px;
     margin:0px;
}
#body h1{
    text-align: center;
    text-decoration: underline;
    font-weight: bold;
}
#Receipe,
#Ingredients{
    margin-top:4px;
    margin-left:2px;
    padding:2px;
    margin-bottom:5px;
}
#Receipe h2,
#Ingredients h2{
    margin-left: 10px;
    font-weight: bold;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    font-style: italic;
}
#Receipe ul,
#Ingredients ul {
    margin-left: 0px;
}
#Receipe ul li,
#Ingredients ul li{
    margin-top:10px;
    margin-bottom: 10px;
    margin-left: 20px;
    margin-right: 20pxs;
}
#home button img{
    height:30px;
    width:30px
}
#home button{
    background-color:transparent;
    border: none;
}
</style>