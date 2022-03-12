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
    return{
      drinks:[{name:"The Perfect Cup",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/brewing-third-wave-coffee-with-chemex-glass-in-the-royalty-free-image-1608298373.?crop=0.872xw:0.873xh;0.128xw,0.127xh&resize=980:*"},
      {name:"French press",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/cropped-hands-of-woman-pouring-coffee-in-cup-on-royalty-free-image-1608299261.?crop=0.449xw:1.00xh;0.330xw,0&resize=980:*"},
      {name:"Iced Coffee",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/glass-of-ice-coffee-on-the-white-table-in-coffee-royalty-free-image-1608299960.?crop=0.425xw:0.957xh;0.418xw,0.0434xh&resize=980:*"},
      {name:"Cold Brew",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/pouring-cold-brew-coffee-at-home-royalty-free-image-1608300789.?crop=0.451xw:1.00xh;0.163xw,0&resize=980:*"},
      {name:"Cappuccino",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/yellow-coffee-cup-with-cappiccino-royalty-free-image-1608638643.?crop=0.88889xw:1xh;center,top&resize=980:*"},
      {name:"Latte",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/close-up-of-barista-holding-coffee-cup-royalty-free-image-1608299464.?crop=0.537xw:1.00xh;0.141xw,0&resize=980:*"},
      {name:"Flat White",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/homemade-flat-white-latte-royalty-free-image-1608640408.?crop=1xw:0.99953xh;center,top&resize=980:*"},
      {name:"Café au Lait",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/milk-coffee-cup-with-saucer-and-a-croissants-on-royalty-free-image-1608639306.?crop=1xw:1xh;center,top&resize=980:*"},
      {name:"Cortado",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/cup-of-latte-or-cortado-coffee-royalty-free-image-1608639937.?crop=1xw:0.99953xh;center,top&resize=980:*"},
      {name:"Maccahito",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/close-up-of-macchiato-royalty-free-image-1608640085.?crop=0.844xw:0.844xh;0.0663xw,0.117xh&resize=980:*"},
      {name:"Americano",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/americano-royalty-free-image-1608641222.?crop=0.883xw:1.00xh;0,0&resize=980:*"},
      {name:"Irish Coffee",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/irish-coffee-in-a-bar-concept-of-st-patrick-holiday-royalty-free-image-1608301253.?crop=0.447xw:1.00xh;0.0765xw,0&resize=980:*"},
      {name:"Dalgona Coffee",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/dalgona-coffee-a-trendy-fluffy-creamy-whipped-royalty-free-image-1608301380.?crop=1xw:1xh;center,top&resize=980:*"},
      {name:"Affogato",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/coffee-latte-royalty-free-image-1608301506.?crop=1xw:0.99625xh;center,top&resize=980:*"},
      {name:" Mexican Coffee (Café de Olla)",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/mexican-coffee-in-ceramic-cup-royalty-free-image-1608641379.?crop=1xw:0.99651xh;center,top&resize=980:*"},
      {name:"Espresso Martini",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/espresso-martini-cocktail-on-coffee-table-in-indoor-royalty-free-image-1608641764.?crop=0.784xw:0.764xh;0.104xw,0.236xh&resize=980:*"},
      {name:"Turkish Coffee",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/traditional-turkish-coffee-royalty-free-image-1609770906.?crop=0.99882xw:1xh;center,top&resize=980:*"},
      {name:"Vietnamese Iced Coffee (Cà Phê Đá)",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/iced-coffee-royalty-free-image-1609771033.?crop=0.99976xw:1xh;center,top&resize=980:*"},
      {name:"Dirty Chai",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/winter-warm-spice-coffee-drink-royalty-free-image-1609771559.?crop=1xw:0.99953xh;center,top&resize=980:*"},
      {name:"Frappucino",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/coffee-caramel-milkshake-royalty-free-image-1609771812.?crop=0.93375xw:1xh;center,top&resize=980:*"},]
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