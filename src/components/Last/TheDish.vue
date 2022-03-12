<template>
    <div id="dish" @click="redirect">
        <img :src="Image" alt="Item">
        <h4>{{ Item }}</h4>
    </div>
</template>

<script>
export default {
    props:['Item','Image'],
    inject:['directRedirect'],
    methods:{
        redirect(){
            this.directRedirect(this.Item)
        }
    },
    mounted(){
        console.log(this.Item)
    }
}
</script>

<style scoped>
#dish{
    border:2px solid transparent;
    width:150px;
    height: 100px;
    margin-left:2px;
    margin-right:4px;
    border-radius: 30px;
    cursor:pointer;
}
 img{
    border:2px solid transparent;
    width:100%;
    height: 100%;
    border-radius: 30px;
    cursor:pointer;
}
 h4{
    text-align: center;
    font-weight: bolder;
    font-family: 'Times New Roman', Times, serif;
    color:black;
}

</style>