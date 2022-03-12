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
import TheSearch from './components/TheSearch.vue';
import TheWallpaper from './components/TheWallpaper.vue';
import TheMenu from './components/TheMenu.vue';
import TheGrid from './components/TheGrid.vue';

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
  computed:{
    veganItems(){
      return this.$store.getters['getVegan'];
    },
    nonVegItems(){
    return this.$store.getters['getNonVeg']
    }, 
    drinkItems(){
      return this.$store.getters['getDrinks']
    },
    desertItems(){
      return this.$store.getters['getDesert']
    },
    snackItems(){
      return this.$store.getters['getSnacks']
    },
    healthyItems(){
      return this.$store.getters['getHealthy']
    },
    quickItems(){
      return this.$store.getters['getQuiks']
    }


  },

  provide() {
    return {
     
 Row1: {
        title: 'Vegan',
        items: this.veganItems
      }, Row2: {
        title: 'Non Veg',
        items: this.nonVegItems
      }, Row3: {
        title: 'Drinks',
        items:this.drinkItems
      },
      Row4: {
        title: 'Deserts',
        items: this.desertItems
      },
       Row5: {
        title: 'Snacks',
        items: this.snackItems
      },
       Row6: {
        title: 'Healthy',
        items: this.healthyItems
      },
       Row7: {
        title: 'Quick Bytes',
        items: this.quickItems
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