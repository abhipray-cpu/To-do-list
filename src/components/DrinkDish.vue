<template>
    <div id="dish" @click="redirect">
         <div id="image">
             <img :src="image" :alt="name">
         </div>
         <div id="Name">
             <h1>{{ name }}</h1>
         </div>
    </div>
</template>

<script>
export default {
    props:["name","image"],
    inject:['directRedirect'],
    methods:{
        redirect(){
            this.directRedirect(this.name);
        }
    }
}
</script>

<style scoped>
#dish{ 
    margin-left:70px;
    width:300px;
    height:370px;
    display:grid;
    grid-template-rows:300px 60px;
    margin-top:10px;
    margin-bottom:10px
}
#image img{
    width:300px;
    height:300px;
    max-width: 300px;
    max-height: 300px;
    border-radius:10px;
}
#Name h1{
    margin-top:2px;
    text-align:center;
    font-weight:1000;
    font-style: italic;
    font-size:34px
}

</style>