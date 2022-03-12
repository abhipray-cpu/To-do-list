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
    return{
       veganDish: [{ name: "Ratatoullie", image: "https://www.thespruceeats.com/thmb/HgkLdvxQHWqDO_nzMnrDCjpNKmo=/1500x0/filters:no_upscale():max_bytes(150000):strip_icc():format(webp)/ratatouille-recipe-1375502-11-5b3fd43246e0fb003716c8c3.jpg" },
                { name: "Roquefort and Carmelized Onion Tart", image: "https://www.thespruceeats.com/thmb/s_WMvwPBb5MNQABZojI_Ktv9T24=/2123x0/filters:no_upscale():max_bytes(150000):strip_icc():format(webp)/GettyImages-157610395-581617635f9b581c0bf17e79.jpg" },
                { name: "Truffled French Fries", image: "https://www.thespruceeats.com/thmb/_rhUxh1Zri-q4vWVi4trhsm8yzM=/2048x0/filters:no_upscale():max_bytes(150000):strip_icc():format(webp)/easy-homemade-truffle-fries-recipe-1375725-6420_preview-5b1989fa8e1b6e003698aa87.jpeg" }
            ],
            nonVegDish: [{ name: "Soupe à l’oignon", image: "https://www.expatica.com/app/uploads/sites/5/2014/05/french-onion-soup.jpg" }, { name: "Coq au vin", image: "https://www.expatica.com/app/uploads/sites/5/2020/03/Coq-au-vin.jpg" }, { name: "Boeuf bourguignon", image: "https://www.expatica.com/app/uploads/sites/5/2020/03/Boeuf-bourguignon.jpg" }],
            drinksDish: [{ name: "Absinthe", image: "https://www.listenandlearn.org/blog/wp-content/uploads/2014/07/FrenchDrinks-Tyler.jpeg" },
                { name: "Grand Marnier", image: "https://www.listenandlearn.org/blog/wp-content/uploads/2014/07/FrenchDrinks-Tyler.jpeg" },
                { name: "French wine", image: "data:image/jpeg;base64,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" }
            ],
            desertsDish: [{ name: "Crème brûlée", image: "https://i.insider.com/58a4d0a6c32d6b28008b4678?width=800&format=jpeg&auto=webp" },
                { name: "Profiterolls", image: "https://i.insider.com/58a46519c32d6b28008b45b1?width=800&format=jpeg&auto=webp" },
                { name: "Macarons", image: "https://i.insider.com/5880d4d8ba58c323008b5410?width=800&format=jpeg&auto=webp" }
            ],
            snacksDish: [{ name: "Jambon Beurre", image: "https://www.thespruceeats.com/thmb/cwh5jV3Dj3E7NAfCKlMux5VjgfE=/2121x0/filters:no_upscale():max_bytes(150000):strip_icc():format(webp)/GettyImages-647334273-57c6b1ee3df78cc16ebabc2f.jpg" },
                { name: "Parmesan Truffle Fries", image: "https://www.thespruceeats.com/thmb/_rhUxh1Zri-q4vWVi4trhsm8yzM=/2048x0/filters:no_upscale():max_bytes(150000):strip_icc():format(webp)/easy-homemade-truffle-fries-recipe-1375725-6420_preview-5b1989fa8e1b6e003698aa87.jpeg" },
                { name: "French Crepes", image: "https://www.thespruceeats.com/thmb/uN03HxJMj4dpqaby9n7yfQ75DsM=/1970x0/filters:no_upscale():max_bytes(150000):strip_icc():format(webp)/crepes-GettyImages-74333267-1--57c6b9a43df78cc16ebb38da.jpg" }
            ],
            healthyDish: [{ name: "Scallops", image: "https://i0.wp.com/www.healthfitnessrevolution.com/wp-content/uploads/2016/09/iStock-1043694260.jpg?resize=300%2C200&ssl=1" },
                { name: "Camembert", image: "https://i0.wp.com/www.healthfitnessrevolution.com/wp-content/uploads/2019/08/iStock-929619742.jpg?resize=630%2C420&ssl=1" },
                { name: "Slow Cooker Coq au Vin", image: "https://imagesvc.meredithcorp.io/v3/mm/image?url=https%3A%2F%2Fstatic.onecms.io%2Fwp-content%2Fuploads%2Fsites%2F37%2F2016%2F02%2F15222632%2FR1518131.jpg&w=200&c=sc&poi=face&q=85" }
            ],
            quickBytes: [{ name: "Layonnaise Potatos", image: "https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/delish-200212-lyonnaise-potatoes-0350-portrait-pf-1582835936.jpg?crop=1xw:1xh;center,top&resize=980:*" },
                { name: "Chicken Fricassee", image: "https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/chicken-fricassee-vertical-1536771734.png?crop=1xw:1xh;center,top&resize=980:*" },
                { name: "Cheesy Croissant Casserole", image: "https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/180829-bookazine-delish-04591-1538491939.jpg?crop=1xw:1xh;center,top&resize=980:*" }
            ]
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