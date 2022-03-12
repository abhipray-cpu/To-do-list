<template>
     <div id="Baap">
    <div id="body">
      <!--this search will also route to receipe component with search ID-->
      <the-search @EmitValue="ProcessValue"></the-search>
      <the-wallpaper></the-wallpaper>
      <div id="minContain">
        <the-menu @switch="ChangeComponent"></the-menu>
        <the-drinks></the-drinks>
      </div>
    </div>
  </div>
</template>

<script>
//fetch data from the api and make it working
import TheSearch from '../TheSearch.vue';
import TheWallpaper from '../TheWallpaper.vue';
import TheMenu from '../TheMenu.vue';
import TheDrinks from '../TheDrinks.vue'

export default {
  components: {
    TheSearch,
    TheWallpaper,
    TheMenu,
    TheDrinks
  },
  inject: ['searchReq', 'changeComponent'],
provide(){
  return {
    drinks:[{
      name:"Iced Tea",image:"https://www.acouplecooks.com/wp-content/uploads/2020/07/Iced-Tea-001.jpg"
    },
    {
      name:"Masala Chai",image:"https://www.acouplecooks.com/wp-content/uploads/2020/09/Masala-Chai-010.jpg"
    },
    {
      name:"Ginger Tea",image:"https://www.acouplecooks.com/wp-content/uploads/2020/08/Ginger-Tea-006.jpg"
    },
    {
      name:"Chai Latte",image:"https://www.acouplecooks.com/wp-content/uploads/2020/09/Chail-Latte-007.jpg"
    },
    {

      name:"Cold Brew Tea",image:"https://www.acouplecooks.com/wp-content/uploads/2020/07/Cold-Brew-Tea-006.jpg"
    },
    {
      name:"Matcha Japanese green tea",image:"https://www.acouplecooks.com/wp-content/uploads/2021/08/How-to-Make-Matcha-013.jpg"
    },
    {
      name:"Classic Sweet Tea",image:"https://www.acouplecooks.com/wp-content/uploads/2020/07/Sweet-Tea-001.jpg"
    },
    {
      name:"Arnold Palmer",image:"https://www.acouplecooks.com/wp-content/uploads/2021/04/Arnold-Palmer-Drink-002.jpg"
    },
    {
      name:"Perfect Tea Latte",image:"https://www.acouplecooks.com/wp-content/uploads/2020/09/Tea-Latte-007.jpg"
    },
    {
      name:"Iced Chai Latte",image:"https://www.acouplecooks.com/wp-content/uploads/2020/10/Iced-Chai-Tea-Latte-010.jpg"
    },
    {
      name:"Vanilla Chai Latte",image:"https://www.acouplecooks.com/wp-content/uploads/2020/09/Vanilla-Chai-Latte-003.jpg"
    },
    {
      name:"Matcha Chai  Latte",image:"https://www.acouplecooks.com/wp-content/uploads/2021/08/Matcha-Latte-001.jpg"
    },
    {
      name:"Iced Matcha Latte",image:"https://www.acouplecooks.com/wp-content/uploads/2021/08/Iced-Matcha-Latte-008.jpg"
    },
    {
      name:"Mint Tea",image:"https://www.acouplecooks.com/wp-content/uploads/2020/06/Mint-Tea-006.jpg"
    },
    {
      name:"Sage Tea",image:"https://www.acouplecooks.com/wp-content/uploads/2020/07/Sage-Tea-006.jpg"
    },
    {
      name:"Thyme Tea",image:"https://www.acouplecooks.com/wp-content/uploads/2020/06/Thyme-Tea-007.jpg"
    },
    {
      name:"Oregano Tea",image:"https://www.acouplecooks.com/wp-content/uploads/2020/07/Oregano-Tea-003.jpg"
    },
    {
      name:"Rosemarry  Tea",image:"https://www.acouplecooks.com/wp-content/uploads/2020/07/Rosemary-Tea-006.jpg"
    },
    {
      name:"Lavender Tea",image:"https://www.acouplecooks.com/wp-content/uploads/2020/09/Lavender-Tea-003.jpg"
    }
    ]
  }
},
  methods: {
    ProcessValue(value) {
      this.searchReq(value);
    },
    ChangeComponent() {
      this.changeComponent();
    },
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


</style>