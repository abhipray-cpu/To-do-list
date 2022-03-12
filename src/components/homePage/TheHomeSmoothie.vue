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
    drinks:[{name:"Tripple Berry Smoothie",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/delish-how-to-make-a-smoothie-vertical-1542310073.png?crop=1xw:1xh;center,top&resize=980:*"},
    {name:"Keto Smoothie",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/keto-smoothie-vertical-1540502290.jpg?crop=1xw:1xh;center,top&resize=980:*"},
    {name:"Perfect Green Smoothie",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/delish-healthy-green-smoothie-3-1526492435.jpg?crop=0.376xw:1.00xh;0.262xw,0&resize=980:*"},
    {name:"Choclate Keto Protein Smoothie",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/delish-keto-protein-shake-vertical-088-1543791746.jpg?crop=1xw:1xh;center,top&resize=980:*"},
    {name:"Piña Colada Protein Smoothie",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/17/24/640x959/gallery-1497792694-pinacoladaproteinshake-pin-2.jpg?resize=980:*"},
    {name:"Super Fruit Smoothie",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/16/19/1600x2399/gallery-1462827491-superfruit.jpg?resize=980:*"},
    {name:"Easy banana Smoothie",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/delish-banana-smoothie-3-1526490493.jpg?crop=0.502xw:1.00xh;0.328xw,0&resize=980:*"},
    {name:"Razzle Dazzle Smoothie",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/16/19/1600x2399/gallery-1462829051-razzle-dazzle.jpg?resize=980:*"},
    {name:"Peanut Butter Banana Smoothie",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/delish-peanut-butter-banana-smoothie-1-1526494470.jpg?crop=0.377xw:1.00xh;0.390xw,0&resize=980:*"},
    {name:"Green Dream Smoothie",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/16/19/1600x2399/gallery-1462826798-green-machine.jpg?resize=980:*"},
    {name:"Pineapple Banana Smoothie",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/16/19/1600x2399/gallery-1462827105-pina-colada.jpg?resize=980:*"},
    {name:"Sunshine Daydream Smoothie",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/16/19/1462829771-sunshine-daydream.jpg?crop=1xw:0.9196501220504475xh;center,top&resize=980:*"},
    {name:"Best-Ever Açaí Bowl",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/190514-acai-bowl-162-1559077269.jpg?crop=0.9997369113391213xw:1xh;center,top&resize=980:*"},
    {name:" Cantaloupe Breakfast Bowls",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/delish-cantaloupe-breakfast-bowls-still001-1557182240.jpg?crop=0.377xw:1.00xh;0.273xw,0&resize=980:*"},
    {name:"PB&J smoothie",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/16/19/1600x2399/gallery-1462826618-peanut-butter-jelly-smoothie-1.jpg?resize=980:*"},
    {name:"Hangover Smoothie",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/15/52/1450898916-delish-hangover-smoothie.jpg?crop=0.376xw:1.00xh;0.221xw,0&resize=980:*"},
    {name:"Piña Colada Smoothie Bowls",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/17/04/1485446951-delish-pina-colada-smoothie-bowls-pin-3.jpg?crop=0.999546485260771xw:1xh;center,top&resize=980:*"},
    {name:"The Sage's Smoothie",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/cm/15/10/54f65cb063807_-_juice-generation-sage-smoothie-s1-del0214.jpg?crop=1xw:1xh;center,top&resize=980:*"},
    {name:"Rehydration Smoothie",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/cm/15/10/54f64357bcf27_-_rehydration-smoothie-opr0111-xl.jpg?crop=0.669xw:1.00xh;0.146xw,0&resize=980:*"},
    {name:"Açai Super Smoothie",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/cm/15/10/54f64b99ed594_-_acai-super-smoothie-recipe-fw0311-xl.jpg?crop=0.669xw:1.00xh;0.306xw,0&resize=980:*"},
    {name:"Strawberry,Banana and almond Butter smoothie",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/cm/15/11/54fdf159bfab6-strawberry-banana-almond-butter-smoothie-recipe-fw0311-xl.jpg?crop=0.669xw:1.00xh;0.185xw,0&resize=980:*"},
    {name:"Jump Start Smoothie",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/15/29/1436909798-del-lucky-foods-07-pomegranate-berry-smoothie.jpg?crop=1.0xw:1xh;center,top&resize=980:*"},
    {name:"Pineapple Citrus smoothie",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/freshly-blended-yellow-and-orange-fruit-smoothie-in-royalty-free-image-530209184-1564585945.jpeg?crop=1xw:1xh;center,top&resize=980:*"},
    {name:"Tropical Smoothie Bowl",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/1481210269-smoothie-1625669486.jpeg?crop=1xw:1xh;center,top&resize=980:*"},
    {name:"Rasberry Smoothie Bowl",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/raspberry-smoothie-bowls-wd-0220-1579641472.jpeg?crop=0.669xw:1.00xh;0.154xw,0&resize=980:*"},
    {name:"Strawberry Smoothie Bowl",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/strawberry-smoothie-bowls-wd-0220-1579641095.jpeg?crop=0.6675347222222222xw:1xh;center,top&resize=980:*"},
    {name:"Peach Smoothie Bowls",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/peach-smoothie-bowls-wd-0220-1579640875.jpeg?crop=0.669xw:1.00xh;0.179xw,0&resize=980:*"},
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