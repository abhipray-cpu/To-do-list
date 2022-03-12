<template>
  <div id="Baap">
    
    <div id="body">
      <!--this search will also route to receipe component with search ID-->
<the-search @EmitValue="ProcessValue"></the-search>
<h3>{{ IngredientTitle }}</h3>
<the-wallpaper></the-wallpaper>
 <div id="minContain">
   <the-menu @switch="ChangeComponent"></the-menu>
   <the-grid></the-grid>
  </div>

  </div>
  </div>
</template>



<script>
//fetch data from the api and make it working
import TheSearch from './components/TheSearch.vue'
import TheWallpaper from './components/TheWallpaper.vue'
import TheMenu from './components/TheMenu.vue'
import TheGrid from './components/TheIngredientGrid.vue'

export default {
    components:{
         TheSearch,
         TheWallpaper,
         TheMenu,
         TheGrid
       
    },
    inject:['searchReq','changeComponent','IngredientTitle'],
 
    methods:{
        ProcessValue(value){
            this.searchReq(value);
            
        },
        ChangeComponent(){
               this.changeComponent();
        }
    },
   
    provide(){
        /*
        Indian
Chinese
Korean
Italian
French
Thai
Fastfood
Japanese
Mexican*/
      return {
        
        'Row1':{title:'Indian',items:[{name:'Butter Panner',image:''},{name:'Kadhai Paneer',image:''},{name:'Malai Kofta',image:''}]},
        'Row2':{title:'Chinese',items:[{name:'Butter Chicken',image:''},{name:'Chilli Chicken',image:''},{name:'Seekh Kebab',image:''}]},
        'Row3':{title:'Korean',items:[{name:'Virgin Mohito',image:''},{name:'Blue Lagoon',image:''},{name:'Rasna',image:''}]},
        'Row4':{title:'Italian',items:[{name:'Ras Malai',image:''},{name:'Jalebi Baby',image:''},{name:'Cheena Toast',image:''}]},
        'Row5':{title:'French',items:[{name:'Spring Roll',image:''},{name:'Drums of Heaven',image:''},{name:'Masala Kebab',image:''}]},
        'Row6':{title:'Thai',items:[{name:'Green Salad',image:''},{name:'ChickPea Salad',image:''},{name:'Spinach Smoothie',image:''}]},
        'Row7':{title:'FastFood',items:[{name:'Roasted Almonds',image:''},{name:'Peanut Enrgy Bar',image:''},{name:'Upma',image:''}]},
        'Row8':{title:'Japanese',items:[{name:'Roasted Almonds',image:''},{name:'Peanut Enrgy Bar',image:''},{name:'Upma',image:''}]},
        'Row9':{title:'Mexican',items:[{name:'Roasted Almonds',image:''},{name:'Peanut Enrgy Bar',image:''},{name:'Upma',image:''}]}
      }
    }
}
</script>


<style scoped>
#Baap{
  background-color:rgb(2, 2, 63)
}
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
  display: none;
}

#minContain{
  display: grid;
  grid-template-columns: 20fr 80fr;
  overflow-x:auto; ;
}
#minContain::-webkit-scrollbar{
  display:none
}

</style>