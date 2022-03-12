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
             veganDish: [{
                    name: "Honey Chilli Potato",
                    image: "https://i.ndtvimg.com/i/2018-05/honey-chili-potato_620x330_61525941818.jpg",
                },
                {
                    name: "Vegetable Dumplings",
                    image: "https://thewoksoflife.com/wp-content/uploads/2015/09/vegetable-dumplings-9.jpg",
                },
                {
                    name: "SOY SCALLION SHANGHAI NOODLES",
                    image: "https://thewoksoflife.com/wp-content/uploads/2014/02/DSC_0135.jpg",
                }
            ],
            nonVegDish: [{
                    name: "Orange Chicken",
                    image: "data:image/jpeg;base64,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",
                },
                {
                    name: "Chicken Chowmein",
                    image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR19gYwwNQT-5f4MrXTSKBlFpgUrFEgRXhdAw&usqp=CAU",
                },
                {
                    name: "Chicken Lolipop",
                    image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQl1rXpnOyjSXpx5K6_ttGFMgG-7-Tx-InzTQ&usqp=CAU",
                }
            ],
            drinksDish: [{
                    name: "Peral Milk Tea",
                    image: "https://www.orientalmart.co.uk/route/images/uploads/news/1560415581.jpg",
                },
                {
                    name: "Chinese black beer",
                    image: "data:image/jpeg;base64,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",
                },
                {
                    name: "Sour Prune Drink",
                    image: "http://www.smartshanghai.com/uploads/articles/2015/08/6311439274239.jpg",
                }
            ],
            snacksDish: [{
                    name: "Pineapple buns",
                    image: "https://www.honestfoodtalks.com/wp-content/uploads/2021/04/Chinese-Snacks-Pineapple-Bun.jpeg",
                },
                {
                    name: "Haw Flakes",
                    image: "https://www.honestfoodtalks.com/wp-content/uploads/2021/01/6.jpg",
                },
                {
                    name: "Turnip Cakes",
                    image: "https://www.honestfoodtalks.com/wp-content/uploads/2020/02/dim-sum-fried-turnip-cake-1.jpg",
                }
            ],
            desertsDish: [{
                    name: "Chinese egg tarts",
                    image: "https://i.pinimg.com/564x/21/f2/82/21f282613b330d255ef5fc75f3508884.jpg",
                },
                {
                    name: "Soy milk pudding",
                    image: "https://i.pinimg.com/564x/f5/5f/e5/f55fe58a9dff8a5f011266603479a5e4.jpg",
                },
                {
                    name: "Red bean cake",
                    image: "https://i.pinimg.com/564x/7f/5b/bb/7f5bbbf31e4d5ece1f4e6943ecf502bf.jpg",
                }
            ],
            healthyDish: [{
                    name: "Chinese poached chicken and rice",
                    image: "https://images.immediate.co.uk/production/volatile/sites/30/2020/08/chicken-broth-19e3f68.jpg?quality=90&webp=true&resize=375,341",
                },
                {
                    name: "Chinese steamed bass with chicken",
                    image: "https://images.immediate.co.uk/production/volatile/sites/30/2020/08/recipe-image-legacy-id-805460_11-4405a0f.jpg?quality=90&webp=true&resize=375,341",
                },
                {
                    name: "Speedy soy spinach",
                    image: "https://images.immediate.co.uk/production/volatile/sites/30/2020/08/recipe-image-legacy-id-1259464_8-b36631e.jpg?quality=90&webp=true&resize=375,341",
                }
            ],

            quickBytes: [{
                    name: "Oyster sauce chicken",
                    image: "https://www.thespruceeats.com/thmb/buYTFMk4veoDEpfaQk3UaBXfEhs=/1487x0/filters:no_upscale():max_bytes(150000):strip_icc():format(webp)/bowls-of-chinese-spicy-chicken-dish-and-rice-597061039-5a5a810422fa3a00362d8ce4.jpg",
                },
                {
                    name: "Kung pao chicken",
                    image: "https://www.thespruceeats.com/thmb/l8IX8tGYwK6VAt6J81bfXrLjapE=/2121x0/filters:no_upscale():max_bytes(150000):strip_icc():format(webp)/GettyImages-1127677771-cc80c1c3141a4d69ad15e638a897424e.jpg",
                },
                {
                    name: "Oyster sauce chicken",
                    image: "https://www.thespruceeats.com/thmb/buYTFMk4veoDEpfaQk3UaBXfEhs=/1487x0/filters:no_upscale():max_bytes(150000):strip_icc():format(webp)/bowls-of-chinese-spicy-chicken-dish-and-rice-597061039-5a5a810422fa3a00362d8ce4.jpg",
                }
            ],
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