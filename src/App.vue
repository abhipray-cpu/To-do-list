<template>
  <div id="Baap">
   <keep-alive>
  <component :is="component"></component>
   </keep-alive>
  </div>
</template>



<script>
//fetch data from the api and make it working
// import TheHome from './TheHome.vue'
import TheReceipe from './TheReceipe.vue'
import TheHome from './TheHome.vue'
import TheIngredient from './TheIngredient.vue'
import TheForm from './components/TheForm.vue'
import TheReceipes from './TheReceipes.vue'
import TheHomeIndian from './components/homePage/TheHomeIndian.vue'
import TheHomeChinese from './components/homePage/TheHomeChinese.vue'
import TheHomeKorean from './components/homePage/TheHomeKorean.vue'
import TheHomeItalian from './components/homePage/TheHomeItalian.vue'
import TheHomeFrench from './components/homePage/TheHomeFrench.vue'
import TheHomeThai from './components/homePage/TheHomeThai.vue'
import TheHomeFastfood from './components/homePage/TheHomeFastfood.vue'
import TheHomeJapanese from './components/homePage/TheHomeJapanese.vue'
import TheHomeMexican from './components/homePage/TheHomeMexican.vue'
import TheHomeCocktail from './components/homePage/TheHomeCocktails.vue'
import TheHomeCoffee from './components/homePage/TheHomeCoffee.vue'
import TheHomeTea from './components/homePage/TheHomeTea.vue'
import TheHomeShake from './components/homePage/TheHomeShake.vue'
import TheHomeSmoothie from './components/homePage/TheHomeSmoothie.vue'
import TheHomeSeaFood from './components/homePage/TheHomeSeaFood.vue'
import AllReceipes from './components/AllReceipe.vue'
import axios from 'axios'
export default {
  
    components:{
      // TheHome
       TheReceipe,
       TheHome,
       TheForm,
       TheIngredient,
       TheReceipes,
       TheHomeIndian,
       TheHomeChinese,
       TheHomeKorean,
       TheHomeItalian,
       TheHomeFrench,
       TheHomeThai,
       TheHomeFastfood,
        TheHomeJapanese,
        TheHomeMexican,
        TheHomeCocktail,
        TheHomeCoffee,
        TheHomeTea,
        TheHomeShake,
        TheHomeSmoothie,
        TheHomeSeaFood,
        AllReceipes
    },
    provide(){
      return{
        images:this.image,
        title:this.title,
        instructions:this.instruction,
        ingredients:this.ingredients,
        searchReq:this.searchFunction,
        homeRedirect:this.landingRedirect,
        changeComponent:this.changeComponent,
        redirect:this.menuRedirect,
        redirectIngredient:this.redirectIngredient,
        IngredientTitle:this.IngredientTitle,
        directRedirect:this.directRedirect,
        rowRedirect:this.rowRedirect
      }
    },
    data(){
      return{
        component:'TheHome',
        IngredientTitle:'',
        state:'Indian'
        }
    },
    methods:{
      //there are two possible solutions
      //either add routes 
      //or create seprate components for each cusine and then render them based on global cusine state
      landingRedirect(){
             let val = this.$store.getters.getCusine;
             if(val === 'Indian')
            {
              this.component='TheHomeIndian'
            }
            else if(val === 'Chinese')
            { 
              this.component='TheHomeChinese'
            }
            else if(val === 'Korean')
            {
              this.component='TheHomeKorean'
            }
            else if(val === 'Italian')
            {
              this.component='TheHomeItalian'
            }
            else if(val === 'French')
            {
              this.component='TheHomeFrench'
            }
            else if(val === 'Thai')
            {
              this.component='TheHomeThai'
            }
            else if(val === 'FastFood')
            {
              this.component='TheHomeFastfood'
            }
            else if(val === 'Japanese')
            {
              this.component='TheHomeJapanese'
            }
            else if(val === 'Mexican')
            {
              this.component = 'TheHomeMexican'
            }
            else if(val === 'Cocktails')
            {
              this.component='TheHomeCocktail'
            }
            else if(val === 'Coffee')
            {
              this.component='TheHomeCoffee';
            }
            else if(val === 'Tea')
            {
              this.component='TheHomeTea';
            }
            else if(val === 'Shakes')
            {
              this.component='TheHomeShake';
            }
            else if(val === 'Smoothies')
            {
              this.component='TheHomeSmoothie';
            }
            else if(val === 'Seafood')
            {
              this.component='TheHomeSeaFood';
            }

      },
      searchFunction(value){
        console.log(`The item you searched for is ${value}`)
        this.$store.commit({
          type:'updateReceipe',
          payload:value
        })
        this.$store.dispatch('getReceipe');
        
        this.component = 'TheReceipe';
        },
      fetchData(){
       axios.get('https://receipe-e7c2c-default-rtdb.asia-southeast1.firebasedatabase.app/receipes.json')
       .then(response=>{
         return response.data;
       })
       .then(data=>{
         console.log(data);
         //now how to use and display this data?
       })
       .catch(error=>{
         console.log('error ocurred');
         console.log(error);
       })
      },
      changeComponent(){
        this.component = 'TheForm';
      },
      menuRedirect(val){
        //this function will fetch the values based on the cusine and a different component will be loaded basically same home component with more options
            console.log(`You will be redirected to this receipe link ${val}`);
            this.$store.dispatch({
              type:"changeCusine",
              payload:val

            })
            console.log(this.$store.getters.getVegan);
            if(val === 'Indian')
            {
              this.component='TheHomeIndian'
            }
            else if(val === 'Chinese')
            { 
              this.component='TheHomeChinese'
            }
            else if(val === 'Korean')
            {
              this.component='TheHomeKorean'
            }
            else if(val === 'Italian')
            {
              this.component='TheHomeItalian'
            }
            else if(val === 'French')
            {
              this.component='TheHomeFrench'
            }
            else if(val === 'Thai')
            {
              this.component='TheHomeThai'
            }
            else if(val === 'FastFood')
            {
              this.component='TheHomeFastfood'
            }
            else if(val === 'Japanese')
            {
              this.component='TheHomeJapanese'
            }
            else if(val === 'Mexican')
            {
              this.component = 'TheHomeMexican'
            }
            else if(val === 'Cocktails')
            {
              this.component='TheHomeCocktail'
            }
            else if(val === 'Coffee')
            {
              this.component='TheHomeCoffee';
            }
            else if(val === 'Tea')
            {
              this.component='TheHomeTea';
            }
            else if(val === 'Shakes')
            {
              this.component='TheHomeShake';
            }
            else if(val === 'Smoothies')
            {
              this.component='TheHomeSmoothie';
            }
            

      },
      redirectIngredient(val){
        this.$store.dispatch({
              type:"changeCusine",
              payload:val

            })
               if(val === 'Seafood')
            {
              this.component='TheHomeSeaFood';
            }
      },
      lastRedirect(val){
        console.log(`This is the final redirection to ${val}`);
        this.component = "TheReceipes"
      },
      directRedirect(value){
        console.log(`You will be redirected to this receipe ${value}`)
        this.$store.commit({
          type:'updateReceipe',
          payload:value
        })
        this.$store.dispatch('getReceipe');
        this.component='TheReceipe';

      },
      rowRedirect(value){
        
console.log(value)
       // this.component='AllReceipes';
      }
    },
    //it will be better to use action mapping in here
    mounted() {
      this.receipes=this.$store.dispatch('getReceipe');


    }
   
   
}
</script>


<style scoped>
#Baap{
  background-color:rgb(2, 2, 63);
  overflow-y: auto;
}
#Baap::-webkit-scrollbar{
  display: none;
}


</style>