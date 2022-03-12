<template>
    <div id="container">
        <header>
            <h2>Share your receipes with others</h2>
        </header>
        <div id="home"><button @click="homeRedirect"><img src="/Assets/home-solid.svg" alt=""></button></div>
        <form @submit.prevent="processValues">
            <label for="cuisine">Choose a cuisine:</label>
           <select name="cuisine" id="cuisine" v-model="cuisine">
           <option value="Indian">Indian</option>
           <option value="Chinese">Chinese</option>
           <option value="Korean">Korean</option>
           <option value="Italian">Italian</option>
           <option value="French">French</option>
           <option value="Thai">Thai</option>
           <option value="Fastfood">Fastfood</option>
           <option value="Japanese">Japanese</option>
           <option value="Mexican">Mexican</option>
           </select> <br>
            <input type="text" placeholder="Image" v-model="image">  <br>
            <textarea name="ingrdients"  cols="46" rows="15" v-model="ingredients" placeholder=".Give ingredients for your receipe 
                .Give them in seprate lines i.e new line for each ingredient">
                </textarea><br>
            <textarea name="ingrdients"  cols="46" rows="15" v-model="instructions" placeholder=".Give instructions for your receipe 
                .Give them in seprate lines i.e new line for each instruction">
                
                </textarea><br>
            <input type="text" placeholder="Title" v-model="title" style="margin-bottom:20px"> <br>
            <!--to build a drop box for these two input fields--> 
             <label for="type">Choose a type:</label>
           <select name="type" id="type" v-model="type">
           <option value="Vegan">Vegan</option>
           <option value="Non Veg">Non Veg</option>
           <option value="Drinks">Drinks</option>
           <option value="Deserts">Deserts</option>
           <option value="Snacks">Snacks</option>
           <option value="Healthy">Healthy</option>
           <option value="Quick Bytes">Quick Bytes</option>
           </select> <br>
            <label for="vegan">Vegan:</label>
           <select name="vegan" id="vegan" v-model="vegan">
           <option value="True">True</option>
           <option value="False">False</option>
           </select> <br>
            <button type="submit">Add receipe</button>
        </form>
    </div>
</template>

<script>
import axios from 'axios';
export default {
    inject:['homeRedirect'],
    data(){
        return{
            cuisine:'',
            image:'',
            ingredients:'',
            instructions:'',
            title:'',
            type:'',
            vegan:''
        }
    },
    methods:{
        processValues(){
            // console.log(this.cuisine)
            // console.log(this.image)
            // console.log(this.ingredients)
            // console.log(this.instructions)
            // console.log(this.title)
            // console.log(this.type)
            // console.log(this.vegan)
            this.ingredients=this.ingredients.split('\n');
            this.instructions=this.instructions.split('\n');
             axios.post('https://receipe-e7c2c-default-rtdb.asia-southeast1.firebasedatabase.app/receipes.json',{
                  cusine:this.cuisine,
                  image:this.image,
                  ingredients:this.ingredients,
                  instructions:this.instructions,
                  title:this.title,
                  type:this.type,
                  vegan:this.vegan,
             })
             console.log('Receipe added successfully')
             this.cuisine=''
             this.image=''
             this.ingredients=''
             this.instructions=''
             this.title=''
             this.type=''
             this.vegan=''
             this.homeRedirect();

        }
    }
}
</script>

<style scoped>
#container{
    margin-left: 35%;
    border:2px solid black;
    border-radius: 10px;
    width:414px;
    height:800px;
    padding-top:0px;
    overflow-y: auto;
    background-color: white;
}
#container::-webkit-scrollbar{
  display: none;
}
header{
    width: 100%;
    height:50px;
    background-color:navy;
    margin-top:0px;
    border-radius: 10px;
    padding-top:20px ;

}
header h2{
    text-align: center;
    color: white;
    font-weight: bolder;
    margin-top:0px
}
form{
margin-top:10px;
}
form input{
    border:2px solid black;
    border-radius:10px;
    margin-top:20px;
    height:30px;
    
    width:90%;
    margin-left:20px;
    color:black;
    font-weight:bolder;
    font-size:20px;
}
form input::placeholder,
form textarea::placeholder{
    color:navy;
    font-weight:bolder;
    font-size:20px;

}
form input:hover,
form input:focus,
form textarea:hover,
form textarea:focus{
    outline: none !important;
    border-color: navy;
}
form textarea{
    margin-left:7%;
    margin-top:20px;
       border:2px solid black;
    border-radius:10px;
    padding:10px;
   
}
button{
    margin-top: 10px;
    border:2px solid navy;
    font-size: larger;
    text-align: center;
    font-weight: bolder;
    background-color:transparent;
    margin-left: 35%;
    margin-bottom: 10px;
    border-radius:10px
}
button:hover{
    background-color:navy;
    color:white
}
form label{
    margin-left:5%;
    color:navy;
    font-weight: bolder;
    font-size: xx-large;
    margin-top:20px;
    margin-bottom:20px;
    }
form select{
    margin-left:10px;
    margin-top: 20px;
    margin-bottom: 20px;
    font-weight: bolder;
    font-size: larger;
}
#home button img{
    height:30px;
    width:30px
}
#home button{
    background-color:transparent;
    border: none;
    margin-left:10px;
}
</style>