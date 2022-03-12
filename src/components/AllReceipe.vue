<template>
   <div id="body">
           <h1>Teri maa ka bhosda</h1>
     </div>
     <div id="receipe">
         <!--this section will contain all the receipes of this cusine-->
     </div>
</template>

<script>
export default {
    mounted(){
        console.log(this.$store.dispatch('getCusineDish'));
    }
}
</script>

<style scoped>
h1{
    color:black;
    text-align: center;
    font-style: italic;
    font-weight: bold;
    font-size: 32px;
}
#body {
  margin-left: 35%;
  border: 2px solid black;
  border-radius: 10px;
  width: 414px;
  height: 800px;
  padding: 2px;
  overflow-y: auto;
  background-color: white;
}
</style>