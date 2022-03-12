<template>
  <div id="Baap">
    <div id="body">
      <!--this search will also route to receipe component with search ID-->
      <the-search @EmitValue="ProcessValue"></the-search>
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
import TheSearch from '../TheSearch.vue';
import TheWallpaper from '../TheWallpaper.vue';
import TheMenu from '../TheMenu.vue';
import TheGrid from '../TheGrid2.vue';

export default {
  components: {
    TheSearch,
    TheWallpaper,
    TheMenu,
    TheGrid,
  },
  inject: ['searchReq', 'changeComponent'],

  methods: {
    ProcessValue(value) {
      this.searchReq(value);
    },
    ChangeComponent() {
      this.changeComponent();
    },
  },
  data(){
    return{
      IndianDish:[{
        name:"Anchovy65",image:"https://cdn.tasteatlas.com//images/dishes/08c64cbaaadb4c5080daec9b67666629.jpg?w=905&h=510"
      },
      {
        name:"Prawn Koliwada",image:"https://cdn.tasteatlas.com//images/dishes/ea220c33cfea4ce2914ee8d5a19324c4.jpg?w=905&h=510"
      },
      {
        name:"Bombil Fry",image:"https://cdn.tasteatlas.com//images/dishes/dd7555964d3a4fa5a19fb3feaa5cd788.jpg?w=905&h=510"
      }],
      ChineseDish:[{
        name:"Fried Shrimps with Longjing Tea",image:"https://cdn.tasteatlas.com//images/dishes/de06e32edc5345588f3508c3b28d5abb.jpg?w=905&h=510"
      },
      {
        name:"Drunken Prawn",image:"https://cdn.tasteatlas.com//Images/Dishes/63575675130244cb9648305c0ce97382.jpg?w=905&h=510"
      },
      {
        name:"Stir-fry shrimp",image:"https://cdn.tasteatlas.com//Images/Dishes/d89e3029be1e430fb1a78377e6cf8add.jpg?w=905&h=510"
      }],
      KoreanDish:[{
        name:"SQUID DISH Ojingeo chae bokkeum",image:"https://cdn.tasteatlas.com//images/dishes/5c251a0df49e423b8f9c4b4a7c6359e5.jpg?w=905&h=510"
      },
      {
        name:"Guljeon",image:"https://cdn.tasteatlas.com//images/dishes/3dafea56e95949ce8f575f42e215217c.jpg?w=905&h=510"
      },
      {
        name:"Nakji Bokeum",image:"https://cdn.tasteatlas.com//images/dishes/ecec07c17e544581bd532f9d09238430.jpg?w=905&h=510"
      }],
      ItalianDish:[{
        name:"Calamari Ripeni",image:"https://cdn.tasteatlas.com//Images/Dishes/70e9068b53c1441f9108ca854d40fedd.jpg?w=905&h=510"
      },
      {
        name:"Involtini di pesce spada",image:"https://cdn.tasteatlas.com//images/dishes/83f1efb0a2354e568ede5b6f2fe74c3d.jpg?w=905&h=510"
      },
      {
        name:"Cacciucco",image:"https://cdn.tasteatlas.com//Images/Dishes/7f7decd02f724c3bb2a1d7c549679e2d.jpg?w=905&h=510"
      }],
      FrenchDish:[{
        name:"Sole à la Normande",image:"https://cdn.tasteatlas.com//images/dishes/72baa6d8babd48d0add40c2ac5a4ce53.jpg?w=905&h=510"
      },
      {
        name:"Saumon à l'oseille",image:"https://cdn.tasteatlas.com//images/dishes/4229526e57bb4171814c4e4c25ad4639.jpg?w=905&h=510"
      },
      {
        name:"Meunière",image:"https://cdn.tasteatlas.com//images/dishes/6076bbbae7214fef879c8b9a8cf8dd13.jpg?w=905&h=510"
      }],
      thaiDish:[{
        name:"Poo cha",image:"https://cdn.tasteatlas.com//images/dishes/a97a9cc66d304a789785693db856d508.jpg?w=905&h=510"
      },
      {
        name:"Pla muek yang  THAILAND ",image:"https://cdn.tasteatlas.com//images/dishes/1e85458a97e34c719c6049c03bdf0613.jpg?w=905&h=510"
      },
      {
        name:"Thai Shrimp and Glass Noodles(Goong ob woon sen)",image:"https://cdn.tasteatlas.com//images/dishes/e13ebd4a08bf4e828546e8654a5e5e16.jpg?w=905&h=510"
      }],
      fastfoodDish:[{
        name:"Fish and chips",image:"https://static.toiimg.com/thumb/59736398.cms?width=1200&height=900"
      },
      {
        name:"Fish Cutlets",image:"https://i.ndtvimg.com/i/2016-07/fish-cutlets_625x350_71469696011.jpg"
      },
      {
        name:"Chettinad Fish Fry",image:"https://i.ndtvimg.com/i/2016-07/chettinad-fish_625x350_71469695663.jpg"
      }],
      japaneseDish:[{
        name:"Fugu Chiri",image:"https://cdn.tasteatlas.com//Images/Dishes/5198bbf38a18446fb74a8e9a70de7f57.jpg?w=905&h=510"
      },
      {
        name:"Maguro nigiri sushi",image:"https://cdn.tasteatlas.com//images/dishes/7ff89cab5d8a436c8612e86980fea3ff.jpg?w=905&h=510Maguro nigiri sushi"
      },
      {
        name:"Sake Nigiri Sushi",image:"https://cdn.tasteatlas.com//images/dishes/ef30d84ca9f04834917378c56630c6da.jpg?w=905&h=510"
      }],
      MexicanDish:[{
        name:"Huachinango a la Veracruzana",image:"https://cdn.tasteatlas.com//images/dishes/b95643d2416443b88d61ed5277902de9.jpg?w=905&h=510"
      },
      {
        name:"Camarones el mojo de ajo",image:"https://cdn.tasteatlas.com//images/dishes/66697e2a4d854e05a6a39a8b2ff015a9.jpg?w=905&h=510"
      },
      {
        name:"Enchiladas de camaron",image:"https://cdn.tasteatlas.com//images/dishes/f00bf4c627944346acb1c7884e577ff5.jpg?w=905&h=510"
      }],
    }
  },

  provide() {
    return {
     
 Row1Cocktail: {
        title: 'Indian',
        items: this.IndianDish
      }, Row2Cocktail: {
        title: 'Chinese',
        items: this.ChineseDish
      }, Row3Cocktail: {
        title: 'Korean',
        items:this.KoreanDish
      },
      Row4Cocktail: {
        title: 'Italian',
        items: this.ItalianDish
      },
       Row5Cocktail: {
        title: 'French',
        items:this.FrenchDish
      },
       Row6Cocktail: {
        title: 'Thai',
        items: this.thaiDish
      },
       Row7Cocktail: {
        title: 'FastFood',
        items:this.fastfoodDish
      },
       Row8Cocktail: {
        title: 'Japanese',
        items: this.japaneseDish
      },
       Row9Cocktail: {
        title: 'Mexican',
        items:this.MexicanDish
      }
    };
  },
};
</script>


<style scoped>
#Baap {
  background-color: rgb(2, 2, 63);
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
#body::-webkit-scrollbar {
  display: none;
}

#minContain {
  display: grid;
  grid-template-columns: 20fr 80fr;
  overflow-x: auto;
}
#minContain::-webkit-scrollbar {
  display: none;
}
</style>