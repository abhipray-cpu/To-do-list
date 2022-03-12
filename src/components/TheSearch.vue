<template>
    <div>
        <form @submit.prevent = "$emit('EmitValue', SearchValue)">
            <input type="text" v-model="SearchValue" placeholder="Search">
        </form>
    </div>
</template>


<script>
export default {
       data(){
           return {
                SearchValue:''}
       },
       emits: ['EmitValue'] ,
// a better approach is to use a method here and then call the emot from that function
// we can set the searchValue to ' ' after trigerring the function  
}
</script>

<style scoped>
      div form input{
          width: 80%;
      }
      div form input,
      div form input:focus,
      div form input:hover,
      div form :active{
               border: 2px solid black;
               padding: 2px;
               font:28px;
               font-weight: bold;
               font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;

      }
      div form input::placeholder{
          color:black;
          font:28px;
               font-weight: bold;
               font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      }
      div{
          margin-top:10px;
          margin-left:60px;
          margin-right:10px
        
          
      }
</style>