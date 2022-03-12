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
    drinks:[
      {name:"Choclate Milk Shake",image:"https://www.itisakeeper.com/wp-content/uploads/2020/06/CHOCOLATE-MILKSHAKE.jpg"},
      {name:"Vanilla Milk Shake",image:"https://www.itisakeeper.com/wp-content/uploads/2020/06/VANILLA-MILKSHAKE.jpg"},
      {name:"StrawBerryMilkshake",image:"https://www.itisakeeper.com/wp-content/uploads/2020/06/STRAWBERRY-MILKSHAKE.jpg"},
      {name:"Salted Caramel Pretzel Milkshake",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/15/24/1280x1280/square-1433964498-delish-milkshakes-new-salty.jpg?resize=768:*"},
      {name:"Cherry Vanilla Milkshake",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/15/24/1280x1280/square-1433964548-delish-milkshakes-new-cherry.jpg?resize=768:*"},
      {name:"Mint White choclate milkshake",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/15/24/1280x1280/square-1433964595-delish-milkshakes-new-mint.jpg?resize=768:*"},
      {name:"S'mores milkshake",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/15/24/1280x1280/square-1433964636-delish-milkshakes-new-smores.jpg?resize=768:*"},
      {name:"Peanut Butter Brownie Milkshake",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/15/24/1280x1280/square-1433964673-delish-milkshakes-new-peanut.jpg?resize=768:*"},
      {name:"Oreo Cheesecake Milkshake",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/15/24/1280x1280/square-1433964773-delish-milkshakes-new-oreo.jpg?resize=768:*"},
      {name:"Fruity Pebble Milkshake",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/15/24/1280x1280/square-1433964813-delish-milkshakes-new-fruity.jpg?resize=768:*"},
      {name:"Strawberry Shortcake milkshake",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/15/24/1280x1280/square-1433964890-delish-milkshakes-new-strawberry.jpg?resize=768:*"},
      {name:"Banana Cream Pie milkshake",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/15/24/1280x1280/square-1433964851-delish-milkshakes-new-banana.jpg?resize=768:*"},
      {name:"Piña Colada Protein Smoothie",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/17/24/640x959/gallery-1497792694-pinacoladaproteinshake-pin-2.jpg?resize=980:*"},
      {name:"Burbon Milk Punk",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/17/16/640x959/gallery-1492816817-delish-bourbon-milk-punch-pin-2.jpg?resize=980:*"},
      {name:"Firecracker Milkshake",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/15/27/1435607256-july-4th-milkshakes-1.jpeg?crop=1.0xw:1xh;center,top&resize=980:*"},
      {name:"Cap'n Crunch Milkshakes",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/16/26/640x958/gallery-1467401531-capn-crunch-milkshake-pinterest-002.jpg?resize=980:*"},
      {name:"Red,white and boozy milkshake",image:"https://hips.hearstapps.com/del.h-cdn.co/assets/16/26/640x959/gallery-1467051959-delish-red-white-boozy-shakes-4.jpg?resize=980:*"},
      {name:"Choco Chip cookie coffee shake",image:"https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/choc-chip-cookie-coffee-4-1-1522210789.jpg?crop=0.9715686274509804xw:1xh;center,top&resize=980:*"},
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