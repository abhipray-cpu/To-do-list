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
import TheGrid from '../TheGrid.vue';

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
return {
   veganDish: [{ name: "Vegan Tofu Bolognese", image: "https://hurrythefoodup.com/wp-content/uploads/2016/08/Vegan-Tofu-Bolognese-6.jpg" },
                { name: "Vegan Mushroom Risotto", image: "https://hurrythefoodup.com/wp-content/uploads/2019/04/vegan-mushroom-risotto-7-of-8.jpg" },
                { name: "Creamy Pumpkin Pasta", image: "https://hurrythefoodup.com/wp-content/uploads/2021/04/pumpkin-pasta.jpg" }
            ],
            nonVegDish: [{ name: "Lemon Chicken and Pea Gemelli", image: "https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/1460034142-lemon-chicken-and-pea-gemelli-1530823187.jpg?crop=0.784xw:0.785xh;0.183xw,0.00461xh&resize=980:*" },
                { name: "Skillet chicken potato and peppers", image: "https://hips.hearstapps.com/wdy.h-cdn.co/assets/16/26/skillet-chicken-potatoes-peppers-wdy0616.jpg?crop=1.0xw:1xh;center,top&resize=980:*" },
                { name: "Creamy Parmesan Chicken Skillet", image: "https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/italian-chicken-recipes-chicken-parmesan-skillet-1530807951.jpg?crop=1xw:1xh;center,top&resize=980:*" }
            ],
            drinksDish: [
                { name: "LimonCello", image: "https://cdn.tasteatlas.com//images/ingredients/faed7c35fee94815be73ff2e3259c78c.jpg?w=905&h=510" },
                { name: "Campari", image: "https://cdn.tasteatlas.com//Images/Ingredients/7fc5727aca0b401a8acccdd03bc762c7.jpg?w=905&h=510" },
                { name: "Amaretto", image: "https://cdn.tasteatlas.com//images/ingredients/54e38b95ab5a4840956aa799afbd4c4a.jpg?w=905&h=510" }
            ],
            desertsDish: [{ name: "Tiramisu", image: "https://images.immediate.co.uk/production/volatile/sites/30/2021/03/Best-ever-tiramisu-374e63d.jpg?webp=true&quality=90&resize=620%2C310" },
                { name: "Cannoli", image: "https://images.immediate.co.uk/production/volatile/sites/30/2021/03/cannoli-fb8f075.jpg?webp=true&quality=90&resize=620%2C310" },
                { name: "Vanilla panna cotta", image: "https://images.immediate.co.uk/production/volatile/sites/30/2021/03/panna-cotta-aa6e5e8.jpg?webp=true&quality=90&resize=620%2C310" }
            ],
            snacksDish: [{ name: "Panzerotti", image: "https://cdn.tasteatlas.com//Images/Dishes/ca0da7070c0a4ff7ad2bd7e251c21435.jpg?w=905&h=510" }, {
                    name: "Arrosticini",
                    image: "https://cdn.tasteatlas.com//Images/Dishes/d7832fdebd1a43288a38b466868d1d39.jpg?w=905&h=510"
                },
                { name: "Arancini", image: "https://cdn.tasteatlas.com//images/dishes/288fea3b46744e59a2d5c79c032bafb7.jpg?w=905&h=510" }
            ],
            healthyDish: [{ name: "Lighter sphagetti and meatball", image: "https://images.immediate.co.uk/production/volatile/sites/30/2020/08/lighter-spaghetti-meatballs-fb343c6.jpg?quality=90&webp=true&resize=375,341" }, {
                name: "Lighter chicken and cacciatore",
                image: "https://images.immediate.co.uk/production/volatile/sites/30/2020/08/lighter-chicken-cacciatore-c94e376.jpg?quality=90&webp=true&resize=375,341"
            }, { name: "Sphagetti with smoky tomato and sea sauce", image: "https://images.immediate.co.uk/production/volatile/sites/30/2020/08/spaghetti-smoky-tomato-seafood-sauce-030e4f5.jpg?quality=90&webp=true&resize=375,340" }],
            quickBytes: [{ name: "Easy party meatballs", image: "https://imagesvc.meredithcorp.io/v3/mm/image?url=https%3A%2F%2Fcdn-image.myrecipes.com%2Fsites%2Fdefault%2Ffiles%2Fstyles%2F4_3_horizontal_-_1200x900%2Fpublic%2Fperfectpartymeatballs_1.jpeg%3Fitok%3DFnYpa9Kq%261515708313&w=200&c=sc&poi=face&q=85" }, {
                name: "Classic Froccacia Bread",
                image: "https://imagesvc.meredithcorp.io/v3/mm/image?url=https%3A%2F%2Fcdn-image.myrecipes.com%2Fsites%2Fdefault%2Ffiles%2Fstyles%2F4_3_horizontal_-_1200x900%2Fpublic%2F1573666465%2FMyRecipes-Classic-Focaccia164.jpg%3Fitok%3Dnivll3xr&w=200&c=sc&poi=face&q=85"
            }, { name: "Easy party pizza sticks", image: "https://imagesvc.meredithcorp.io/v3/mm/image?url=https%3A%2F%2Fcdn-image.myrecipes.com%2Fsites%2Fdefault%2Ffiles%2Fstyles%2F4_3_horizontal_-_1200x900%2Fpublic%2Fpizza_sticks.jpeg%3Fitok%3DvZzScqEV%261515518715&w=200&c=sc&poi=face&q=85" }],
}
  },

  provide() {
    return {
     
 Row1: {
        title: 'Vegan',
        items: this.veganDish
      }, Row2: {
        title: 'Non Veg',
        items: this.nonVegDish
      }, Row3: {
        title: 'Drinks',
        items:this.drinksDish
      },
      Row4: {
        title: 'Deserts',
        items: this.desertsDish
      },
       Row5: {
        title: 'Snacks',
        items: this.snacksDish
      },
       Row6: {
        title: 'Healthy',
        items: this.healthyDish
      },
       Row7: {
        title: 'Quick Bytes',
        items: this.quickBytes
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